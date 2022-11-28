# Applications in the Cloud

App Engine is a Platform-as-a-Service ("PaaS") offering. The App Engine 
platform manages the hardware and networking infrastructure required to run 
your code. App Engine provides built-in services that many web applications 
need. This module describes how App Engine works.

## Learning Objectives
- Explain the purpose of and use cases for Google App Engine and Google 
  Cloud Datastore
- Compare the App Engine Standard environment with the App Engine Flexible 
  environment
- Express the purpose of and use cases for Google Cloud Endpoints
- Express the purpose of and use cases for Apigee Edge.
- Preview an App Engine application using Cloud Shell.
- Launch an App Engine application and then disable it.

## Introduction
- The App Engine platform manages the hardware and networking infrastructure
  required to run your code.
- App engine will scale your application automatically in response to the 
  amount of traffic it receives.
  - That’s why App Engine is especially suited for applications where the 
    workload is highly variable, like a web application
- So you only pay for those resources you use
- App Engine offers NoSQL databases, in-memory caching, load balancing, 
  health checks, logging, and user authentication to applications running in it

## Google App Engine Standard Environment
- Standard is the simpler.
  - Easily deploy application
  - Auto-scale workloads
  - Free daily quota
  - Usage base pricing
- Restrictions
  - No writing to local
    - it has to write to a database service
  - All request times out at 60s
  - Limits on third-party software

## Google App Engine Flexible Environment
- Build and deploy containerized apps
  - Your application runs inside Docker containers on Google Compute Engine 
    Virtual Machines
  -  App Engine manages these Compute Engine machines for you
- No Sandbox constrains
- Can access App Engine resources
- SSH access
- Allow writing to local disk
- Supports 3rd-party binary
- Network access
-  App Engine Standard Environment supports Java, Python, PHP, and Go, but in 
   the Flexible Environment, you upload your own runtime to run code in a 
   language of your choice
- App Engine Flexible Environment applications let their owners control the 
  geographic region where they

## Google Cloud Endpoints and Apigee Edge
- Helps you to create and maintain APIs
- Control access and validate calls with JSON web tokens and Google API keys
  - Identify web, mobile users with Auth0 and Firebase Authentication
- Generate client libraries 

## Quiz Notes
- Apigee Edge allows you to 
  - gradually decompose a pre-existing monolithic application, not implemented 
    in GCP, into microservices
  - to do business analytics and billing on a customer-facing API   
- Cloud End Point allows you to support developers who are building services 
  in GCP through API logging and monitoring.