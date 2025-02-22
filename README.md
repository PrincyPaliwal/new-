# Serverless Lakehouse Accelerator

This accelerator helps organizations transition to a cost-efficient, serverless data lakehouse using Databricks SQL Serverless, Delta Sharing, and Unity Catalog.

## Purpose

The accelerator simplifies the setup of a serverless lakehouse environment, enabling organizations to leverage the benefits of serverless compute, fine-grained access controls, and seamless data sharing.

## Features

1.  Lower-cost compute with serverless SQL
2.  Fine-grained access controls with Unity Catalog
3.  Pre-configured Delta Sharing setup

## Implementation

The accelerator uses the Databricks REST API to automate the following tasks:

1.  Creates a Serverless SQL warehouse.
2.  Configures Unity Catalog for secure access control.
3.  Sets up Delta Sharing for cross-organization data sharing.

## Getting Started

Follow these steps to set up the Serverless Lakehouse Accelerator:

## 1. Prerequisites

1.  A Databricks workspace.
2.  A Databricks personal access token (PAT) with appropriate permissions.
3.  Python 3.6 or higher installed.

## 2. Installation

1.  **Install Libraries:** Install the required Python libraries:

    ```bash
    pip install databricks-sdk requests
    ```

## 3. Configuration

1.  **Create Configuration File (Recommended):**  It's best practice to store sensitive information like API keys in a separate configuration file. Create a file named `config.json` in the same directory as your script. Add the following content, replacing the placeholder values with your actual values:

    ```json
    {
      "DATABRICKS_HOST": "https://<your-databricks-workspace>.cloud.databricks.com",
      "DATABRICKS_TOKEN": "dapi-xxxxxxxxxxxxxxxxxxxx",
      "CATALOG_NAME": "serverless_catalog",
      "SCHEMA_NAME": "lakehouse_schema",
      "WAREHOUSE_NAME": "serverless_sql_warehouse",
      "DELTA_SHARE_NAME": "serverless_delta_share",
      "SHARE_RECIPIENT": "partner_org"
    }
    ```

## 4. Running the Accelerator

1.  **Save the Script:** Save the provided Python code as a file (e.g., `lakehouse_setup.py`).
2.  **Run the Script:** Open your terminal, navigate to the directory where you saved the script, and execute it:

    ```bash
    python lakehouse_setup.py
    ```

    The script will print messages indicating the progress and results of each step.

## 5. Python Code

### Code Extracted from Notebooks

#### Databricks Job Orchestration

```python
# Variables and Values
DATABRICKS_INSTANCE = "https://<your-databricks-instance>"
DATABRICKS_TOKEN = "dapi-xxxxxxxxxxxxxxxxxxxx"
DATABRICKS_JOB_ID = "<your-databricks-job-id>"

# Import variables from the Serverless_Databricks_Job_Orchestrator_01 notebook
%run "./Serverless_Databricks_Job_Orchestrator_01"

import json
import os
import requests

def lambda_handler(event, context):
    url = f"{DATABRICKS_INSTANCE}/api/2.1/jobs/run-now"
    headers = {
        "Authorization": f"Bearer {DATABRICKS_TOKEN}",
        "Content-Type": "application/json"
    }
    payload = {"job_id": DATABRICKS_JOB_ID}
    
    response = requests.post(url, headers=headers, json=payload)
    
    if response.status_code == 200:
        return {"status": "Success", "run_id": response.json()["run_id"]}
    else:
        return {"status": "Error", "message": response.text}
```

This script triggers a Databricks job via API call, handles errors, and ensures smooth job execution.

## Conclusion

By following these steps, you can easily set up a Serverless Lakehouse with Databricks, leveraging serverless SQL, Unity Catalog, and Delta Sharing. The provided Python scripts streamline the process, ensuring a smooth deployment.

