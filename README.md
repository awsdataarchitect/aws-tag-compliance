# AWS Resource Tag Compliance with Automation

## Free API from AWS to Track Resource Tag Compliance

### Introduction

Managing and monitoring AWS resources effectively is crucial for cost control, security, and operational efficiency. One key aspect of this management is ensuring that resources are consistently tagged according to organizational policies. Tags help in organizing resources, tracking costs, and applying governance. However, identifying resources that lack required tags can be a tedious task when done manually.

In this project, we provide a programmatic solution to automate the detection of AWS resources missing specific tags and generate actionable reports. We use a Python script, `aws_tag_compliance_reporter.py`, that leverages AWS SDKs and CLI tools to create an efficient and scalable tagging compliance solution.

### Overview of the Solution

Our approach includes:
- **Fetching All AWS Resources**: Retrieve a comprehensive list of all resources in your AWS account.
- **Identifying Missing Tags**: Check each resource for the presence of specific tags.
- **Generating Reports**: Create a detailed report of resources that do not meet the tagging requirements.
- **Storing Reports**: Upload the generated report to an S3 bucket for easy access and sharing.

### Prerequisites

- **AWS Account**: An active AWS account with appropriate permissions.
- **AWS CLI and Boto3**: Installed and configured.
- **Python**: Ensure Python is installed on your system.

### Step-by-Step Guide

1. **Setup AWS CLI and Boto3**
   - First, make sure you have AWS CLI and Boto3 installed and configured with the necessary permissions:
     ```bash
     pip install boto3
     ```
   - **Tip**: If you use AWS CloudShell, it comes with AWS CLI, pip, and Boto3 pre-installed.
     ```bash
     pip3 list | grep boto3
     ```

2. **The Python Script**
   - Clone the GitHub repository to get the script:
     ```bash
     git clone https://github.com/awsdataarchitect/aws-tag-compliance.git
     cd aws-tag-compliance
     ```
   - Run the script, which performs the following tasks:
     - Lists all AWS resources.
     - Checks for specific tags.
     - Generates a report of resources without the required tags.
     - Uploads the report to an S3 bucket.
     ```bash
     python3 aws_tag_compliance_reporter.py
     ```

3. **Deployment and Scheduling**
   - **Deploy the Script**: Deploy the script on an EC2 instance, Lambda function, or container with the necessary permissions.
   - **Schedule Execution**: Use AWS Lambda with CloudWatch Events or an EC2 cron job for periodic execution.

4. **IAM Permissions**
   - Ensure the IAM role or user running the script has the following permissions:
     - `resourcegroupstaggingapi:GetResources`
     - `s3:PutObject` (for uploading the report to S3)

### Benefits of This Approach

- **Automation**: Streamlines the process of identifying resources without required tags.
- **Scalability**: Handles large numbers of resources efficiently using paginated API calls.
- **Actionable Reporting**: Provides a clear report of non-compliant resources for easy remediation.
- **Integration**: Easily integrates with other AWS services for further processing or notifications.

### Pricing

AWS Resource Explorer and `resourcegroupstaggingapi` are offered at no additional charge. There are no setup fees or upfront commitments.

### Conclusion

By implementing the `aws_tag_compliance_reporter.py` script, you can automate the detection of AWS resources missing specific tags, ensuring compliance with organizational policies. This solution offers a scalable and efficient way to manage tagging across your AWS environment, helping maintain control and consistency in your resource management practices.
