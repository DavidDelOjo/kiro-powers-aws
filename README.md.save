# Kiro Powers - AWS Collection

A collection of Kiro Powers for AWS services, providing specialized tools and workflows for security assessment and cost analysis.

## Available Powers

### 🔐 AWS Well-Architected Security

Security assessment tool based on AWS Well-Architected Framework to monitor security services, analyze security posture, and verify compliance in AWS environments.

**Features:**
- Monitor security services (GuardDuty, Security Hub, Inspector, IAM Access Analyzer)
- Analyze security findings
- Assess compliance
- Inventory AWS resources
- Complete security posture analysis
- Encryption verification

**MCP Server:** `awslabs.well-architected-security-mcp-server`

**Location:** `aws-well-architected/`

---

### 💰 AWS Pricing Calculator

MCP server for accessing real-time AWS pricing information and providing cost analysis capabilities with the AWS calculator.

**Features:**
- Real-time pricing queries
- Multi-region comparisons
- Monthly cost estimation
- Infrastructure project analysis (CDK, Terraform)
- Cost optimization recommendations
- Detailed report generation

**MCP Server:** `awslabs.aws-pricing-mcp-server`

**Location:** `aws-pricing/`

---

## Installation

### Prerequisites

- **Kiro IDE** version 0.7 or higher
- **Python 3.10+**
- **uv** package manager
- **AWS CLI** configured with credentials

### Installing uv

```bash
# macOS/Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Or using pip
pip install uv
```

### AWS CLI Configuration

```bash
# Configure AWS CLI
aws configure

# Or configure a specific profile
aws configure --profile my-profile
```

## Quick Start

### Method 1: Install from GitHub (Recommended)

1. Open Kiro IDE
2. Open the Powers panel
3. Click "Add Custom Power"
4. Select "GitHub Repository"
5. Enter: `https://github.com/DavidDelOjo/kiro-powers-aws`
6. Select the power you want to install:
   - `aws-well-architected`
   - `aws-pricing`
7. Click "Add"

### Method 2: Install from Local Directory

1. Clone this repository:
   ```bash
   git clone https://github.com/DavidDelOjo/kiro-powers-aws.git
   ```

2. Open Kiro IDE
3. Open the Powers panel
4. Click "Add Custom Power"
5. Select "Local Directory"
6. Enter the full path to the power directory:
   ```
   /path/to/kiro-powers-aws/aws-well-architected
   ```
   or
   ```
   /path/to/kiro-powers-aws/aws-pricing
   ```
7. Click "Add"

## Configuration

### AWS Well-Architected Security

Edit `aws-well-architected/mcp.json` to configure:

```json
{
  "mcpServers": {
    "well-architected-security-mcp-server": {
      "env": {
        "AWS_PROFILE": "your-profile-name",
        "AWS_REGION": "your-region"
      }
    }
  }
}
```

**Required IAM Permissions:**
- `SecurityAudit` (AWS managed policy)
- Or custom policy with read-only permissions for security services

### AWS Pricing

Edit `aws-pricing/mcp.json` to configure:

```json
{
  "mcpServers": {
    "awslabs.aws-pricing-mcp-server": {
      "env": {
        "AWS_PROFILE": "your-profile-name",
        "AWS_REGION": "your-region"
      }
    }
  }
}
```

**Required IAM Permissions:**
- `pricing:GetProducts`
- `pricing:DescribeServices`
- `pricing:GetAttributeValues`

## Usage Examples

### AWS Well-Architected Security

```
"Monitor the operational status of AWS security services in my account"

"Show me critical security findings that require attention"

"Analyze security posture against Well-Architected best practices"

"Verify compliance of my S3 buckets with security standards"

"Provide an inventory of all resources in my AWS account"
```

### AWS Pricing

```
"How much does an EC2 t3.medium instance cost in us-east-1?"

"Compare prices of t3.large instances between us-east-1 and eu-west-1"

"Calculate the monthly cost of 3 t3.medium instances running 24/7"

"How much would it cost to store 5TB in S3 Standard for a month?"

"Give me cost optimization recommendations for my EC2 infrastructure"
```

## Troubleshooting

### MCP Server Won't Connect

1. Verify `uv` is installed: `uv --version`
2. Check AWS credentials: `aws sts get-caller-identity`
3. Restart Kiro IDE
4. Reconnect the MCP server:
   - Cmd+Shift+P (macOS) or Ctrl+Shift+P (Windows/Linux)
   - Type "MCP: Reconnect Server"
   - Select the server

### Access Denied Errors

1. Verify IAM permissions for your user/role
2. Attach required policies (see Configuration section)
3. Wait a few minutes for permissions to propagate

### Empty Results

1. Verify the service is enabled in your AWS account
2. Check the region configuration
3. Ensure you have resources in the specified region

## Documentation

- [AWS Well-Architected Security - Full Documentation](aws-well-architected/POWER.md)
- [AWS Pricing Calculator - Full Documentation](aws-pricing/POWER.md)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Author

**David Del Ojo**

## Resources

- [Kiro Powers Documentation](https://kiro.dev/docs/powers)
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- [AWS Pricing](https://aws.amazon.com/pricing/)
- [AWS MCP Servers](https://github.com/awslabs/mcp)
- [Model Context Protocol](https://modelcontextprotocol.io/)

## Acknowledgments

- AWS Labs for the official MCP servers
- Kiro team for the Powers platform
- MCP community for the open protocol
