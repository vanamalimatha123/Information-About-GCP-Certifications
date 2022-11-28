# Storage in The Cloud

Every application needs to store data. Different applications and 
workloads require different storage and database solutions. This module 
describes and differentiates among GCP's core storage options: Cloud 
Storage, Cloud SQL, Cloud Spanner, Cloud Datastore, and Google Bigtable.

## Learning Objectives

- Summarize the purpose of and use cases for: 
  - Cloud Storage
  - Cloud SQL
  - Cloud Spanner
  - Cloud Bigtable
- Choose between the various storage options on Google Cloud Platform
- Build a BigQuery table using data from Cloud Storage.
- Use SQL queries to analyze data stored in BigQuery.

## Module Introduction

Storage Options:
- Cloud Storage 
- Cloud SQL
- Cloud Spanner
- Cloud Data Store
- Google Big Table.

## Google Cloud Storage
- High performance, internet-scale
- High durability and high availability
- Simple administration
  - Does not require capacity management
- Object Storage:
  - It's not file storage, in which you manage your data in a hierarchy of
    folders
  - It's not block storage that OS manages the data as chunks of disk
  - The storage lets you address arbitrary bunch of bytes with a unique key
    - Often these unique keys are in the form of URLs which means 
      object storage interacts nicely with Web technologies
- The storage objects are immutable, which means that you do not edit 
  them in place but instead you create new versions
- It always encrypts the data on the server side before it is 
  written to disk
- data in-transit is encrypted using HTTPS
- Cloud Storage files are organized into buckets.
  - When you create a bucket, you give it a globally unique name.
- you can turn on object versioning on your buckets if you want.
  - Cloud Storage keeps a history of modifications
- Cloud Storage also offers lifecycle management policies:
  - delete objects since a specific time or only the last 3 versions
    
### Type Storage Class
`Multi-Regional`
  - Most frequently accessed
  - Availability SLA: 99.95%
  - Content storage and delivery
`Reginoal`
  - Accessed frequently within a region
  - Availability SLA: 99.90%
  - in-region analytics, transcoding
`Nearline`
  - Accessed less than once a month
  - Availability SLA: 99.00%
  - Long-tail content, backup 
  - access fee per GB
`Coldline`
  - Accessed less than once a year
  - Availability SLA: 99.00%
  - Archiving, Disaster recovery
  - access fee per GB, higher than Nearline

### Cloud Storage Interaction *(ways to bring data to the storage)*
- gsUtil
  - cloud storage command-line from cloud SDK
- Drag-n-Drop in GCP console from Chrome
- Online storage transfer service and offline appliance for petabyte
- Import and export tables from `BigQuery`
- Startup scripts, images, and general object storage from `Compute Engine`
- Object storage, logs, Datastore backups from `App Engine`
- Import and export tables from `Cloud SQL`

## Quiz Notes:
- Cloud Storage is NOT suitable for to providing the root file system 
  of a Linux virtual machine
- Cloud Storage objects live in buckets, some characteristics define on
  a per-bucket basis:
  - A geographic location
  - A globally-unique name
  - All Cloud Storage objects are automatically encrypted at rest
    
## Cloud Bigtable
- BigTable is a NoSQL database
- Bigtable as a persistent hash table
- Ideal for storing large amount of data with low latency
- Scalable
- Data encryption in-flight and at rest
- Control access via IAM
- NoSQL databases such as Cloud Bigtable are suitable when all items in the 
  database needn't have their integrity checked by a database schema. Why not? 
  Maybe you want your database items to contain variable fields, or maybe 
  because you simply want your application to manage database integrity.
- Some developers think of Cloud Bigtable as a persistent hashtable, which 
  means each item in the database can be sparsely populated, and is looked up 
  with a single key
  
## Cloud SQL
- Choice of MySQL or PostgreSQL
- Cloud SQL provides several replica services like read, failover, and 
  external replicas. This means that if an outage occurs, Cloud SQL can 
  replicate data between multiple zones with automatic failover
- On-demand and Schedule backup
- Scale Vertically *(Read and Write)*
- Scale Horizontally *(Read)*
- Each Cloud SQL database is configured at creation time for either MySQL or 
  PostgreSQL. Cloud Spanner uses ANSI SQL 2011 with extensions.

## Cloud Spanner
- It's a horizontal scalable
- Strong transactional consistency at global scale.
- SQL Queries
- Automatic replication
Cloud Spanner can scale to petabyte database sizes, while Cloud SQL is 
  limited by the size of the database instances you choose. At the time 
  this quiz was created, the maximum was 10,230 GB.
  
# Cloud Datastore
- Horizontal NoSQL DB
- Design for application backends
- Automatically handles sharding and replication
- Unlike Cloud Bigtable, it also offers transactions that affect multiple 
  database rows, and it lets you do SQL-like queries
- Cloud Datastore databases can span App Engine and Compute Engine applications
- Cloud Datastore stores structured objects.

# Storage Comparison
- `Cloud Datastore`
  - free daily quota that provides storage, reads, writes, deletes and small 
    operations at no charge
  - if you need to store unstructured objects or if you require support for 
    transactions and SQL-like queries.
  - provides terabytes of capacity with a maximum unit size of one megabyte 
    per entity
  - **USE CASE**: 
    - store a large amount of structured objects. app engine applications
  - **BEST FOR**:
    - semi-structured application data that is used in app engines' applications
- `Cloud Bigtable`
  - store a large amount of structured objects.
  - does not support SQL's queries nor does it support multi-row transactions.
  - petabytes of capacity with a maximum unit size of 10 megabytes per cell 
    and 100 megabytes per row
  - **BEST FOR**:
    - analytical data with heavy read/write events like AdTech, Financial or IoT data
- `Cloud Spanner`
  - full SQL support for an online transaction processing system
  - provides petabytes
  - **USE CASE**
    - Whenever high I/O, global consistency
  - **BEST FOR**
    - large scale database applications that are larger than two terabytes; for 
      example, for financial trading and e-commerce use cases.
    - large-scale database application
- `BigQuery`
  - to use its big data analysis and interactive query and capabilities.
  - **USE CASE**:
    - Data wearhouse
  - **BEST FOR**
    - interactive, querying, offline analytics
- `Cloud Storage`
  - **USE CASE**:
    - if you need to store immutable blobs larger than 10 megabytes such as 
      large images or movies
  - **BEST FOR**
    - structured and unstructured, binary or object data like images, large 
      media files and backups.
- `Cloud SQL`
  - full SQL support for an online transaction processing system
  - Cloud SQL provides terabytes of capacity
  - **BEST FOR**
    - web frameworks and in existing applications like storing user credentials
      and customer orders.
      
## Quiz Notes
- The Best storage for  developing an application that transcodes large video 
  files is the *Cloud Storage*
- ? The best storage for manufacture devices with sensors and need to stream huge
  amounts of data from these devices to a storage option in the cloud is
- You are building a small application. If possible, you'd like this 
  application's data storage to be at no additional charge. Which service has a
  free daily quota, separate from any free trials *Cloud Datastore*
- Your application needs to store data with strong transactional consistency, 
  and you want seamless scaling up. Which storage option is the best choice for 
  your application? *Cloud Spanner*
- Which GCP storage service  is often the ingestion point for data being moved 
  into the cloud, and is frequently the long-term storage location for data?
  *Cloud Storage*