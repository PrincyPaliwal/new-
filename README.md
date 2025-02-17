## AI-Powered Data Quality & Anomaly Detection



## Overview

The AI-Powered Data Quality & Anomaly Detection repository provides a comprehensive solution for ensuring data integrity and detecting anomalies using **AWS Glue DataBrew, Databricks AutoML, and AWS CloudWatch**. It automates data cleansing, anomaly detection, and real-time alerting to maintain high-quality data for analytics and decision-making.

This repository includes tools and workflows that integrate seamlessly with **AWS and Databricks**, helping teams monitor, govern, and enhance data quality efficiently.

## Folder Structure

The repository is structured into **Accelerators**, **Operational Tools**, and **Documentation** to support various data quality and anomaly detection use cases.

### 1. Accelerators

Pre-built solutions designed to address specific challenges in data quality, anomaly detection, and governance:

- [**Data Quality Governance**](https://github.kadellabs.com/digiclave/databricks-accelerators/-/tree/dev/Accelerators/data_quality_governance?ref_type=heads): Ensures data consistency and integrity in Databricks environments.
- [**Automated Anomaly Detection**](https://github.kadellabs.com/digiclave/databricks-accelerators/-/tree/dev/Accelerators/anomaly_detection?ref_type=heads): Uses AutoML to detect data anomalies in real time.
- [**CloudWatch Alerting**](https://github.kadellabs.com/digiclave/databricks-accelerators/-/tree/dev/Accelerators/cloudwatch_alerting?ref_type=heads): Real-time monitoring and alerting on data issues.

### 2. Operational Tools

Utilities and frameworks to support data quality monitoring and integration with various cloud platforms:

- [**AWS Glue DataBrew Pipeline**](https://github.kadellabs.com/digiclave/databricks-accelerators/-/tree/dev/OTS_Tool/aws_glue_databrew?ref_type=heads): Automates data cleaning and transformation tasks.
- [**Databricks AutoML Workflow**](https://github.kadellabs.com/digiclave/databricks-accelerators/-/tree/dev/OTS_Tool/databricks_automl?ref_type=heads): ML-based anomaly detection using Databricks AutoML.
- [**Real-Time Monitoring**](https://github.kadellabs.com/digiclave/databricks-accelerators/-/tree/dev/OTS_Tool/real_time_monitoring?ref_type=heads): Integrates CloudWatch for real-time anomaly alerts.

### 3. Documentation

Guides and references for setting up and using the accelerators and tools:

- **Accelerators Overview**: Details on available accelerators and their use cases.
- **Operational Tools Overview**: Guides for implementing monitoring and anomaly detection frameworks.

## Getting Started

### Prerequisites

Ensure you have the following before using the accelerators and tools:

- **Databricks Workspace**: With appropriate permissions on AWS.
- **AWS Credentials**: IAM roles with permissions for DataBrew, CloudWatch, and SNS.
- **Databricks API Token**: For AutoML and job execution.
- **AWS CLI** configured (`aws configure`).

### Installation

Clone the repository to your local environment:

```bash
git clone https://github.kadellabs.com/digiclave/databricks-accelerators.git
cd databricks-accelerators
```

Navigate to the desired accelerator or tool and follow the setup instructions.

## Usage

1. **Configure Cloud Credentials**: Set AWS IAM roles and Databricks tokens.
2. **Run DataBrew Job**: Clean and preprocess data using Glue DataBrew.
3. **Train AutoML Model**: Detect anomalies using Databricks AutoML.
4. **Monitor and Alert**: Use AWS CloudWatch to detect issues and send alerts.

Example command to run the pipeline locally:

```bash
python main.py
```

## Automation

For continuous monitoring, deploy as an **AWS Lambda function** or schedule Databricks Jobs:

- Automate anomaly detection with scheduled runs.
- Set up **SNS, Slack, and PagerDuty** notifications for real-time alerting.

## Contributions

We welcome contributions! Submit a pull request or open an issue for feature requests or improvements.

## License

This project is licensed under the MIT License.

## Contact

For support or questions, use the GitHub Issues section or contact the project maintainers via email.

---

Let me know if you need any modifications! 🚀

