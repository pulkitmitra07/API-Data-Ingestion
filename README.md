## Weather Data Ingestion Challenge

# Overview
This repository presents the solution for the Weather Data Ingestion Challenge. The objective is to ingest weather data from the OpenWeatherMap API and AirVisual API for Sydney into AWS on an hourly cadence. Additionally, an ETL (Extract, Transform, Load) step is integrated to enrich and transform the data before storing it in AWS S3.

# Solution Components
- Lambda Function: Python-based Lambda function (index.py) responsible for fetching data from OpenWeatherMap and AirVisual APIs, transforming the data, and ingesting it into AWS S3.
- AWS CloudFormation Template: Defines the infrastructure as code (IAC) for deploying AWS resources including Lambda function, S3 bucket, IAM role, CloudWatch Events rule, and associated permissions (weather_data_ingestion_template.yaml).
- EventBridge/CloudWatch Rule: Configured to trigger the Lambda function at an hourly cadence for data ingestion.
- S3 Bucket: Stores the ingested weather data and transformed data after the ETL step.

# Deployment Steps
- Clone Repository: Clone this repository to your local environment or fork it to your own GitHub account.
- Deploy CloudFormation Stack: Use the AWS CLI or AWS Console to deploy the CloudFormation stack using the weather_data_ingestion_template.yaml file.
-  Once the stack is created, go to the AWS Lambda console:
    Navigate to the Lambda function created by the CloudFormation stack (WeatherDataIngestLambda-unique).
    Click on "Upload from" and choose "Zip file" option.
    Select the Lambda function code zip file (WeatherDataIngestLambda-unique.zip) containing your Lambda function code and dependencies.
    Click on "Save" to update the Lambda function with the new code and dependencies.
- Test Lambda Function: After deployment, test the Lambda function using the AWS Lambda console. Configure a test event with the desired location data (e.g., Sydney).
- Verify Data Ingestion: Check the specified S3 bucket for the ingested weather data files and transformed data files.

# Assumptions
- OpenWeatherMap API and AirVisual API provide hourly reporting data for Sydney.
- Secure management of API keys and credentials is in place.
- The ETL step includes data enrichment and transformation to provide meaningful insights from the raw data.

# Personal Twist
- Integration of AirVisual API: The solution integrates data from both OpenWeatherMap and AirVisual APIs to provide comprehensive weather and air quality data.
- ETL Step: The ETL step performs data enrichment and transformation, including combining data from multiple APIs and providing a consolidated output.

# Repository Structure
- index.py: Python code for the Lambda function (index.py), including data fetching, transformation, and ingestion logic.
- weather_data_ingestion_template.yaml: AWS CloudFormation template for infrastructure deployment.
- README.md: Documentation providing setup instructions, explanations, and usage guidelines.
