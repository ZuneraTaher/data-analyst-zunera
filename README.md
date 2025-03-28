# *data-analyst-zunera*
Descriptive Analysis of Parks, Recreation, and Pets in Vancouver

## *Project Title*

Understanding Parks, Recreation, and Pet Facilities in Vancouver

## *Objective*

The primary goal of this project is to conduct a descriptive analysis of parks, recreation, and pet facilities in the City of Vancouver. This analysis aims to:

Summarize key characteristics of park usage.

Identify trends in recreational facility access.

Generate insights that can inform city planning and public service improvements.

## *Dataset*

The dataset includes polygon representation data of parks and recreational areas in Vancouver, containing the following key features:

PARK_ID: Unique identifier for each park.

PARK_NAME: Name of the park.

AREA_HA: Area of the park in hectares.

PARK_URL: URL for more information about the park.

Geom: Geometric representation of the park's boundaries (polygon data).

geo_point_2d: Geographic coordinates of the park (latitude and longitude).

## *Data Source*

The dataset is sourced from the City of Vancouver's open data portal, which provides access to various datasets related to city planning and public services.

## 1. Methodology

Using services such as Amazon S3, AWS Glue, Glue DataBrew, and AWS Athena, the project implements a complete ETL (Extract, Transform, Load) workflow—from data ingestion and transformation to storage and analysis.

## Data Ingestion:

The dataset is ingested into an Amazon S3 bucket named *cityofvancouver-raw-zun*, where it is organized into subfolders for raw and transformed data. This setup facilitates efficient data management and retrieval.

![image](https://github.com/user-attachments/assets/b7befefd-b9e2-449d-9274-3ebd567ff12c)


## Data Cleaning and Transformation:

AWS Glue is utilized to automate the data cleaning process. This includes identifying and handling missing values, correcting data types, and removing duplicates.
AWS Glue DataBrew provides a visual interface for data preparation, allowing for easy transformation of the dataset without the need for extensive coding. Data profiling is conducted to assess data quality and consistency.

![image](https://github.com/user-attachments/assets/0c82cb50-0e0c-498b-a63a-7d97176feb92)


## Data Storage:

Once the dataset is cleaned and processed, it is stored in a structured format within the S3 bucket. Advanced cloud functionalities such as KMS-based encryption are configured to ensure the confidentiality and integrity of the data. This involves creating a key in AWS Key Management Service (KMS) to encrypt sensitive data stored in S3.

![image](https://github.com/user-attachments/assets/5066c6d0-1e9c-42fe-9957-07abe35ecf7d)

![image](https://github.com/user-attachments/assets/93fb1da0-9352-4d97-a7fd-4536803a6d3f)




## Data Versioning and Lifecycle Management:

Bucket versioning is enabled on the S3 bucket to maintain multiple versions of objects, allowing for recovery from accidental deletions or overwrites.

Lifecycle policies are implemented to automatically transition older data to cheaper storage classes, optimizing costs while ensuring data availability.

![image](https://github.com/user-attachments/assets/7320ebb8-6998-474d-931b-58f49c55a6d2)



## Data Analysis:

The cleaned dataset is queried using AWS Athena, which allows for running SQL queries directly on the data stored in S3. This enables the extraction of meaningful insights regarding usage patterns, location distribution, and data quality.

## Example SQL queries include:

SELECT PARK_NAME, AREA_HA FROM "cov_prk_trf_system" WHERE AREA_HA > 1.0;

![image](https://github.com/user-attachments/assets/e73b6577-c563-4f5b-a388-71add251574c)


## Monitoring and Auditability:

AWS CloudWatch is configured to monitor the S3 bucket and Glue jobs, providing insights into resource utilization and performance. Alarms are set up to notify stakeholders of any anomalies or threshold breaches, ensuring proactive management of the data infrastructure.

![image](https://github.com/user-attachments/assets/d53a67cc-21f4-4616-9b6f-265ecca9947e)

AWS CloudTrail is utilized to log and monitor all API calls made within the AWS environment. This service provides a detailed history of actions taken on AWS resources, enabling auditing and compliance tracking. By capturing events related to data access and modifications, CloudTrail enhances security and accountability, allowing the team to review who accessed or modified data and when.

![image](https://github.com/user-attachments/assets/855a2628-4776-444b-adac-1a1fae821741)



## 2. Descriptive Statistics

Calculate summary statistics for key variables, including:

Total Area of Parks: Sum of all park areas to understand the total green space available.

Average Park Size: Mean area of parks to gauge the typical size of recreational spaces.

Number of Parks by Type: Categorize parks (e.g., community parks, pet-friendly parks) and count the number in each category.

Distribution of Parks by Area Size: Create bins for park sizes (e.g., small, medium, large) and count the number of parks in each bin.

Count of Parks with Pet Facilities: Identify parks that allow pets and count them.

## 3. Data Visualization
   
Create visual representations to illustrate findings:

Time Series Graphs: If historical data is available, show trends in park area over time.

Bar Charts: Display the number of parks by type (e.g., community parks, pet-friendly parks).

Pie Charts: Represent the share of parks with pet facilities versus those without.

Heatmaps: Visualize park locations across the city, highlighting areas with high concentrations of parks.

## 4. Facility Usage Analysis

Analyze usage patterns of parks and recreational facilities:

If available, analyze data on park usage (e.g., foot traffic, events held). 

Identify peak usage times and popular parks based on available data.
 
Assess the accessibility of parks in different neighborhoods.

## 5. Insights and Findings

Summarize the insights derived from the analysis, highlighting:

Areas with High Concentrations of Parks: Identify neighborhoods with a high number of parks and recreational facilities.

Trends in Park Accessibility and Usage: Discuss any observed trends in how parks are accessed and used by the community.

Preferences for Pet-Friendly Parks: Analyze which parks are most popular among pet owners and any trends in pet facility usage.

## 6. Recommendations

Provide actionable recommendations based on the findings to inform:

Future Park Development: Suggest areas for new parks or enhancements to existing parks based on community needs.

Maintenance Strategies: Recommend maintenance schedules for high-traffic parks to ensure they remain accessible and enjoyable.

Targeted Marketing Campaigns: Propose marketing strategies to promote underutilized parks or recreational programs.

Enhancements to Pet-Friendly Facilities: Suggest improvements to parks that cater to pet owners, such as adding more pet waste stations or dog parks.

## Tools and Technologies

Data Analysis: Python (Pandas, Matplotlib, Seaborn) or R for data analysis.

Data Visualization: Tableau or Power BI for creating interactive dashboards.

## Cloud Services:

AWS S3 for data storage.

AWS Glue for data cleaning and transformation.

AWS Glue DataBrew for visual data preparation.

AWS Athena for querying the dataset using SQL.

AWS KMS for managing encryption keys.

AWS CloudWatch for monitoring and alerting.

## Deliverables

A detailed report summarizing the methods, findings, and recommendations.

Visualizations and dashboards to present key insights clearly.

A presentation for stakeholders to communicate important findings and suggestions for future action.
