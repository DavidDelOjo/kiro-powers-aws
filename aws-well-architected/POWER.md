---
name: "aws-well-architected"
displayName: "AWS Well-Architected Security"
description: "Security assessment tool based on AWS Well-Architected Framework to monitor security services, analyze security posture, and verify compliance in AWS environments."
keywords: ["aws", "well-architected", "security", "compliance", "guardduty", "security-hub"]
author: "David Del Ojo"
---

# AWS Well-Architected Security

## Overview

This power provides operational tools for monitoring and assessing AWS environments against the AWS Well-Architected Framework Security Pillar. It enables operations teams to evaluate security posture, monitor compliance status, and optimize security costs while maintaining operational excellence.

The official AWS Labs MCP server integrates multiple AWS security services (GuardDuty, Security Hub, Inspector, IAM Access Analyzer) to provide comprehensive operational security visibility of your infrastructure.

## Use Cases

This power is designed for operational use in the following environments:

- **Production Operations**: Monitor security posture and compliance status in production environments
- **Compliance Operations**: Perform continuous compliance monitoring and reporting for regulatory requirements
- **Security Operations Center (SOC)**: Integrate with SOC workflows for continuous security monitoring
- **Cost Optimization**: Monitor security service costs and optimize spending
- **Operational Reporting**: Generate security operations reports for stakeholders and management

## Prerequisites

### System Requirements
- Python 3.10 or higher
- `uv` installed (Python package manager)

### AWS Credentials
- AWS CLI configured with appropriate credentials
- Read-only permissions for AWS security services
- AWS profile configured (optional but recommended)

### Installing uv

If you don't have `uv` installed:

```bash
# macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Or using pip
pip install uv
```

### AWS CLI Configuration

```bash
# Configure AWS CLI with your credentials
aws configure

# Or configure a specific profile
aws configure --profile my-security-profile
```

## Configuration

### Environment Variables

The MCP server uses the following optional environment variables:

- **`AWS_PROFILE`**: AWS CLI profile to use (optional, uses default if not specified)
- **`AWS_REGION`**: AWS region (optional, uses default if not specified)
- **`FASTMCP_LOG_LEVEL`**: Logging level (`ERROR`, `INFO`, `DEBUG`)

### IAM Best Practices

We strongly recommend creating dedicated IAM roles with least-privilege permissions:

1. Create a specific IAM role for security assessment operations
2. Apply least-privilege permissions by attaching only necessary read-only policies
3. Use scoped-down resource policies when possible
4. Apply a permission boundary to limit maximum permissions

**Recommended read-only policies:**
- `SecurityAudit` (AWS managed policy)
- `ViewOnlyAccess` (AWS managed policy)
- Custom policies with specific permissions for GuardDuty, Security Hub, Inspector, IAM Access Analyzer

## Available Tools

The MCP server provides the following operational tools:

### CheckSecurityServices
Monitors operational status of AWS security services.

**Functionality:**
- Monitors operational status of GuardDuty, Security Hub, Inspector, and IAM Access Analyzer
- Identifies service availability across regions
- Provides operational recommendations for maintaining service coverage

### GetSecurityFindings
Retrieves operational security findings.

**Functionality:**
- Collects findings from Security Hub, GuardDuty, and Inspector
- Filters findings by severity, resource type, or service
- Provides operational context and remediation guidance

### GetResourceComplianceStatus
Operational compliance monitoring.

**Functionality:**
- Monitors resources against security standards
- Identifies non-compliant resources for remediation workflows
- Provides compliance metrics and recommendations

### GetStoredSecurityContext
Historical security operations data.

**Functionality:**
- Retrieves historical data for trend analysis
- Enables comparison of security posture over time
- Provides context for findings and cost optimization

### ExploreAwsResources
Operational resource inventory.

**Functionality:**
- Discovers resources across AWS services
- Maps resource relationships for security context
- Identifies resources requiring security attention

### AnalyzeSecurityPosture
Comprehensive security operations analysis.

**Functionality:**
- Evaluates security posture against Well-Architected Framework
- Provides recommendations for improvements and cost optimization
- Generates security metrics and prioritized action items

## Common Workflows

### Workflow 1: Security Services Monitoring

**Goal:** Verify that all critical security services are operational.

**Example prompts:**
```
"Monitor the operational status of AWS security services in my account"
```

**What to expect:**
- List of security services and their status by region
- Recommendations on services that should be enabled
- Identification of gaps in security coverage

### Workflow 2: Security Findings Analysis

**Goal:** Review and prioritize current security findings.

**Example prompts:**
```
"Show me critical security findings that require operational attention"
```

**What to expect:**
- List of findings ordered by severity
- Details about affected resources
- Remediation recommendations
- Context about potential impact

### Workflow 3: Compliance Assessment

**Goal:** Verify compliance status of resources against security standards.

**Example prompts:**
```
"Verify compliance of my S3 buckets with operational security standards"
```

**What to expect:**
- Compliance status per resource
- Specific standards that are not met
- Overall compliance metrics
- Improvement recommendations

