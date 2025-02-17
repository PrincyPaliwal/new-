# Real-time Streaming Analytics Accelerator

## Overview
The **Real-time Streaming Analytics Accelerator** processes streaming data such as logs, financial transactions, and IoT sensor data. This solution integrates **Amazon Kinesis, AWS Lambda, and Databricks Structured Streaming** to provide low-latency insights, scalability, and seamless integration with analytics platforms.

## Features
- **Low-latency analytics**: Processes real-time data streams for instant insights.
- **Scalability**: Handles high-throughput event streams efficiently.
- **Serverless Architecture**: Utilizes AWS Lambda for event-driven triggers.
- **Integration with BI Tools**: Supports Amazon QuickSight, Tableau, and Power BI.

## Use Cases
1. **Log Analytics** – Monitor application logs for real-time anomaly detection.
2. **Financial Transactions Monitoring** – Detect fraud and ensure compliance.
3. **IoT & Sensor Data Processing** – Analyze real-time sensor readings.
4. **Clickstream Analysis** – Track user activity and detect bot traffic.
5. **Stock Market & Trading Analytics** – Process financial data streams for insights.

## Folder Structure
### 1. **Infrastructure Provisioning**
- **Terraform Scripts**: Provisions AWS resources including Kinesis, Redshift, S3, and IAM roles.

### 2. **Streaming Data Processing**
- **Databricks Structured Streaming Scripts**: Transforms and writes data to Delta Lake & Redshift.

### 3. **Event-driven Processing**
- **AWS Lambda Functions**: Triggers notifications based on processed data events.

## Getting Started
### Prerequisites
Ensure you have:
- **AWS Account** with permissions for Kinesis, Redshift, S3, Lambda, and Databricks.
- **Databricks Workspace** with appropriate configurations.
- **Terraform & AWS CLI** for deployment automation.

### Installation
Clone the repository:
```bash
git clone https://github.com/your-repo/realtime-streaming-analytics.git
cd realtime-streaming-analytics
```

### Setup & Deployment
#### 1. **Deploy Infrastructure using Terraform**
```bash
cd infra/
terraform init
terraform apply -auto-approve
```

#### 2. **Deploy Databricks Streaming Notebook**
Run the Databricks Structured Streaming script to process Kinesis data and write to Delta Lake:
```python
spark.readStream \
    .format("kinesis") \
    .option("streamName", "real-time-stream") \
    .option("region", "us-east-1") \
    .load() \
    .writeStream \
    .format("delta") \
    .outputMode("append") \
    .start("s3://streaming-processed-data-bucket/delta-lake/")
```

#### 3. **Deploy AWS Lambda Function for Event Notifications**
```bash
zip lambda.zip lambda/handler.py
aws lambda create-function --function-name DataProcessedNotifier \
    --runtime python3.8 --role arn:aws:iam::YOUR_ACCOUNT_ID:role/lambda_exec_role \
    --handler handler.lambda_handler --zip-file fileb://lambda.zip
```

### Data Visualization in Amazon QuickSight
Once data is stored in Redshift:
1. Connect Amazon QuickSight to Redshift.
2. Create dashboards to visualize transactions and trends.

## Monitoring & Debugging
- **AWS CloudWatch Logs**: Monitor Lambda and Kinesis event processing.
- **Databricks UI**: Track real-time processing and job execution.
- **Step Functions Execution History**: Validate workflow execution.

## Contributions
We welcome contributions! Submit a pull request with enhancements.

## License
This project is licensed under the **MIT License**.

## Contact
For support or inquiries, use the GitHub Issues section or contact the project maintainer via email.

