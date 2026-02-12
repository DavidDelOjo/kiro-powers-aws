# Usage Examples

This document provides detailed examples of using the AWS Powers in Kiro.

## Table of Contents

- [AWS Well-Architected Security Examples](#aws-well-architected-security-examples)
- [AWS Pricing Calculator Examples](#aws-pricing-calculator-examples)
- [Combined Workflows](#combined-workflows)

---

## AWS Well-Architected Security Examples

### Example 1: Daily Security Check

**Scenario**: You want to perform a daily security check of your AWS environment.

**Prompt**:
```
Monitor the operational status of all AWS security services in my account and show me any critical findings
```

**Expected Output**:
- Status of GuardDuty, Security Hub, Inspector, and IAM Access Analyzer
- List of critical and high-severity findings
- Affected resources
- Remediation recommendations

**Use Case**: Daily standup, security operations center (SOC) monitoring

---

### Example 2: Compliance Audit

**Scenario**: You need to verify S3 bucket compliance for an audit.

**Prompt**:
```
Verify compliance of all my S3 buckets with security standards and identify any buckets without encryption
```

**Expected Output**:
- Compliance status per bucket
- Encryption configuration
- Public access settings
- Versioning status
- Recommendations for non-compliant buckets

**Use Case**: Compliance audits, security reviews, regulatory requirements

---

### Example 3: Security Posture Assessment

**Scenario**: Monthly security assessment against AWS Well-Architected Framework.

**Prompt**:
```
Analyze my complete security posture against AWS Well-Architected best practices and provide a prioritized action plan
```

**Expected Output**:
- Assessment against Well-Architected pillars
- Security score and metrics
- Prioritized recommendations
- Risk analysis
- Implementation roadmap

**Use Case**: Monthly security reviews, architecture assessments, improvement planning

---

### Example 4: Resource Inventory

**Scenario**: You need a complete inventory of AWS resources for security review.

**Prompt**:
```
Provide a complete inventory of all resources in my AWS account organized by service and region
```

**Expected Output**:
- Complete resource list by service
- Distribution by region
- Resources with security issues
- Resource relationships and dependencies

**Use Case**: Asset management, security audits, cost analysis preparation

---

### Example 5: Incident Investigation

**Scenario**: GuardDuty detected suspicious activity.

**Prompt**:
```
Show me all critical GuardDuty findings from the last 24 hours with details about affected resources and recommended actions
```

**Expected Output**:
- Recent critical findings
- Affected EC2 instances, IAM users, or other resources
- Finding details and context
- Immediate remediation steps
- Related findings

**Use Case**: Incident response, security investigations, threat hunting

---

## AWS Pricing Calculator Examples

### Example 1: Single Instance Pricing

**Scenario**: You want to know the cost of a specific EC2 instance.

**Prompt**:
```
How much does a t3.medium EC2 instance cost per hour in us-east-1?
```

**Expected Output**:
- On-Demand price per hour
- Monthly cost (730 hours)
- Annual cost
- Reserved Instance pricing options
- Spot pricing (if available)

**Use Case**: Quick pricing lookups, instance selection, budget planning

---

### Example 2: Multi-Region Comparison

**Scenario**: You're deciding which region to deploy in.

**Prompt**:
```
Compare the price of m5.xlarge instances across us-east-1, us-west-2, eu-west-1, and ap-southeast-1
```

**Expected Output**:
- Price comparison table by region
- Percentage differences
- Most economical region
- Latency considerations
- Regional availability notes

**Use Case**: Region selection, cost optimization, multi-region planning

---

### Example 3: Monthly Cost Estimation

**Scenario**: You need to estimate monthly costs for a new project.

**Prompt**:
```
Calculate the monthly cost of running 5 t3.large instances 24/7 with 100GB EBS storage each in us-east-1
```

**Expected Output**:
- EC2 compute costs
- EBS storage costs
- Data transfer estimates
- Total monthly cost
- Annual projection
- Savings options (Reserved Instances, Savings Plans)

**Use Case**: Budget planning, project proposals, cost forecasting

---

### Example 4: Storage Cost Analysis

**Scenario**: You're evaluating S3 storage options.

**Prompt**:
```
Compare the monthly cost of storing 10TB in S3 Standard vs S3 Intelligent-Tiering vs S3 Glacier in us-east-1
```

**Expected Output**:
- Cost comparison by storage class
- Access cost considerations
- Retrieval time differences
- Recommendations based on access patterns
- Break-even analysis

**Use Case**: Storage planning, cost optimization, data lifecycle management

---

### Example 5: Infrastructure Project Analysis

**Scenario**: You have a Terraform project and want to estimate costs.

**Prompt**:
```
Analyze this Terraform configuration and estimate the monthly AWS costs:

[Paste your Terraform code]
```

**Expected Output**:
- Identified AWS services
- Cost per service
- Total monthly estimate
- Cost breakdown by resource type
- Optimization recommendations

**Use Case**: Infrastructure planning, budget approval, cost forecasting

---

### Example 6: Cost Optimization

**Scenario**: You want to reduce your EC2 costs.

**Prompt**:
```
I'm running 20 t3.large instances 24/7 in us-east-1. How can I optimize costs?
```

**Expected Output**:
- Current monthly cost
- Reserved Instance savings (1-year, 3-year)
- Savings Plans options
- Spot Instance potential
- Right-sizing recommendations
- Estimated savings per option

**Use Case**: Cost reduction initiatives, budget optimization, financial planning

---

### Example 7: Database Pricing

**Scenario**: You're choosing between RDS options.

**Prompt**:
```
Compare the monthly cost of RDS MySQL db.m5.large vs Aurora MySQL db.r5.large in us-east-1 with 500GB storage
```

**Expected Output**:
- Compute cost comparison
- Storage cost differences
- I/O cost considerations
- Backup costs
- Total monthly cost
- Performance differences
- Recommendations

**Use Case**: Database selection, migration planning, cost analysis

---

## Combined Workflows

### Workflow 1: Security + Cost Optimization

**Scenario**: You want to improve security while optimizing costs.

**Step 1 - Security Assessment**:
```
Analyze my security posture and identify resources that need security improvements
```

**Step 2 - Cost Analysis**:
```
For the resources identified, what would be the cost impact of implementing the recommended security improvements?
```

**Use Case**: Balanced security and cost optimization

---

### Workflow 2: Compliance + Budget Planning

**Scenario**: You need to ensure compliance and plan budget for remediation.

**Step 1 - Compliance Check**:
```
Verify compliance of all my resources with security standards and list non-compliant resources
```

**Step 2 - Remediation Cost**:
```
Estimate the cost of enabling encryption and additional security features for the non-compliant resources
```

**Use Case**: Compliance projects, security budget planning

---

### Workflow 3: New Project Planning

**Scenario**: Planning a new AWS project with security and cost considerations.

**Step 1 - Architecture Cost**:
```
Estimate the monthly cost of this architecture:
- 3 t3.large EC2 instances
- Application Load Balancer
- RDS MySQL db.m5.large
- 1TB S3 storage
- CloudFront distribution
```

**Step 2 - Security Requirements**:
```
What security services should I enable for this architecture and what would be the additional cost?
```

**Step 3 - Optimization**:
```
How can I optimize both security and costs for this setup?
```

**Use Case**: New project planning, architecture design, comprehensive planning

---

## Tips for Effective Usage

### Best Practices

1. **Be Specific**: Include instance types, regions, and exact configurations
2. **Use Filters**: Narrow down results by severity, service, or resource type
3. **Regular Monitoring**: Schedule regular security and cost reviews
4. **Combine Powers**: Use both powers together for comprehensive analysis
5. **Document Results**: Save important findings and cost estimates

### Common Patterns

**Daily Operations**:
```
"Show me critical security findings and any cost anomalies from the last 24 hours"
```

**Weekly Reviews**:
```
"Provide a weekly security summary and cost trend analysis"
```

**Monthly Planning**:
```
"Complete security assessment and cost optimization recommendations for next month"
```

**Quarterly Audits**:
```
"Full compliance audit and annual cost projection with optimization opportunities"
```

---

## Troubleshooting Examples

### Example: No Results Returned

**Problem**: Query returns no results

**Solution**:
```
"Check if GuardDuty is enabled in my account and which regions have it active"
```

### Example: Access Denied

**Problem**: Getting access denied errors

**Solution**:
```
"What IAM permissions do I need to run security assessments with this power?"
```

### Example: Unexpected Costs

**Problem**: Pricing seems incorrect

**Solution**:
```
"Break down the pricing for t3.medium in us-east-1 showing all cost components"
```

---

## Advanced Examples

### Multi-Account Security

```
"Compare security posture across my development, staging, and production accounts"
```

### Cost Forecasting

```
"Based on current usage, forecast my AWS costs for the next 6 months with 20% growth"
```

### Compliance Reporting

```
"Generate a compliance report for all S3 buckets, RDS databases, and EC2 instances against CIS AWS Foundations Benchmark"
```

### Cost Allocation

```
"Break down my monthly AWS costs by service, region, and environment tag"
```

---

**Note**: These examples assume you have:
- Kiro IDE 0.7+ installed
- AWS CLI configured with appropriate credentials
- Both powers installed and configured
- Necessary IAM permissions

For more information, see the individual POWER.md files in each power directory.
