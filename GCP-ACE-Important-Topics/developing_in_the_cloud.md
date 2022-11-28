# Developing, Deploying and Monitoring in the Cloud

Popular tools for development, deployment, and monitoring just work in 
GCP. Customers also have options for tools in each of these three areas 
that are tightly integrated with GCP. This module covers those tools.

## Learning Objectives
- Understand options for software developers to host their source code.
- Understand the purpose of template-based creation and management of 
  resources.
- Understand the purpose of integrated monitoring, alerting, and debugging.
- Build a Deployment Manager deployment.
- Update a Deployment Manager deployment.
- View the load on a VM instance using Stackdriver.

## Development in the Cloud

### Cloud Resource Repositories
- Fully featured Git repositories on GCP
  - keep code private to a GCP project and use IAM permissions to protect 
    it
  - provides git version control
- A developer choose to store source code in Cloud Source Repositories to
  - reduce work
  - To keep code private to a GCP project

### Cloud Functions
- Create a single-purpose functions that respond to event without a server
  or runtime
- Cloud Functions can trigger on events in Cloud Storage, Cloud Pub/Sub, 
  or in HTTP call
- Your code executes whenever an event triggers it, no matter whether it 
  rarely happens, or many times per second. That means you don't have to 
  provision compute resources to handle these operations.

### Deployment: Infrastructure as code
- It's more efficient to use template to setup your environment. 
  - That means a specification of what the environment should look like
- GCP provides Deployment Manager to let you do just that. It's an 
  Infrastructure Management Service that automates the creation and 
  management of your Google Cloud Platform resources for you.

### Monitoring: Proactive instrumentation
- Stackdriver is GCP's tool for monitoring, logging and diagnostics
  - Monitoring
    - platform, system and applications metrics
    - Uptime/health checks
    - Dashboard and alerts
  - Logging
    - platform, system and applications logs
    - Log search, view filter and export
    - Log-based metrics
  - Trace
    - Latency reporting and sampling
    - Per-URL latency and statics
  - Error Reporting
    - Error notifications
    - Error dashboard
  - Debugger
    - Debug applications
  - Profiler
    - Continues profiling of CPU and memory consumption
  
## Quiz Notes
- a GCP customer choose to use Cloud Source Repositories because they 
  don't want to host their own git instance, and they want to integrate 
  with IAM permissions.
- customer choose to use Cloud Functions because their application contains
  event-driven code that they don't want to have to provision compute resources 
  for.
- Customer choose to use Deployment Manager because Deployment Manager is 
  an infrastructure management system for GCP resources.
- to define alerts on your GCP resources, such as when health checks fail
  you can use Stackdriver Monitoring
- Stackdriver Logging lets you view logs from your applications, and filter 
  and search on them.
- Stackdriver Logging lets you define metrics based on your logs.