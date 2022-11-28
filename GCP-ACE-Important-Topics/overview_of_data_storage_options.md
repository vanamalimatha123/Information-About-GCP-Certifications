# Overview of Data Storage Options 

This module introduces the various data storage options available to your 
applications in Google Cloud.

## Learning Objectives
Choose the appropriate data storage option for application data.

  
## GCP Storage Service Options
- Cost-effective
- Varied choices based on your application or workload

![Dstorage at a glance](resources/storage_at_a_glance1.png)
![Dstorage at a glance](resources/storage_at_a_glance2.png)

### Cloud Storage
- Fully managed, highly available
- Cos-effective, scalable object/blob store
- Objects access via HTTP requests
- Object name is the key only

- **Ideal use case**:
  - Image and videos
  - Objects and blobs
  - Unstructured data
  - Static website hosting

### Firestore
- Fully managed, serverless, NoSQL
- Scalable, automatic horizontal scaling
- Native mobile and web client libraries
  - strongly consistent storage layer
  - a collection and document based data model
- Real-time updates and offline features
- Security access controls for data are built in, and enable you to handle
  data validation via a configuration language

- **Ideal use case**:
  - Native mobile or web client 
  - Document-oriented data
  - Large collection of small documents
  - Durable key-value data
  - Hierarchical data
  - Managing multiple indexes
  - Transactions
  
### Datastore (Firestore in Datastore mode)
- Fully managed, NoSQL
- Scalable
- data store automatically handles sharding and replication
  - This provides you with a highly available and durable database that 
    scales automatically to handle your applications load.
- Datastore provides a myriad of capabilities:
  - acid transactions
  - SQL like queries, Indexes
- Typical use cases includes product catalogs, user profiles, and transactions
  based on ACID properties.
- Data Store is not ideal for a relational database and it is not an effective 
  solution for analytic data.
- strongly consistent queries, transaction improvements, and the removal of
  the one per second limit on writes to an entity group.

- **Ideal use case**:
  - Server applications
  - Semi-structured application data
  - Durable key-value data
  - Hierarchical data
  - Managing multiple indexes
  - Transactions
  
### Cloud BigTable
- High performance wide column, NoSQL database service
- Sparsely populated table
- Can scale  to billions of rows and thousands of columns
- Can store TB to PB of data
- Big table is built for fast key value lookup and scanning over a defined
  key range.
  - It's similar to a spreadsheet that gives you access to any set of columns 
    from contiguous rows by searching only the value in the first column where 
    the key updates to individual rows are atomic.
- Bigtable offers seamless scaling. 
- Changes to the deployment configuration are immediate so there's no
  downtime during reconfiguration. 
- Cloud Bigtable supports the open source industry standard HBased API.

- **Ideal use case**:
  - Operational and analytical applications
  - Storing large amounts of single-keyed data
  - MapReduce operations
  
### Cloud SQL
- Managed services (replication, failover, backups)
- MySQL, PostgreSQL, and SQL services
- Relational database services
- Proxy allows for secure access of your Cloud SQL Second Generation instances 
  without setting Allow rules
  - Without your having to allow IP addresses or configure SSL
  - he proxy uses the Cloud SQL API to authenticate with Google Cloud
  
- **Ideal use case**:
  - Web frameworks
  - Structured data
  - OLTP workloads
  - Applications using MySQL/PGS
  
### Cloud Spanner
- Fully managed relational database service offering both strong consistency
  and horizontal scalability.
- Transactional consistency.
- Global Scale, high availability
- Multi-regional replication
- It is designed for mission critical OLTP applications. 
- Cloud Spanner provides automatic synchronous replication for high 
  availability
- 99.9999% SLA

- Unlike cloud SQL spanner requires every table to have a primary key.
  Another difference is that Spanner also supports interleaf tables, 
  where child rows are inserted into the table adjacent to the parent row.

- **Ideal use case**:
  - Mission-critical applications
  - High transactions
  - Scale and consistency requirement
  
### BigQuery
- lowcost- enterprise data warehouse for analytic
- fully managed service
  - meaning you don't need to worry about administration of your data warehouse
- Petabyte scale
- Fast response time
  - Bigquery can scan terabytes in seconds and terabytes in minutes.
- Serverless

- **Ideal use case**:
  - Online Analytical Processing (OLAP) workload
  - Big data exploration and processing
  - Reporting via Business Intelligence (BI) tools
  
### Firebase
- Mobile and web access to Google Cloud Storage
- Serverless third-party authentication and authorization 
- Realtime
- NoSQL JSON database
- Web and mobile hosting content
- Production-grade

- **Ideal use case**:
  - Images, pictures, and videos
  - Objects and blobs
  - Unstructured data
  - Mobile and web apps
  - Realtime
  - Atomic release managements
  - JS app support
  - Firebase integration
  
## Cache Your Application Data
- Memorystore automates complex tasks for Redis and Memcached caching engines
- Fully protocol compatible with each engine
- Ideal for high-performance scalable web application, gaming, and stream 
  process
- Fully managed system
- Google-grade security

## Review
Google Cloud platform has a rich set of services to enable you to store,
query, and manage different types of application data. Store files in 
Cloud Storage, use readers labs, Memcached Cloud to cache application 
data. It's easy to get started with Cloud Datastore and NoSQL database. 
Use it to store structured application data. Bigtable is a 
high-performance, wide column NoSQL database. Bigtable is ideal for high 
volume flat data such as sensor readings and data from Internet of Things 
or IoT devices. Cloud SQL is a managed service for MySQL and PostgreSQL. 
You can use Cloud SQL Proxy to easily and securely connect to your Cloud 
SQL instance. If your application's relational data will exceed the volume 
that can be optimally handled in Cloud SQL, or you need global reach, use 
Spanner. Spanner is a fully managed relational database service that 
offers both strong consistency and horizontal scalability. Spanner
supports global automatic synchronous replication with low latency. 
BigQuery is a fully managed data warehouse solution. Use BigQuery for
analytics workloads