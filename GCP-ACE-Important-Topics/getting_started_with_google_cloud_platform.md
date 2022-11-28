# Getting Started with Google Cloud Platform

GCP customers use projects to organize the resources they use. They use Google Cloud Identity and Access Management, also called “IAM,” to control who can do what with those resources. They use any of several technologies to connect with GCP. This module covers each of these topics, and it introduces a service called Cloud Launcher that is an easy way to get started with GCP

## Learning Objectives
- Identify the purpose of projects, folders, and organization nodes on Google Cloud Platform
- Describe the purpose of and use cases for Identity and Access Management
- List the methods of interacting with Google Cloud Platform
- Build a solution deployment using Cloud Launcher

## Module Introduction
- use project to orginize the workload
- use `IAM` or Identity Access Managment to control access
- project are the main way to orginize the resources in GCP
- use `IM` to implement least priviliege

### The Google Cloud Platform Resource Hierarchy
- policies are inherited downwards
- all GCP resources are belonged to a project
- `Project ID`: permanent, unchangeable, human-readable identifier and has to be unique across GCP
- `Project Name`  assigned by the user, not uniqe and changeable 
- `Project number` that is assigned by GCP and is unique and unchangeable
- we could  organize the projects to folders
  - use folder to represent different department, teams, environment in the organization, applications 
  - allow teams to delegate different admin rights
  - resources in the folder inherit `IAM` policies from the folder 
  - to use folder, we need organization node at the top level
- the organization node is the root node for GCP
  - ability to have centralized visibility on how resources are used and apply policies centrally 
- more generous policy is the one that takes effect
- the policies implemented at a higher level can't take away access that's granted at a lower level

### Indentity and Access Managment (IAM)
- `IAM` allows admin to let `who` to do `what` on `which` resources
- There are 3 kind of roles in Cloud IAM:
  - Primitive: Very broad and apply to all GCP services in a project
    - Owner
    - Editor
    - Viewer
    - Billing Admin
  - Predefined: more fine-grained permission to a particular GCP services 
  - Custom: define precise set of permission
     - at project or organization level, can NOT be used at folder level
- Service accounts control service-to-service interaction
  - gives identity to a service

### Interacting with GCP
- Console 
- SDK and the Cloud Shell
  - gcloud
  - gsutil (Cloud Storage)
  - bq (BigQuery)
- Mobile App
- REST-based API

- It allows view and mange all resources and projects
- Enable/Disable API GCP services 
- Gives access to cloud shell

###  Cloud Marketplace (formerly Cloud Launcher)
- a tool to quickly deploy software to GCP

## Quiz Notes:
- All Google Cloud Platform resources are associated with a project.
- In Google Cloud IAM: if a policy applied at the project level gives you 
  *Owner permissions*, your access to an individual resource in that project 
  might NOT be restricted to View permission if someone applies a more 
  restrictive policy directly to that resource.
- Service accounts are used to provide:
  - A way to restrict the actions a resource (such as a VM) can perform
  - Authentication between Google Cloud Platform services
  - A way to allow users to act with service account permissions
- Google takes care of the lower parts of the stack, and customers are
    responsible for the higher parts
- difference between IAM primitive roles and IAM predefined roles:
  - Primitive roles affect all resources in a GCP project. Predefined roles 
    apply to a particular service in a project.
- You pay only for the underlying GCP resources you use, with the possible 
  addition of extra fees for commercially licensed software.
