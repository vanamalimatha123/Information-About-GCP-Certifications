# Containers in the Cloud
Containers are simple and interoperable, and they enable seamless, fine-grained 
scaling. Kubernetes is an orchestration layer for containers. Kubernetes Engine 
is Kubernetes as a service, a scalable managed offering that runs on Google’s 
infrastructure. You direct the creation of a cluster, and Kubernetes Engine 
schedules your containers into the cluster and manages them automatically, based 
on requirements you define. This module explains how Kubernetes Engine works 
and how it helps deploy applications in containers.

## Learning Objectives
- Define the concept of a container and identify uses for containers
- Identify the purpose of and use cases for Google Container Engine and 
  Kubernetes
- Build a Kubernetes cluster using Kubernetes Engine.
- Deploy and manage Docker containers in Kubernetes Engine using the kubectl 
  command.

## Containers and Kubernetes Engine 
- Just like Infrastructure as a Service (Iaas), it saves you infrastructure 
  chores
- Like a Platform as a service (PaaS), it was built with the needs of developers 
  in mind.
- The idea of a Container is to give you
  - the independent scalability of workloads like you get in a PaaS environment 
  - abstraction layer of the operating system and hardware, like you get in an 
    IaaS environment.
- In essence, you're visualizing the operating system rather than the hardware
- Containers are loosely coupled to their environments
  - Containers are a way to package software
  - Containers are easy to move around. 
  - Containers abstract away unimportant details of their environments
  - Deploying a containerized application consumes less resources and is 
    less error-prone than deploying an application in virtual machines

### Kubernetes
- Kubernetes makes it easy to orchestrate many Containers on many hosts
- Kubernetes is an open-source orchestrator for containers, so you can better 
  manage and scale your applications.
- Kubernetes lets you deploy containers on a set of nodes called a cluster
  - cluster s a set of master components that control the system as a whole, and
    a set of nodes that run containers
    - In Kubernetes, a `node` represents a computing instance. 
    - In Google Cloud, `nodes` are virtual machines running in Compute Engine
- Whenever Kubernetes deploys a container, or a set of related containers, it 
  does so inside an abstraction called a `pod`.
  - A pod is the smallest deployable unit in Kubernetes

## Introduction to Hybrid and Multi-Cloud Computing (Anthos)
- Distributing systems housed on-premises are difficult to upgrade
  - Upgrades are expensive
  - Life of servers are short

- Hybrid or multi-cloud architecture allows you to keep parts of your systems
  infrastructure on-premises while moving other parts to the Cloud
  - Move only some part of the workload to the cloud 
  - Move at your own pace
  - Take advantage of cloud scalability and low cost
  - Add specialized services to your compute resource stack 

### Anthos
- Kubernetes and GKE On-Prem the foundation
- On-Prem and Cloud environment stay in sync
- a rich set of tools is available:
  - Managing services on-premises and in the Could
  - Monitoring systems and services
  - Migrating application from VMs into your clusters.
  - Maintain consistent policies across all cluster, whether on-premisses or 
    in the Cloud
    
- `Google Kubernetes Engine on the Cloud` site of your hybrid network:
  - Google Kubernetes Engine is a managed production-ready environment for 
    deploying containerized applications.
  - Operates seamlessly with high availability and an SLA.
  - Runs certified Kubernetes ensuring portability across clouds and on-premises.
  - Includes auto-node repair, and auto-upgrade, and auto-scaling.
  - Uses regional clusters for high availability with multiple masters.
  - Node storage replication across multiple zones.

- `GKE deployed on-prem`:
  - Provides an easy upgrade path to the latest Kubernetes releases that have 
    been validated and tested by Google.
  - Provides access to container services on Google Cloud platform, such as 
    Cloud build, container registry, audit logging, and more.
  - It also integrates with Istio, Knative and Marketplace Solutions.
  

## Quiz Notes
- In Kubernetes, a group of one or more containers is called a pod. Containers
  in a pod are deployed together. They are started, stopped, and replicated as 
  a group.
  - The simplest workload that Kubernetes can deploy is a pod that consists 
    only of a single container.
