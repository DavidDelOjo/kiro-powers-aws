---
name: "aws-pricing"
displayName: "AWS Pricing Calculator"
description: "MCP server for accessing real-time AWS pricing information and providing cost analysis capabilities with the AWS calculator."
keywords: ["aws", "pricing", "costs", "calculator", "budget", "cost-optimization"]
author: "David Del Ojo"
---

# AWS Pricing Calculator

## Overview

This power provides real-time access to AWS pricing information and cost analysis capabilities. It allows you to query AWS service prices, compare costs across regions, analyze infrastructure projects, and receive cost optimization recommendations.

The official AWS Labs MCP server integrates the AWS Pricing API to provide up-to-date data and detailed cost analysis at no additional charge.

## Key Features

### Pricing Discovery & Information

- **Service catalog exploration**: Discover all AWS services with available pricing information
- **Pricing attribute discovery**: Identify filterable dimensions (instance types, regions, storage classes, etc.)
- **Real-time pricing queries**: Access current pricing data with advanced filtering capabilities
- **Multi-region pricing comparisons**: Compare pricing across different AWS regions in a single query
- **Bulk pricing data access**: Download complete pricing datasets in CSV/JSON formats

### Cost Analysis & Planning

- **Detailed cost report generation**: Create comprehensive cost analysis reports with unit pricing and usage scenarios
- **Infrastructure project analysis**: Scan CDK and Terraform projects to automatically identify AWS services
- **Architecture pattern guidance**: Get detailed architecture patterns and cost considerations
- **Cost optimization recommendations**: Receive AWS Well-Architected Framework aligned suggestions

### Natural Language Queries

- Ask questions about AWS pricing in plain English
- Get instant answers from the AWS Pricing API for any AWS service
- Retrieve comprehensive pricing information with flexible filtering options

## Prerequisites

### AWS Credentials

- AWS account with appropriate permissions
- AWS credentials configured (via AWS CLI or environment variables)
- IAM permissions: `pricing:*` to access the Pricing API

**Important Note**: The server only accesses publicly available AWS pricing information. All Pricing API calls are free of charge and do not incur any costs.

### IAM Permissions Configuration

