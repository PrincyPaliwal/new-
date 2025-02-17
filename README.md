# Automated Data Lineage & Compliance Reporting

## Overview
The **Automated Data Lineage & Compliance Reporting** system enhances security and governance by tracking data lineage, scanning for sensitive data, and enforcing access controls dynamically. This solution integrates AWS Macie, AWS IAM, and Databricks Unity Catalog to provide an automated compliance framework.

## Features
- **AWS Macie Scanning**: Detects sensitive data in S3 buckets.
- **Databricks Unity Catalog**: Tracks data lineage automatically.
- **IAM Role Enforcement**: Restricts access to sensitive data dynamically.
- **AWS Step Functions**: Automates the entire process from scanning to enforcement.
- **Serverless Architecture**: Uses Lambda for event-driven execution.

## Folder Structure
### 1. **Macie & Security Enforcement**
- **Macie Classification Job**: Identifies sensitive data.
- **IAM Policy Automation**: Blocks unauthorized access based on Macie findings.

### 2. **Databricks Lineage Tracking**
- **Unity Catalog Setup**: Enables lineage tracking.
- **Schema & Table Definitions**: Manages metadata and data governance.

### 3. **Automation & Orchestration**
- **Step Functions Workflow**: Triggers Macie scans, stores results, and applies IAM restrictions.
- **Lambda Functions**: Executes automated security actions.

## Getting Started
### Prerequisites
To deploy this solution, ensure you have:
- **AWS Account** with access to Macie, IAM, and Step Functions.
- **Databricks Workspace** with Unity Catalog enabled.
- **AWS CLI & Terraform (Optional)** for deployment automation.

### Installation
Clone the repository to your local machine:
```bash
git clone https://github.com/your-repo/automated-data-lineage.git
cd automated-data-lineage
```

### Setup & Deployment
#### 1. **Deploy Macie Classification Job**
```bash
python scripts/macie_scan_setup.py
```

#### 2. **Set Up Databricks Unity Catalog**
Run the following in Databricks:
```sql
CREATE METASTORE my_metastore MANAGED LOCATION 's3://databricks-unity-bucket/';
CREATE CATALOG my_catalog;
CREATE SCHEMA my_schema;
CREATE TABLE customer_data (id INT, name STRING, email STRING) USING DELTA;
```

#### 3. **Deploy Step Functions Workflow**
```bash
aws stepfunctions create-state-machine --name DataComplianceWorkflow --definition file://step_function_definition.json --role-arn arn:aws:iam::YOUR_ACCOUNT_ID:role/StepFunctionsRole
```

#### 4. **Deploy Lambda Functions**
```bash
aws lambda create-function --function-name trigger-macie --runtime python3.9 --role arn:aws:iam::YOUR_ACCOUNT_ID:role/LambdaRole --handler macie_lambda.lambda_handler --zip-file fileb://macie_lambda.zip
aws lambda create-function --function-name apply-iam-restrictions --runtime python3.9 --role arn:aws:iam::YOUR_ACCOUNT_ID:role/LambdaRole --handler iam_lambda.lambda_handler --zip-file fileb://iam_lambda.zip
```

### Monitoring & Debugging
- **CloudWatch Logs**: Tracks Macie and Step Functions execution logs.
- **Databricks UI**: View lineage logs under Data Explorer → Lineage tab.
- **Step Functions Execution History**: Monitors event triggers and automation flows.

## Contributions
We welcome contributions! If you have ideas for improvements, submit a pull request.

## License
This project is licensed under the **MIT License**.

## Contact
For issues, support, or questions, please use the GitHub Issues section or contact the project maintainer via email.