- A Kubernetes cluster is a group of machines where Kubernetes can schedule
  containers in pods. The machines in the cluster are called `nodes` 
- Because the resources used to build Kubernetes Engine clusters come from 
  Compute Engine, Kubernetes Engine gets to take advantage of Compute Engine’s 
  and Google VPC’s capabilities.
- The Kubernetes Engine team periodically performs automatic upgrades of your 
  cluster master to newer stable versions of Kubernetes, and you can enable 
  automatic node upgrades too.
  
## LAB

#### Confirm that needed APIs are enabled`
- In the GCP Console, on the Navigation menu (Navigation menu), click 
  APIs & Services.
  - Scroll down in the list of enabled APIs, and confirm that both of these 
    APIs are enabled:
    - Kubernetes Engine API
    - Container Registry API
#### Start a Kubernetes Engine cluster`
- In GCP console, on the top right toolbar, click the Activate Cloud Shell button.
-  For convenience, place the zone that Qwiklabs assigned to you into an
   environment variable called `MY_ZONE`. At the Cloud Shell prompt, type 
   this partial command: `export MY_ZONE=us-central1-a`
- Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster 
  `webfrontend` and configure it to run 2 nodes:
  `gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2`
- It takes several minutes to create a cluster as Kubernetes Engine provisions 
  virtual machines for you.
- After the cluster is created, check your installed version of Kubernetes 
  using the kubectl version command: `kubectl version`
- The gcloud container clusters create command automatically authenticated
  kubectl for you.
- View your running nodes in the GCP Console. On the Navigation menu 
  (Navigation menu), click Compute Engine > VM Instances.
#### Start a Kubernetes Engine cluster
- Run and deploy a container:
   From your Cloud Shell prompt, launch a single instance of the nginx 
  container. (Nginx is a popular web server.)
  `kubectl create deploy nginx --image=nginx:1.17.10`
-  In Kubernetes, all containers run in pods. This use of the kubectl create
   command caused Kubernetes to create a deployment consisting of a single pod
   containing the nginx container. A Kubernetes deployment keeps a given number
   of pods up and running even in the event of failures among the nodes on 
   which they run. In this command, you launched the default number of pods, 
   which is 1.

**Note**: If you see any deprecation warning about future version you can
simply ignore it for now and can proceed further.

- View the pod running the nginx container: `kubectl get pods`
- Expose the nginx container to the Internet:
  `kubectl expose deployment nginx --port 80 --type LoadBalancer`
- Kubernetes created a service, and an external load balancer with a public 
  IP address attached to it. The IP address remains the same for the life of 
  the service. Any network traffic to that public IP address is routed to pods 
  behind the service: in this case, the nginx pod.
- View the new service: `kubectl get services`
- You can use the displayed external IP address to test and contact the nginx 
  container remotely.
- It may take a few seconds before the External-IP field is populated for your
  service. This is normal. Just re-run the kubectl get services command every 
  few seconds until the field is populated.
- Open a new web browser tab and paste your cluster's external IP address into 
  the address bar. The default home page of the Nginx browser is displayed.
- Scale up the number of pods running on your service: `kubectl scale deployment nginx --replicas 3`
- Scaling up a deployment is useful when you want to increase available 
  resources for an application that is becoming more popular.
- Confirm that Kubernetes has updated the number of pods: `kubectl get pods`
- Confirm that your external IP address has not changed: `kubectl get services`
- Return to the web browser tab in which you viewed your cluster's external IP 
  address. Refresh the page to confirm that the nginx web server is still responding.

## Quiz Notes
- reasons for deploying applications using containers.
  - Consistency across development, testing, production environments
  - Simpler to migrate workloads
- Kubernetes allows you to manage container clusters in multiple cloud providers.
- Google Cloud Platform provides a secure, high-speed container image storage 
  service for use with Kubernetes Engine.
- Google Cloud Platform offer its own tool for building containers, but 
  customers may choose not use it.
- Engine workloads run in clusters built from Compute Engine virtual machines