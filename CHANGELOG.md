# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-02-12

### Added

#### AWS Well-Architected Security Power
- Security assessment tool based on AWS Well-Architected Framework
- Monitor security services (GuardDuty, Security Hub, Inspector, IAM Access Analyzer)
- Analyze security findings and compliance status
- Complete security posture analysis
- Resource inventory and encryption verification
- Comprehensive POWER.md documentation
- MCP server configuration with `awslabs.well-architected-security-mcp-server`

#### AWS Pricing Calculator Power
- Real-time AWS pricing information access
- Multi-region price comparisons
- Monthly cost estimation and analysis
- Infrastructure project analysis (CDK, Terraform)
- Cost optimization recommendations
- Detailed report generation
- Comprehensive POWER.md documentation
- MCP server configuration with `awslabs.aws-pricing-mcp-server`

#### Documentation
- Complete README.md with installation and usage instructions
- Individual POWER.md files for each power with detailed workflows
- Troubleshooting guides and best practices
- IAM permissions documentation
- Configuration examples

#### Repository Structure
- Apache License 2.0
- Organized folder structure for each power
- MCP configuration files included
- Contributing guidelines

### Requirements
- Kiro IDE version 0.7 or higher
- Python 3.10+
- uv package manager
- AWS CLI configured with credentials

---

## Future Releases

### [Planned]
- Additional AWS Powers (CloudWatch, Lambda, etc.)
- Multi-language support for documentation
- Video tutorials and demos
- Integration examples with CI/CD pipelines
- Enhanced error handling and diagnostics
