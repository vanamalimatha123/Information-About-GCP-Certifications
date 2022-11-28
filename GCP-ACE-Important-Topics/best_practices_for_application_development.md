# Best Practices for Application Development

This module introduces best practices for application development.

## Learning Objectives
- Design and develop secure, scalable, reliable, loosely coupled application 
  components and microservices.
- Understand how to re-architect applications for the cloud.

## Loosely Coupled Microservices and API Gateways
- Applications that run in the Cloud must be built for:
  - global reach
  - scalability, and high availability
  - security
  
### Implementing Microservices
- Monolithic applications
  - Codebase becomes large
  - Packages have tangled dependency
- Microservices
  - Service boundaries matches business boundaries
  - Codebase is modular
  - Each service can be independently updated, deployed, scan scaled

### Perform Asynchronous Operations
- Keep the operations in the user thread at a minimum.
- Performed backend operations asynchronously.
- Use event-driven processing where possible

### Design for Loose Coupling
- Design application components so that they are loosely-coupled at runtime
  - Tightly coupled components can make an application less resilient to 
    failures, spikes in traffic, and changes to service.
- You can use a Cloud Pub/Sub topic as a message queue. Publishers can 
  publish messages to the topic and subscribers can subscribe to message 
  from this topic
  
### Implement Stateless Components for Scalability
- Implement application components so that they don't store state 
  internally or access a shared state
- Design each application so that it focuses on compute tasks only
  -  This approach enables you to use a worker pattern to add or remove 
     additional instances of the component for scalability
- Application components should start up quickly to enable efficient 
  scaling and shut down gracefully when they receive a termination signal. 
  
### Cache Content
- Caching content can improve application performance and lower network 
  latency
  - When a user requests data, the application component should check the 
    cache first. If data exists in the cache meaning the TTL has not 
    expired, the application should return the previously cached data
- Use a content delivery network to cache web pages

### Implement API gateways
- This let you to make backend functionality available to consumer 
  applications.

## Security, Reliability, and Migration

### Use Federated Identify Management 
- Identify users by using external identify provider such Google, Facebook,
  Twitter, GitHub
- This will minimize your effort for user administration

### Implement Health-check Endpoint
- Implement health-check endpoint for each service
- The endpoint handler should check the health of all dependencies and 
  infrastructure components

### Setup logging and Monitor Your Application Performance
- Treat your logs as event streams.
- Logs constitute a continuous stream of events that keep occurring as long as 
  the application is running
- Write your log to an event stream such as standard out and let the 
  underlying infrastructure collate all events for later analysis and 
  storage.

### Handle Transient and Long-lasting Errors Gracefully
- Applications should implement retry logic with exponential backup and 
  fail gracefully if the errors persist.
- When errors are more long-lasting, the application should not waste CPU 
  cycles attempting to retry the request over and over again.
  - In this case, applications should implement a circuit breaker and 
    handle the failure gracefully.
- For errors that are propagated back to the user, consider degrading the 
  application gracefully instead of explicitly displaying the error message
  
### Consider Data Sovereignty and Compliance Requirements

### Perform High Availability Testing and Develop Disaster Recovery Plans
- Identify failure scenarios
- Create disaster recovery plans
  - people, process, tools
- Perform tabletop testing

### Implement Continues Integration and Delivery Pipeline
- With a robust CICD pipeline, you can test and roll out changes incrementally 
  instead of making big releases with multiple changes
- This approach enables you to:
  - lower the risk of regressions
  - debug issues quickly
  - roll back to the last stable build of necessity.
  
### Use the Strangler Pattern to Re-architect Applications
- Incrementally replace components of the old application with new services  