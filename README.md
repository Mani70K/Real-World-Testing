# Regulatory Compliance Reporting System

This project is a **Regulatory Compliance Reporting System** built using **.NET 8** for the backend, with **Jenkins** for frontend automation and **AWS RDS** as the primary database. The system is designed to generate detailed reports on total API call counts and total application counts over specific time periods. The workflow involves inputting the reporting date range (start and end dates) via Jenkins, processing the report generation logic with AWS ECS services, and storing the final reports in an S3 bucket.

## Key Features

- **API and Application Count Reporting**: The system allows users to generate reports that summarize the total API call counts and total application usage during a user-defined time frame.
- **Jenkins Integration**: Users can provide the report parameters (start and end dates) through Jenkins, which automates the workflow.
- **AWS ECS for Processing**: The report generation logic is processed asynchronously using AWS ECS services to ensure scalability and efficient resource usage.
- **S3 Storage for Reports**: Once the reports are generated, they are stored in an AWS S3 bucket for easy access and retrieval.
- **AWS RDS**: The system utilizes AWS RDS as the primary database to store and retrieve necessary data for the report generation.

## Workflow Overview

1. **Input Date Range via Jenkins**: The workflow starts when a user provides the start and end dates for the report through Jenkins. Jenkins then triggers the report generation process.
2. **Task Orchestration via ECS**: Once the date range is provided, the system uses AWS ECS services to process the data. This includes fetching the API call and application count metrics based on the provided time range from the RDS database.
3. **Report Generation**: After gathering the necessary data, the system generates a CSV report summarizing the total API and application counts.
4. **S3 Bucket for Storage**: The final report is stored in a designated AWS S3 bucket, where it can be retrieved later.

## System Components

### 1. **Backend** (.NET 8)
- The backend is developed in **.NET 8**, leveraging its robust capabilities to handle large data processing and report generation tasks. The backend is responsible for interacting with the RDS database, performing necessary computations, and generating CSV reports.
  
### 2. **Frontend Automation** (Jenkins)
- **Jenkins** is used for frontend automation, where users can easily input report parameters and trigger the backend processing workflow. Jenkins pipelines are configured to handle user input, initiate ECS tasks, and monitor the process.

### 3. **AWS ECS Services**
- **AWS ECS** (Elastic Container Service) is used for orchestrating the backend tasks. ECS allows the system to scale processing and handle multiple report generation requests in parallel, ensuring efficiency and scalability.

### 4. **AWS RDS** (Relational Database Service)
- **AWS RDS** is the primary database that stores historical data related to API calls and application usage. The backend interacts with RDS to retrieve data based on the provided start and end dates for report generation.

### 5. **AWS S3** (Simple Storage Service)
- Generated reports are stored in **AWS S3**, a reliable and scalable storage solution. Reports are saved in CSV format and can be easily accessed or shared from the S3 bucket.

## Detailed Workflow

1. **User Inputs Start and End Dates in Jenkins**: 
   - The user specifies a reporting period (start and end dates) in Jenkins. Jenkins triggers the backend .NET application to start processing.

2. **Task Execution Using ECS**: 
   - The ECS service kicks off the process by calling a series of backend services that handle data collection and computation.
   
   - **Metrics Service**: Fetches total API call counts from the RDS database based on the given dates.
   
   - **Application Count Service**: Gathers application usage data over the specified period.

3. **Data Storage**:
   - The processed data is written into a CSV file.
   
   - The generated report is saved in an AWS S3 bucket, categorized by date or other naming conventions for easy retrieval.

4. **Report Retrieval**: 
   - The final CSV report can be accessed from the AWS S3 bucket. It contains the total API call count and application count for the specified reporting period.

## Project Architecture

```bash
├── Backend (.NET 8)
│   ├── Metrics Service (API Call Count)
│   ├── Application Count Service
│   └── Report Generation
├── Frontend Automation (Jenkins)
│   └── Input Start/End Dates -> Trigger ECS Services
├── AWS ECS (Processing)
│   ├── Orchestrates Tasks
│   └── Ensures Scalability and Efficiency
├── AWS RDS (Database)
│   └── Stores Historical API and Application Usage Data
└── AWS S3 (Storage)
    └── Stores Generated Reports (CSV Format)