### Workflow 4: Resource Inventory

**Goal:** Get a complete inventory of AWS resources for security review.

**Example prompts:**
```
"Provide an operational inventory of all resources in my AWS account"
```

**What to expect:**
- Complete list of resources by service
- Resource distribution by region
- Identification of resources with security issues
- Mapping of relationships between resources

### Workflow 5: Complete Security Posture Analysis

**Goal:** Perform a complete assessment against the Well-Architected Framework.

**Example prompts:**
```
"Analyze operational security posture against Well-Architected best practices"
```

**What to expect:**
- Complete assessment against Well-Architected pillars
- Prioritized recommendations by impact
- Security metrics and trends
- Action plan with prioritized items

### Workflow 6: Encryption Verification

**Goal:** Verify that resources have encryption enabled according to policies.

**Example prompts:**
```
"Monitor encryption compliance across my S3 buckets for operational reporting"
```

**What to expect:**
- Encryption status per resource
- Identification of resources without encryption
- Encryption configuration recommendations
- Cost impact of enabling encryption

## Troubleshooting

### Error: "Unable to locate credentials"

**Cause:** AWS CLI is not configured or credentials are not valid.

**Solution:**
```bash
# Verify AWS CLI configuration
aws configure list

# Reconfigure credentials
aws configure

# Or specify profile in mcp.json
"AWS_PROFILE": "your-aws-profile"
```

### Error: "Access Denied" when executing tools

**Cause:** IAM role or user doesn't have necessary permissions.

**Solution:**
1. Verify your user/role has necessary policies
2. Attach the `SecurityAudit` policy for read-only permissions
3. Review logs to identify the specific missing permission
4. Add the minimum necessary permission to your IAM policy

```bash
# Verify current permissions
aws iam get-user-policy --user-name your-user --policy-name your-policy

# List attached policies
aws iam list-attached-user-policies --user-name your-user
```

### Error: "Region not specified"

**Cause:** No AWS region has been specified.

**Solution:**
```bash
# Configure default region
aws configure set region us-east-1

# Or specify in mcp.json
"AWS_REGION": "us-east-1"
```

### Problem: MCP server won't connect

**Cause:** Issues with `uv` installation or the server package.

**Solution:**
```bash
# Verify uv installation
uv --version

# Reinstall the package
uv pip install --upgrade awslabs.well-architected-security-mcp-server

# Verify package is installed
uv pip list | grep well-architected
```

### Problem: Empty or incomplete results

**Cause:** Security services may not be enabled in all regions.

**Solution:**
1. Use `CheckSecurityServices` to verify which services are enabled
2. Enable necessary services in required regions
3. Wait a few minutes for services to collect data
4. Re-run queries

### Problem: Slow performance

**Cause:** Queries across multiple regions or many resources.

**Solution:**
1. Limit queries to specific regions
2. Use filters to reduce query scope
3. Implement rate limiting to avoid API limits
4. Consider running queries during off-peak hours

## Best Practices

### Operational

- **Rate Limiting**: Implement appropriate rate limiting to avoid impacting AWS API limits
- **Monitoring Integration**: Integrate with existing monitoring and alerting systems
- **Access Controls**: Implement appropriate IAM controls and operational access patterns
- **Cost Monitoring**: Monitor API costs and optimize query patterns

### Security

- **Least Privilege**: Always use IAM roles with minimum necessary permissions
- **Credential Rotation**: Rotate AWS credentials regularly
- **Auditing**: Enable CloudTrail to audit all API calls
- **Data Protection**: Never expose credentials or sensitive data in logs

### Compliance

- **Regular Assessments**: Run security assessments regularly (daily, weekly)
- **Documentation**: Document all findings and remediation actions
- **Trends**: Use `GetStoredSecurityContext` to track improvements over time
- **Reporting**: Generate regular reports for stakeholders and audits

### Cost Optimization

- **Efficient Queries**: Use filters to reduce data volume queried
- **Caching**: Implement caching for data that doesn't change frequently
- **Specific Regions**: Limit queries to regions where you have resources
- **Scheduling**: Schedule complete assessments during lower-cost hours

## Operational Deployment Considerations

### Automated Remediation

While this tool provides operational visibility, automated remediation should be implemented through separate operational workflows. Consider:

- AWS Systems Manager for remediation automation
- AWS Lambda for automatic responses to findings
- AWS Config Rules for automatic configuration remediation

### Monitoring Integration

Designed for integration with existing monitoring systems:

- CloudWatch for metrics and alarms
- SNS for notifications
- EventBridge for event-based automation
- Custom dashboards for visualization

## Additional Resources

- **Official Documentation**: [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- **Security Pillar**: [Well-Architected Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)
- **GitHub Repository**: [AWS MCP Servers](https://github.com/awslabs/mcp)
- **Server Documentation**: [Well-Architected Security MCP Server](https://awslabs.github.io/mcp/servers/well-architected-security-mcp-server)

---

**Package**: `awslabs.well-architected-security-mcp-server`  
**MCP Server**: `well-architected-security-mcp-server`  
**License**: Apache License 2.0
