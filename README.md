# Spotify Top 100 Data Pipeline

**Overview**

This repository contains the code and configuration for an end-to-end data pipeline that extracts Spotify's Top 100 songs data, transforms it, and loads it into an AWS data warehouse for analysis.

**Key Technologies**
* **AWS Services:** Lambda, S3, Glue, Athena
* **Programming Language:** Python
* **Spotify API:** For data extraction

**Pipeline Workflow**
1. **Data Extraction:**
   - Authenticates to the Spotify API.
   - Fetches Top 100 songs data.
   - Extracts relevant information.
2. **Data Transformation:**
   - Cleans and preprocesses the data.
   - Transforms data into a desired format.
3. **Data Storage:**
   - Stores transformed data in an S3 bucket.
4. **Data Warehousing:**
   - Creates a Glue Data Catalog to define the data schema.
   - Uses a Glue Crawler to discover and catalog data.
   - Queries the data using Athena.

**Project Structure**

This project aimed to create a fully automated data pipeline to extract, transform, and load (ETL) Spotify's Top 100 songs data into a data warehouse for analysis. This was achieved by leveraging AWS services such as Lambda, S3, Glue, and Athena.

- **Data Extraction**

    * **Authentication and Authorization:** Obtained necessary credentials from the Spotify Developer Dashboard.
    * **API Endpoint Selection:** Utilized the Spotify API's /v1/playlists/{playlist_id}/tracks endpoint to fetch the Top 100 songs.
    * **Lambda Function:** Created a Lambda function to:
      - Authenticate to the Spotify API.
      - Make HTTP GET requests to the selected endpoint.
      - Parse the JSON response and extract relevant data (track name, artist, album, popularity, duration, release date).
        
- **Data Transformation**

  * **Transformation Logic:** Developed Python code to:
    - Clean and preprocess extracted data (handle missing values, normalize text).
    - Transform data into a desired format (CSV, Parquet).
  * **Lambda Function:** Created another Lambda function to execute the transformation logic.
    
- * **Data Storage**

  * **S3 Bucket:** Created an S3 bucket to store the transformed data files.
  * **Data Writing:** The transformation Lambda function wrote the transformed data to the S3 bucket using the boto3 library.

- **Data Warehousing**

  * **Glue Data Catalog:** Created a Data Catalog in AWS Glue to define databases and tables for the data structure.
  * **Glue Crawler:** Created a Glue Crawler to discover and catalog the data files in the S3 bucket.
  * **Athena:** Used Athena to query the data stored in S3, leveraging the Glue Data Catalog.
    
- **Automation**

  * **CloudWatch Events:** Configured CloudWatch Events to trigger the Lambda functions for data extraction and transformation on a scheduled basis.
   
- **Additional Considerations**

  **Error Handling and Logging:** Implemented robust error handling and logging mechanisms.
  
  **Security:** Ensured proper security measures to protect sensitive information.
  
  **Scalability:** Designed the pipeline to be scalable for future growth.
  
  **Cost Optimization:** Optimized resource utilization and leveraged cost-saving strategies.

- **Future Enhancements**
  
  Explore additional data sources (e.g., lyrics, audio features) to enrich the dataset.
  
  Implement machine learning models to predict song popularity or categorize songs.
  
  Create interactive dashboards to visualize the data insights.
  
By following these steps, I successfully built a robust and scalable data pipeline to empower data-driven decision-making for music industry analysis.
