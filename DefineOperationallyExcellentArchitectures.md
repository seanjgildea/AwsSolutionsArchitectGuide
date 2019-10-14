# Domain 5: Define Operationally-Excellent Architectures

## 5.1 Choose design features in solutions that enable operational excellence.

Automated systems that adapt to circumstances and over time evolve to make it better
- Automation scripts
- Perform operations with code
- Frequent small reversible changes
- Anticipate failure
- Learn from all operational failures
- 

Services that support operational excellence
- AWS Config : Tracks resources such as ebs volumes and EC2 instances, it verifies that 
- AWS CloudFormation: JSON and YAML templates into infrastructure and resources
- AWS Trusted Advisor: Checks accounts for best practices on security, reliability, performance, cost and service limits
- AWS Inspector: Checks EC2 instances for security vulnerabilities
- VPC Flow Logs: Logs Network Traffic ( Captures layer 3 and 4 IP-level logs and do not capture layer 7 HTTP errors )
- AWS Cloud Trail: Logs API calls
- AWS CloudWatch: Tracks metrics and triggers alarms with metrics are exceeded. Logs stores logs from EC2 instances, Cloud Trail and Lambda and can also turn these log files into metrics by extracting patterns from log lines. 

Other notes:
- Cloudwatch Metrics do not capture 404 errors by default
- IAM roles are safer and easier than keys and passwords
- Monitor metrics across the system
- Automate responses to metrics where possible

