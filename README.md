# DAP-Model-Advanced-Operations
* A DAP design and implementation project for City of Vancouver mainly on the Data Enriching, Protection, Governance and Observability.
* This step involves the 4 major steps namely:
![image 000](https://github.com/user-attachments/assets/2179592f-519a-4d15-b040-7ab41dd313a4)<br>
* The above image displays the DAP design we are implementing for the analysis.
* I selected the dataset related to rentals in Vancouver.
* I selected to work on the rental agencies in different areas of Vancouver.
* This second part of the DAP design includes the next process of DAP that is once the needed analysis data is available after Glue pipeline design.
* This included multiple details and segments discussed below.
* The different services used here by “Ajayi” are ‘S3’ to store the information both raw and transformed, ‘Glue’ to design needed ETL pipelines and data catalogues, ‘IAM’ to assign needed roles and permissions for performing activities, “KMS” to generate keys that can be used for encryption and decryption, “Athena” to create tables and databases, “CloudTrail” to track user details and actions, “CloudWatch” to create a dashboard, and others as per need.
## Step 1: Data Enriching
* Data enrichment in data management is all about augmenting raw data with relevant context and information that provides more value for analytical purposes.
* This cleanses the data and transforms it to provide meaningful insights, which again are useful to make better decisions.
* We have raw data stored in the “vrs-raw-ajayi” bucket, we can use different services like “Glue” for ensuring proper and valid data integration using pipeline thus enriching the data, “Athena” for creating proper tables, databases, that can further be used for querying and enriching data between tables and store resultant in ‘S3’ buckets, We can even use the “Sagemaker” to pre-process, clean and enrich the datasets using ML models, and other services. Here “Ajayi” explained it in 2 ways using “VPC”, “EC2”, and “Athena”.
### Enriching Using Athena:
* Here we will be using “Athena” to generate tables and databases that can be used to generate needed reports or results based on queries as per requirement.
![image 001](https://github.com/user-attachments/assets/44cc8a71-90bc-4ffd-8f13-8f6cf0d8c7c3)<br>
* The above image shows details of Athena table and DB creation
![image 002](https://github.com/user-attachments/assets/7505c618-abb3-45cf-a238-38ccf580f771)<br>
* The above image shows details of Athena SQL query results.
* You can see from above figure the table created using the sql commands. We created a table called “vrs_table_ajayi” and database called “vrs_db_ajayi”.
* We have also created related columsn as per need called “Total_Units”, “Rental_business_geo_local_area”, “Tou”, and “Outstanding_Units_Percentage” with related datasets.
* The end results are stored in “VRS_Athena_Results_Ajayi” folder in the “vrs-transformed-ajayi bucket”.
* We can also see how we can use SQL queries to get the details and also use the results to enrich our datasets as per need.
### Enriching Using EC2:
* Here we will be using “Ec2” to create web and general servers along with vpc, subnets, route tables, security groups and others needed things as per requirement. 
![image 003](https://github.com/user-attachments/assets/647cab83-c950-4bbb-a3ac-9e95d6e9bff9)<br>
* The above image shows details of VPC results.
![image 004](https://github.com/user-attachments/assets/17fdce61-de38-4530-abd6-14533f4203ac)<br>
* The above image shows details of Subnet results.
![image 005](https://github.com/user-attachments/assets/e0428ccc-d674-4454-820d-edbb72994913)<br>
* The above image shows details of Route Tables results.
![image 006](https://github.com/user-attachments/assets/0133e8db-9123-4984-bacf-d6eab3df439b)<br>
* The above image shows details of Internet Gateway results.
![image 006-1](https://github.com/user-attachments/assets/4d48cf23-3747-4bb0-bd7d-2fea406e797a)<br>
* The above image shows details of Security Group results.
![image 007](https://github.com/user-attachments/assets/d3887404-39ab-4bcf-8aea-4fddb16a91db)<br>
* The above image shows details of EC2 Instances results.
![image 008](https://github.com/user-attachments/assets/ab72132a-0155-4441-9bb7-b561fd5796bc)<br>
* The above image shows details of Web Server results.
![image 009](https://github.com/user-attachments/assets/524512f0-d469-4be8-9a3d-703bc35411d9)<br>
* The above image shows details of Web Server web page results.
* We can see the results using the EC2 services and VPC services.
* The above displayed are the results of VPS along with relevant information of VPC, subnets, route tables, internet gateway, EC2 instances, web server information, general server information, security groups, web server IIS role, and the IIS results as mentioned.

* The above image shows 
## Step 2: Data Protection
* In AWS, one can protect sensitive data by encrypting it to protect its confidentiality and security.
* AWS KMS provides a centralized control point for encryption keys so that users can create, manage, and use them to perform encryption and decryption automatically and with control over access to the keys using IAM policies.
* It improves data protection to be compliant with security standards.
* The data protection can be possible in many ways.
* The best available ways are to protect data by encryption and decryption, creating backups, snapshots of ec2 instances, and other methods.
### KMS Key method
* This method is where we create a KMS key. This key will be useful to ensure the data is protected by using this key.
* Only if you know the key will be able to access the encrypted data.
* We can also use this key to enable the whole bucket encryption using the option of “Server-side encryption with AWS Key Management Service keys (SSE-KMS)” of default encryption enabling. We can also use this key to encrypt the replication as well to protect data.
![image 010](https://github.com/user-attachments/assets/95fd58c1-e92c-4dbb-973b-2a0e8c49b7ad)<br>
* The above image shows details of KMS key Creation results.
![image 011](https://github.com/user-attachments/assets/33379912-4db5-4bee-971a-f5438fae1459)<br>
* The above image shows details of Bucket Default Enabling results.
### Bucket Data Backup
* The other method is to create a backup bucket called “vrs-transformed-ajayi-backup” to store the backup of “vrs-transformed-ajayi” bucket and also enable replication between these two buckets.
![image 012](https://github.com/user-attachments/assets/4d65d95b-12cb-4304-8ee9-3be90e0121df)<br>
* The above image shows 
![image 013](https://github.com/user-attachments/assets/c2d56597-0333-467a-9a36-35b66ca7fb57)<br>
* The above image shows details of Backup Bucket Creation results.
* We have seen how we can use kms key to protect data, enable encryption, data backup using the backup bucket “vrs-transformed-ajayi-backup” and “vrs-transformed-ajayi” bucket along with enabling replication between these two buckets.
## Step 3: Data Governance 
* Data governance is the discipline for establishing, implementing, and maintaining the structure for data across the enterprise.
* This means defining data quality, privacy, security, and compliance with regulatory standard policies, roles, and procedures.
* Starting with creating access controls, auditing data usage, enabling encryption capabilities for your data, and using features such as AWS Glue Data Catalog for managing and cataloging metadata, data governance in AWS is a combination of setup, management, and maintenance.
* To ensure proper data governance first we are supposed to extract the transformed data, then if needed we can even change the schema and the column names as needed.
* We then move on to detecting the sensitive data based on each row, then we do a specific pattern related to “Canada”, and finally redact the data detected using the pattern ‘****’.
![image 014](https://github.com/user-attachments/assets/03e8afee-159d-42af-95b2-3e53b7a0307a)<br>
* The above image shows details of Detect Sensitive Data results.
* To ensure proper data governance we do the process of evaluating the data quality using 3 conditions namely:
   * Completeness of "Outstanding_Units_Percentage" columns data is more than 95%
   * Uniqueness of "Total_units" column more than 75%
   * IsUnique condition on the "Rental_business_geo_local_area" column
* Using these 3 conditions we will be evaluating thedata quality and then save the passed results in the “Full_Rental_Results” folder and those failed in the “Missing_Rental_Results” folder in the “vrs-transformed-ajayi” bucket respectively.
![image 015](https://github.com/user-attachments/assets/2dbf5288-d85b-4a81-a0dc-3923d63f802d)<br>
* The above image shows details of Evaluate Data Quality results.
![image 016](https://github.com/user-attachments/assets/21f0cfae-f9c9-4788-ac32-7790ee3ddc3d)<br>
* The above image shows details of Conditional Router results.
![image 017](https://github.com/user-attachments/assets/26b36596-7c8a-45a6-9acb-adb269e2675a)<br>
* The above image shows details of data catalog.
![image 018](https://github.com/user-attachments/assets/91f1bd44-5a5b-4ea1-816e-5bc8cef2976d)<br>
* The above image shows the results of data catalog stored in 'Full Rental Results' folder of 'vrs_transformed_ajayi'bucket.
![image 019](https://github.com/user-attachments/assets/cdd8a0f1-49fd-4b4d-b542-e2e66a9e8a20)<br>
* The above image shows the results of data catalog stored in 'Missing Rental Results' folder of 'vrs_transformed_ajayi'bucket.
## Step 4: Data Observability 
* The real-time performance and health of the data platform in the rental standards domain is visualized using the data observability dashboard displayed in AWS CloudWatch.
* A customized dashboard tracks key metrics, including bucket storage utilization, number of objects in buckets, and associated estimated charges, giving a full view of data operations.
* We can see from below how we can create a dashboard with all the needed details to monitor.
* For instance if we want to track a particular bucket like “vrs-transformed-ajayi” mainly about the details of the number of objects in the buckets and the bytes or size of the data stored in the bucket.
* We can even create alarms to track usage of Glue job details, web server CPU utilization, and also the billing per day for a particular service or the whole bill of the data as shown.
* We can even track network flow details like the amount of network in and network out flow for each of the web server and the general servers used in the DAP design as sown in below diagram. We can even track other details also as per need. 
![image 020](https://github.com/user-attachments/assets/3bcab7a8-2e51-4591-b2c2-1d09ffe4deac)<br>
* The above image shows details of CloudWatch Dashboard results.
