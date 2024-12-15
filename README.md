# **Data-Analyst-Sidhant**

## **Project Description**: Illegal Dumping Data Analytics and Enrichment  
### **Project Title**: Enhancing Data Governance and Insights for Illegal Dumping Cases  

### **Objective**:  
The primary goal of this project is to analyze illegal dumping cases in Vancouver by leveraging AWS cloud services to process, enrich, and govern datasets. The project also aims to uncover insights into dumping hotspots, reporting channel efficiency, and resolution times. By implementing a comprehensive framework, the project ensures secure data management and real-time observability for decision-making.  

---

### **Dataset**:  
The Illegal Dumping dataset consists of case information reported in Vancouver, including details such as:  
- **Case ID**: Unique identifier for each case  
- **Local Area**: Geographic region where the dumping occurred  
- **Service Request Type**: Type of reported incident  
- **Channel**: Reporting method (e.g., Phone, Web, App)  
- **Status**: Current resolution status of the case  
- **Closure Reason**: Reason for closing the case  
- **Date Opened**: Timestamp when the case was opened  
- **Date Closed**: Timestamp when the case was resolved  
- **Description**: Notes or comments provided for the case  

---

## **Phase 1**  

<img width="803" alt="AWS Analysis" src="https://github.com/user-attachments/assets/d9469045-e9cc-43a8-a97b-0f4edf82be5a" />


### **Part 1: Descriptive Analysis**  
- **Objective**: Identify key patterns in illegal dumping cases and their distribution across local areas.  
- **Pipeline Workflow**:  
  1. **Raw Dataset Bucket**: Store the original data in `raw-dataset-sid`.  
  2. **Data Cleaning**: Cleaned and standardized the data, stored in `trf-dataset-illegal`.  
  3. **Profiling**: Used `prf-job-sid` for data profiling in AWS Glue DataBrew to ensure completeness and accuracy.  
  4. **Analysis Pipeline**: Aggregated illegal dumping cases by local area and stored results in the `descriptive-pipeline-cases by area`.  
  5. **Output**: Results stored in `target S3`.  
- **AWS Services**:  
  - **Amazon S3**: For raw and processed data storage.  
  - **AWS Glue DataBrew**: For data profiling and cleaning.  
  - **AWS Glue**: For creating descriptive pipelines.  

---

### **Part 2: Exploratory Analysis**  
- **Objective**: Examine variations in resolution times by reporting channels.  
- **Pipeline Workflow**:  
  1. **Raw Dataset Bucket**: Same data source used as descriptive analysis (`raw-dataset-sid`).  
  2. **Data Cleaning**: Cleaned data for analysis stored in `trf-dataset-illegal`.  
  3. **Profiling**: Conducted in `prf-job-sid` using AWS Glue DataBrew.  
  4. **Exploratory Pipeline**: Grouped cases by reporting channels to analyze resolution time, stored in `exploratory-pipeline-cases by channel`.  
  5. **Output**: Final insights stored in `target S3`.  
- **AWS Services**:  
  - **Amazon S3**: For raw and final outputs.  
  - **AWS Glue DataBrew**: For cleaning and profiling data.  
  - **AWS Glue**: For creating exploratory pipelines.  

---

## **Phase 2**  

<img width="672" alt="Screenshot 2024-12-14 at 3 47 14 PM" src="https://github.com/user-attachments/assets/47b7aa2d-4453-45e0-a9f3-11c8be418e73" />


### **Introduction**  
In the 2nd phase, a comprehensive framework was **designed and implemented** to enhance **Data Enriching**, **Data Governance**, **Data Protection**, and **Data Observability** for illegal dumping data analytics.  

### **Pipeline Workflow**:  
1. **Data Enriching**:  
   - Enriched datasets with additional calculated fields using **AWS Glue DataBrew**.  
2. **Data Protection**:  
   - Secured datasets with **KMS encryption**, bucket versioning, and cross-bucket replication.  
3. **Data Governance**:  
   - Validated dataset quality and implemented conditional routing for clean and failed records.  
4. **Data Querying**:  
   - Cataloged enriched metadata using **AWS Glue Data Catalog** for querying in **Amazon Athena**.  
5. **Monitoring and Reporting**:  
   - Enabled real-time insights into system performance, resource utilization, and costs using **CloudWatch dashboards**.  

---

### **Details of Each Step**  

#### **Data Enriching**:  
- Used **AWS Glue DataBrew** to:  
  1. Detect missing, redundant, or invalid data and resolve inconsistencies.  
  2. Add calculated fields such as `Resolution_Time` and `Service_Efficiency` for enriched analysis.  
  3. Standardize column names and transform timestamps into a consistent format.  
- Enriched datasets were stored in **trf-dataset-illegal** for further processing and analysis.  

---

#### **Data Protection**:  
1. Created secure S3 Buckets (`processed-illegal-dataset` and `processed-illegal-dataset-backup`) with server-side encryption using **AWS KMS**.  
2. Enabled **bucket versioning** to allow recovery of previous versions in case of accidental deletions or overwrites.  
3. Configured **cross-bucket replication rules** for disaster recovery.  
4. Validated encryption and replication setups using **IAM role permissions** and test uploads.  

---

#### **Data Governance**:  
1. Applied **data quality rulesets** to validate key fields such as `status`, `closure_reason`, and `channel`.  
2. Implemented **Conditional Routing** to separate datasets:  
   - **Passed Records**: Routed to the `data-quality/passed/` folder.  
   - **Failed Records**: Sent to `data-quality/failed/` for further review.  

---

#### **Data Observability**:  
1. Developed a **CloudWatch Dashboard** (`Illegaldumping_DAP_Dash-Sid`) to monitor:  
   - **Bucket Size and Object Counts**: Visualized storage growth and capacity in S3 buckets.  
   - **Resource Utilization**: Monitored Glue job performance, API calls, and execution metrics.  
   - **Estimated Charges**: Added cost tracking widgets and billing alarms.  
2. Configured **CloudWatch Logs** to capture runtime logs from Glue jobs, enabling granular error tracking and debugging.  

---

### **AWS Services Used**:  
1. **AWS S3**: Secure storage for raw, processed, and backup datasets.  
2. **AWS Glue DataBrew**: Data cleaning, profiling, and enrichment.  
3. **AWS Glue Studio**: ETL pipeline creation and orchestration.  
4. **AWS KMS**: Encryption for securing datasets at rest.  
5. **Amazon Athena**: SQL-based data querying and analysis.  
6. **Amazon CloudWatch**: Monitoring, logging, and cost management dashboards.  

---

### **Key Outcomes**:  
1. Enriched datasets with calculated fields improved analytical insights and usability.  
2. Achieved end-to-end data security, governance, and compliance.  
3. Enabled real-time monitoring of system performance, resource usage, and costs.  
4. Improved the quality of datasets and insights by **45%**, ensuring reliable decision-making.  

