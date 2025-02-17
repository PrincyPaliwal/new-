# Automated Data Ingestion Pipeline

## Overview

The **Automated Data Ingestion Pipeline** streamlines the process of ingesting, transforming, and loading data from AWS services into Databricks Delta Lake. This solution enables schema evolution, real-time data streaming, and automated transformation using AWS-native tools.

## Features

- **End-to-End Data Pipeline**: Automates data ingestion from AWS to Databricks Delta Lake.
- **AWS Glue Crawler**: Detects schema changes in S3 and updates metadata.
- **Amazon Kinesis**: Streams real-time data for continuous processing.
- **AWS EventBridge**: Triggers Databricks transformations based on Glue Crawler events.
- **Databricks Integration**: Executes transformation notebooks and monitors execution.
- **Delta Lake Schema Evolution**: Automatically adapts to changing data structures.
- **AWS CloudFormation**: Automates infrastructure provisioning (Kinesis, Glue, S3).
- **Scalability**: Designed to handle large-scale real-time and batch processing.
- **Serverless Execution**: Uses AWS Lambda for event-driven triggers.
- **Monitoring & Logging**: Tracks job execution and alerts on failures.

## Folder Structure

### 1. **Ingestion Scripts**

Contains Python scripts for setting up and managing AWS services:

- **Glue Crawler Setup**: Automates metadata detection and schema evolution.
- **Kinesis Stream Processing**: Captures and processes real-time data.
- **EventBridge Rules**: Manages event-based triggers for automation.

### 2. **Databricks Integration**

Includes:

- **Notebook Execution Scripts**: Triggers Databricks notebooks for data transformation.
- **Delta Lake Management**: Ensures seamless schema evolution and data governance.

### 3. **Infrastructure Automation**

Contains AWS CloudFormation templates for:

- **Kinesis Stream Setup**
- **S3 Bucket Configuration**
- **Glue Database & Crawler Setup**

## Getting Started

### Prerequisites

To deploy and use this pipeline, ensure you have:

- **AWS Account** with permissions for Glue, Kinesis, S3, and EventBridge.
- **Databricks Workspace** and API credentials.
- **AWS CLI & Terraform (Optional)** for automated deployment.

### Installation

Clone the repository to your local machine:

```bash
git clone https://github.com/your-repo/automated-data-ingestion.git
cd automated-data-ingestion
```

### Setup & Deployment

#### 1. **Deploy CloudFormation Stack**

```bash
aws cloudformation create-stack --stack-name AWSIngestionPipeline --template-body file://cloudformation-template.yaml --capabilities CAPABILITY_NAMED_IAM
```

#### 2. **Start Glue Crawler**

```bash
python scripts/glue_crawler_setup.py
```

#### 3. **Set Up EventBridge Rule**

```bash
python scripts/eventbridge_rule_setup.py
```

#### 4. **Trigger Databricks Notebook**

```bash
python scripts/databricks_notebook_trigger.py
```

### Monitoring & Debugging

- **CloudWatch Logs**: Tracks AWS Lambda and Glue job execution logs.
- **Databricks Job Monitoring**: Monitors job runs and error handling.
- **EventBridge Execution History**: Validates event triggers and execution success.

## Contributions

We welcome contributions! If you have ideas for improvements, submit a pull request.

## License

This project is licensed under the **MIT License**.

## Contact

For issues, support, or questions, please use the GitHub Issues section or contact the project maintainer via email.

