# BigData and Machine Learning in the Cloud

GCP's big-data and machine learning offerings are intended to help customers 
get the most out of data. These tools are intended to be simple and practical 
to embed in your applications. This module describes the available big-data and 
machine learning services and explains the usefulness of each.

## Learning Objectives
- Understand the purpose of and use cases for the products in the Google 
  Cloud big data platform..
- Understand the purpose of and use cases for the products in the Google
  Cloud machine learning platform.
- Load data into a BigQuery table from Cloud Storage.
- Use SQL queries to analyze data in BigQuery.

### Google Cloud Big Data Platform
- Integrated Serverless Platform
  - Serverless means you don't have to worry about provisioning Compute 
    Instances to run your jobs
    - The services are fully managed, and you pay only for the resources 
      you consume
  - The platform is integrated, so that GCP data services work together to 
    help you create custom solutions.

#### Cloud Dataproc is managed Hadoop
- Fast, easy, managed way to run Hadoop and Spark/Hive/Pig on GCP
- Create cluster in 90 sec or less on average
- Scale cluster up and down even when they are running
- It is based on the MapReduce programming model which Google invented 
  and published.
- The MapReduce model is, at its simplest, means that one function, 
  traditionally called the "Map function," runs in parallel with a massive 
  dataset to produce intermediate results. Another function, 
  traditionally called the "Reduce function," builds a final result set 
  based on all those intermediate results. 
-  you can monitor your cluster using Stackdriver.

#### Cloud Dataflow
- if your data shows up in real time or it's of unpredictable size or rate
- Process data using Compute Engine instance
  - Clusters are sized for you
  - Automated scaling, no instance provisioning required
- unified programming model and a managed service and it lets you develop and 
  execute a big range of data processing patterns:
- `ETL` (extract/transform/load) pipelines to move, filter, enrich, shape
  data
- Data analysis: batch computation or continues computation using streaming
- Use case:
  - fraud detection and financial services
  - IoT analytics and manufacturing
  - healthcare and logistics and click stream
  - point of sale and segmentation analysis in retail.
- Why Use:
  - Orchestration: create pipeline that coordinate services, including 
  - Integrates with GCP services like BigQuery, and BigTable
    - Open source Python and Java SDKs

#### BigQuery
- BigQuery is a fully managed data warehouse
- Provides near real-time interactive analytics of massive datasets, 
  using SQL syntax
- Getting data into BigQuery:
  - You can load it from cloud storage or cloud data store
  - stream it into BigQuery at up to 100,000 rows per second
- No cluster maintenance is required 
- BigQuery separates storage and computation

#### Cloud Pub/Sub and Cloud Datalab
- Cloud Pub/sub (Publisher/Subscribers)is scalable reliable messaging
  - Supports many to many asynchronous messaging
  - Application components make push/pull subscription to topics
  - Includes support for offline consumers
- Why Use:
  - Building blocks for data ingestion in Dataflow, Internet of Things 
    (IoT), Marketing Analytics
  - Foundation for Dataflow stream 
  - Push notification for cloud-based applications
  - Connect application across GCP (Push/pull between Compute Engine and 
    App Engine)
- Interactive tool for large-scale data exploration, transformation,
  analysis, and visualization
- Integrated Open-source 
  - Built on Jupyter
    
### Google Cloud Machine Learning Platform
- The Google Machine Learning Platform is now available as a cloud service so 
  that you can add innovative capabilities to your own applications.
- Why use ML platform:
  - For structured data
    - Classification and regression
    - Recommendation
    - Anomaly detection
  - For Unstructured data:
    - Image and video analytics
    - Text analytics
    
#### Cloud Vision API
- Analyze images with simple REST API
  - Logo detection, label detection, etc
- you can:
  - Gain insight from images
  - Detect inappropriate images
  - Analyze sentiment
  - Extract text
    
#### Cloud Natural Language API (Cloud Speech API )
- Convert audio to text 
- Return text in real-time
- Highly accurate, even in noisy environments
- Access from any device

#### Cloud translation API
- Translate arbitrary string between thousands of language pairs
- Programmatically detect a document's language
- Supports for dozens of languages

## Cloud Video Intelligence API
- Annotate the contents of videos 
- Detect scene language
- Flag inappropriate content
- Support for a variety of video formats
