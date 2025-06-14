# YouTube Data Analytics Pipeline

## Overview
This project establishes a robust, scalable, and secure data engineering pipeline on AWS to ingest, transform, and analyze daily trending YouTube video data. It focuses on providing actionable insights into video categories and trending metrics across multiple regions, culminating in an interactive analytics dashboard.

## Architecture 
This project was built to achieve the following key objectives:
- **Automated Data Ingestion**: Develop a reliable mechanism to automatically ingest raw YouTube trending data from external sources.
- **Efficient ETL System:**: Transform raw, semi-structured data into a clean, structured, and query-optimized format suitable for analytics.
- **Centralized Data Lake**: Establish a scalable data lake on AWS to serve as a single source of truth for diverse datasets.
- **Scalability & Performance**: Design the architecture to seamlessly handle increasing data volumes and maintain high performance as the dataset grows.
- **Cloud-Native Solution**: Leverage AWS cloud services to overcome local processing limitations for vast amounts of data.
- **Business Intelligence & Reporting**: Create a comprehensive dashboard to visualize key metrics and answer critical business questions related to YouTube trends.

## Architecture 
The pipeline is designed to be serverless and event-driven:
- Raw data is ingested into an S3 Raw Layer.
- An AWS Lambda function is triggered upon new data arrival, transforming the data.
- Processed data is stored in Parquet format in an S3 Cleansed Layer and cataloged by AWS Glue.
- AWS Athena is used for interactive querying, and Amazon QuickSight connects to the Glue Catalog for robust reporting.

<img src="architecture.jpeg">

## AWS Services Used
This project effectively utilizes the following AWS services:

- **Amazon S3 (Simple Storage Service)**: Serves as the core data lake storage, hosting both raw and processed (Parquet) datasets. It provides the required scalability, security, and high availability.
- **AWS IAM (Identity and Access Management)**: Manages secure access to AWS services and resources securely.
- **AWS Lambda**: Acts as the serverless compute engine, triggered by S3 events, to perform data transformation (ETL) on the fly.
- **AWS Glue**: A serverless data integration service used to discover data schemas, create and manage the central Data Catalog (metadata repository), enabling SQL querying on S3 data.
- **AWS Athena**: An interactive query service that allows running standard SQL queries directly on data stored in S3, leveraging the AWS Glue Data Catalog, without needing to load data.
- **Amazon QuickSight**: A powerful, cloud-native business intelligence (BI) service used to build interactive dashboards for data visualization and reporting, connecting directly to the AWS Glue Data Catalog via Athena.

## Dataset Used
This project utilizes a publicly available Kaggle dataset containing daily statistics on popular YouTube videos across multiple months and regions.

### Dataset Features Include:
- Video title, channel title, publication time, and associated tags.
- Key engagement metrics such as views, likes, dislikes, and comment counts.
- Detailed video descriptions.
- A category_id field, linked to a separate JSON file, provides region-specific video categories.

**Link:** [https://www.kaggle.com/datasets/datasnaek/youtube-new](https://www.kaggle.com/datasets/datasnaek/youtube-new)

## QuickSight Dashboard
An interactive Amazon QuickSight dashboard has been developed to visualize key trends and insights from the cleansed YouTube data. The dashboard provides a comprehensive view of:
- Overall viewership and engagement metrics.
- Trending video categories and their performance.
- Regional content popularity and distribution.

<img src="Youtube Analytics Dashboard.jpg">