Your IAM role or user must have `pricing:*` permissions. Example policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "pricing:GetProducts",
        "pricing:DescribeServices",
        "pricing:GetAttributeValues"
      ],
      "Resource": "*"
    }
  ]
}
```

## Available Tools

The MCP server provides tools for querying and analyzing AWS prices:

### GetServiceCatalog
Gets the complete catalog of AWS services with available pricing information.

**Usage:**
```
"Show me all AWS services with available pricing information"
```

### GetPricingAttributes
Identifies filterable attributes for a specific service (instance types, regions, etc.).

**Usage:**
```
"What pricing attributes can I filter for EC2?"
```

### QueryPricing
Queries real-time prices with advanced filters.

**Usage:**
```
"What is the price of a t3.medium instance in us-east-1?"
"Compare prices of t3.large instances between us-east-1 and eu-west-1"
```

### ComparePricing
Compares prices between different options or regions.

**Usage:**
```
"Compare the cost of S3 Standard vs S3 Glacier storage"
"What is the price difference for RDS between regions?"
```

### GenerateCostReport
Generates detailed cost reports with calculations and usage scenarios.

**Usage:**
```
"Generate a cost report for a t3.large EC2 instance running 24/7"
"Calculate the monthly cost of 1TB in S3 Standard"
```

### AnalyzeInfrastructure
Analyzes CDK or Terraform projects to identify services and estimate costs.

**Usage:**
```
"Analyze my Terraform project and estimate monthly costs"
```

### GetArchitecturePatterns
Gets architecture patterns and cost considerations.

**Usage:**
```
"Give me cost-effective architecture patterns for a web application"
```

### OptimizeCosts
Provides cost optimization recommendations.

**Usage:**
```
"How can I optimize costs for my EC2 infrastructure?"
```

## Common Workflows

### Workflow 1: Basic Price Query

**Goal:** Get the price of a specific service.

**Example prompts:**
```
"How much does an EC2 t3.medium instance cost in us-east-1?"
"Give me the price of S3 Standard storage per GB in eu-west-1"
"What is the cost of an RDS MySQL db.t3.small database?"
```

**What to expect:**
- Price per hour or per unit
- Configuration details
- Region information
- Payment options (On-Demand, Reserved, Spot)

### Workflow 2: Cross-Region Price Comparison

**Goal:** Compare costs of the same service in different regions.

**Example prompts:**
```
"Compare the price of t3.large instances between us-east-1, us-west-2, and eu-west-1"
"In which region is it cheapest to run an m5.xlarge instance?"
"Show me the S3 cost difference between all US regions"
```

**What to expect:**
- Comparative price table by region
- Percentage differences
- Recommendation for most economical region
- Latency vs cost considerations

### Workflow 3: Monthly Cost Estimation

**Goal:** Calculate the monthly cost of a specific configuration.

**Example prompts:**
```
"Calculate the monthly cost of 3 t3.medium instances running 24/7 in us-east-1"
"How much would it cost to store 5TB in S3 Standard for a month?"
"Estimate the monthly cost of an RDS db.m5.large database with 500GB of storage"
```

**What to expect:**
- Total monthly cost
- Breakdown by component (compute, storage, transfer)
- Projected annual cost
- Savings options (Reserved Instances, Savings Plans)

### Workflow 4: Service Option Comparison

**Goal:** Compare different configurations or service types.

**Example prompts:**
```
"Compare the cost of S3 Standard vs S3 Intelligent-Tiering for 10TB"
"What is more economical: EC2 On-Demand or Reserved Instances for 1 year?"
"Compare t3 vs t4g instances for a web application"
```

**What to expect:**
- Detailed cost comparison
- Pros and cons of each option
- Recommendation based on use case
- Break-even point

### Workflow 5: Infrastructure Project Analysis

**Goal:** Estimate costs of a CDK or Terraform project.

**Example prompts:**
```
"Analyze this Terraform code and estimate monthly costs"
"Review my CDK stack and give me a cost breakdown"
"How much would it cost to deploy this infrastructure in production?"
```

**What to expect:**
- List of identified services
- Cost estimation per service
- Total projected monthly cost
- Optimization recommendations

### Workflow 6: Cost Optimization

**Goal:** Get recommendations to reduce costs.

**Example prompts:**
```
"How can I reduce costs for my EC2 infrastructure?"
"Give me optimization recommendations for my S3 storage"
"What options do I have to save on RDS costs?"
```

**What to expect:**
- Specific optimization recommendations
- Potential savings estimation
- Implementation steps
- Trade-offs to consider

## Troubleshooting

### Error: "Access Denied" when querying prices

**Cause:** IAM role or user doesn't have `pricing:*` permissions.

**Solution:**
1. Verify IAM permissions for your user/role
2. Attach a policy with `pricing:GetProducts`, `pricing:DescribeServices`, `pricing:GetAttributeValues` permissions
3. Wait a few minutes for permissions to propagate

### Error: "Service not found"

**Cause:** Service name is incorrect or doesn't have available pricing information.

**Solution:**
1. Use `GetServiceCatalog` to see available services
2. Verify the exact service name
3. Some services may not have public pricing

### Empty or incomplete pricing results

**Cause:** Filters may be too specific or incorrect.

**Solution:**
1. Use `GetPricingAttributes` to see filterable attributes
2. Simplify filters
3. Verify the specified region is correct

### Problem: Outdated prices

**Cause:** Prices are obtained in real-time, but there may be caching.

**Solution:**
1. Prices are real-time from the AWS API
2. If you suspect old data, reconnect the MCP server
3. Verify the date/time in the response

### Error: "Region not supported"

**Cause:** The specified region doesn't exist or isn't available.

**Solution:**
1. Verify the region code (e.g., `us-east-1`, not `us-east-1a`)
2. Use standard AWS regions
3. Query the list of available regions

**Common regions:**
- `us-east-1` (N. Virginia)
- `us-west-2` (Oregon)
- `eu-west-1` (Ireland)
- `ap-southeast-1` (Singapore)

## Best Practices

### Price Queries

- **Be specific**: Include instance type, region, and exact configuration
- **Use comparisons**: Compare options before making decisions
- **Consider usage**: Prices vary by usage pattern (24/7 vs intermittent)
- **Review payment options**: On-Demand, Reserved, Spot have different prices

### Cost Analysis

- **Include all components**: Compute, storage, data transfer, backups
- **Project long-term**: Calculate monthly and annual costs
- **Consider growth**: Estimate costs with usage growth
- **Review regularly**: AWS prices change periodically

### Optimization

- **Use Reserved Instances**: For predictable 1-3 year workloads
- **Consider Spot Instances**: For interruption-tolerant workloads
- **Implement auto-scaling**: Pay only for what you use
- **Review storage classes**: S3 has multiple cost options
- **Monitor actual usage**: Use AWS Cost Explorer for real data

### Budget Planning

- **Set up alerts**: Configure AWS Budgets to monitor spending
- **Document estimates**: Save cost calculations for reference
- **Review monthly**: Compare estimated vs actual costs
- **Plan contingencies**: Include margin for unexpected growth

## Common Use Cases

### 1. AWS Migration Planning

**Scenario:** You're migrating on-premise infrastructure to AWS.

**Useful prompts:**
```
"How much would it cost to migrate 10 servers with 8GB RAM to EC2 instances?"
"Compare on-premise storage cost vs S3 for 50TB"
"Estimate the monthly cost of a typical web architecture on AWS"
```

### 2. Existing Cost Optimization

**Scenario:** You want to reduce your current AWS bill.

**Useful prompts:**
```
"How can I reduce costs for EC2 instances running 24/7?"
"Give me options to optimize S3 storage costs"
"How much would I save with Reserved Instances vs On-Demand?"
```

### 3. Architecture Comparison

**Scenario:** You're deciding between different architecture designs.

**Useful prompts:**
```
"Compare the cost of serverless architecture vs traditional EC2"
"What is more economical: RDS or self-managed database on EC2?"
"Compare costs of ECS vs EKS for containers"
```

### 4. Project Budgeting

**Scenario:** You need to estimate costs for a new project.

**Useful prompts:**
```
"Estimate the monthly cost of a web application with 100k users"
"How much would a machine learning architecture cost on AWS?"
"Give me a cost breakdown for a data lake on S3"
```

### 5. Multi-Region Analysis

**Scenario:** You're expanding to multiple regions.

**Useful prompts:**
```
"Compare costs of deploying in us-east-1 vs eu-west-1"
"Which is the most economical region for my use case?"
"Estimate the cost of multi-region replication for high availability"
```

## Limitations and Considerations

### Pricing Accuracy

- Prices are real-time from the official AWS API
- AI assistants are not guaranteed to construct filters perfectly
- Always verify critical prices in the official AWS calculator
- Prices may change without prior notice

### Service Scope

- Only provides public pricing information
- Does not access your account-specific data
- Cannot see your current billing
- Does not execute changes to your infrastructure

### Additional Costs

- Data transfer between regions has additional costs
- Some services have hidden costs (NAT Gateway, etc.)
- Backups and snapshots can increase costs
- Consider AWS support costs if applicable

## Additional Resources

- **Official AWS Calculator**: [AWS Pricing Calculator](https://calculator.aws.amazon.com/)
- **Pricing Documentation**: [AWS Pricing](https://aws.amazon.com/pricing/)
- **Cost Explorer**: [AWS Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/)
- **Well-Architected Cost Optimization**: [Cost Optimization Pillar](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html)
- **GitHub Repository**: [AWS MCP Servers](https://github.com/awslabs/mcp)

---

**Package**: `awslabs.aws-pricing-mcp-server`  
**MCP Server**: `awslabs.aws-pricing-mcp-server`  
**License**: Apache License 2.0  
**API**: All calls are free of charge
