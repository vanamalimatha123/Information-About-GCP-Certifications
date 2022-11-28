# Cloud Client Libraries, the Cloud SDK, and Firebase SDKs

This module introduces the Cloud Client Libraries, the Cloud SDK, and Firebase 
SDKs.

## Learning Objectives
Understand how to set up and use Cloud Client Libraries, the Cloud SDK, and 
Firebase SDKs.

## What are the Cloud Client Libraries
- The best and recommended way to make requests to server
- Provide idiomatic code in each language
- Receive performance benefits from gRPC (Google Remote Procedure Calls) APIs
  - open source remote procedure call framework that can be run anywhere
  - GRPC makes it easier to build connected systems because it enables client 
    and server applications to communicate transparently.
    
### Cloud SDK
- Allows you to access GCP products and services
- consist of:
  - `gcloud` which create and manage GCP resource
  - `BQ` which is used for BigQuery and allows you to manage datasets, tables, 
    and other BigQuery entities. It also allows you to run queries
  - `gsutil` that is used to perform tasks in Cloud Storage, including:
    - create and manage buckets
    - upload, download, and create objects
    - move, copy and rename objects
    - manage access to stored data
- Allows you to run tools interactively or in your automated scripts

### Cloud Shell
- A browser based command-line tool
- Gives you access to a temp virtual machine with 5 GB of persistent disk and 
  storage and the cloud SDK pre-install
- Provides built-in authorization to Cloud Console projects and resources
- Includes built-in code editor

### Google Firebase
- Is mobile and web application development platform
  - Firebase SDK for Cloud Storage
  - App Engine standard environment + Firebase
  - User authentication
  - Cloud Functions
  - Cloud Vision API
  - Cloud Speech API
    
## Quiz Notes
Some uses for the API Explorer
- Execute an API method with some test parameter values.
- View details about the API request and response.
- Search for services and methods.

- Cloud Client Libraries are helpful because they support a language's natural 
  conventions and styles.
- Cloud Client Libraries handle low-level communication, retry logic, 
  and authentication
- Cloud Client Libraries are the latest and recommended approach to making 
  requests to the server
- `gcloud` command to list compute instances: `gcloud compute instances list`

- Use API Explorer as a sandbox to try out Google Cloud APIs.
- If you need to write some quick scripts to work with GCP services, use the 
  Google Cloud SDK. The SDK contains command line tools to help you script your 
  way out of a repetitive task
- Simply implement federated identity management using Firebase Authentication.
 