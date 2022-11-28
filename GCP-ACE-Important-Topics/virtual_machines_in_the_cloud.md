# Virtual Machines in the Cloud

Compute Engine lets you run virtual machines on Google’s global infrastructure. 
This module covers how Compute Engine works, with a focus on Google virtual 
networking.

## Learning Objectives
- Identify the purpose of and use cases for Google Compute Engine
- Summarize the various Google Cloud Platform networking and operational 
  tools and services
- Build a "Compute Engine" virtual machine using the Google Cloud Platform 
  (GCP) Console.
- Build a "Compute Engine" virtual machine using the gcloud command-line 
  interface.

## Introduction
- Compute Engine lets you run virtual machines on Google's global infrastructure
- Virtual Private Cloud Network (VPC), connects GCP resources to each other 
  and to the internet
  - Can segment our network
  - use firewall rules to restrict access to an instance
  - create static routes to forward traffic to specific destination
- The Virtual Private Cloud networks that you define have global scope
  - They can have subnets in any GCP region worldwide
  - subnets can span the zones that make up a region.
  - subnets have regional scope
  - You can also have resources in different zones on the same subnet.
  - You can dynamically increase the size of a subnet in a custom network by 
    expanding the range of IP addresses allocated to it.
  - If you increase the size of a subnet in a custom VPC network, the IP 
    addresses of virtual machines already on that subnet won't be affected.

## Compute Engine
- Compute Engine lets you create/run virtual machine on Google infrastructure
- A preemptible VM is different from an ordinary Compute Engine VM in only one 
  respect. You've given compute engine permission to terminate it if 
  it's resources are needed elsewhere.
- You can choose two kinds of persistent storage; `standard` or `SSD`.
  - If your application needs high-performance scratch space, you can attach a 
    `local SSD`, but be sure to store data of permanent value somewhere else
    because local SSDs content doesn't last past when the VM terminates.

## Important VPC Capabilities
- you can control access both incoming and outgoing traffic
- VPC Peering allows VPCs on different projects to talk to each other
- Shared VPC uses IAM to control who and what in one project can interact 
  with a VPC in another
- Load Balancing Options:
  - `Global HTTP(s)` Can route different URLs to different back ends
  - `Global SSL Proxy` non-HTTPS SSL traffic, support on specific port number
  - `Global TCP Proxy` non-SSL TCP traffic, support on specific port number
  - `Reginal` load balance on any traffic, support on any port number
  - `Reginal internal` load balance of traffic inside a VPC, use for internal 
    tiers of multi-tiers applications
-  DNS is what translates internet host names to addresses
- `CDN` global system of edge caches.
  - You can use this system to accelerate content delivery in your application.
  
## Lab Training
- To display a list of all the zones in the region:
  `gcloud compute zones list | grep us-central1`

- Choose a zone from that list other than the zone `us-central1-a` 
- To set your default zone to the one you just chose:
  `gcloud config set compute/zone us-central1-b`

- To create a VM instance called `my-vm-2` in that zone:

```bash
gcloud compute instances create "my-vm-2" \
--machine-type "n1-standard-1" \
--image-project "debian-cloud" \
--image-family "debian-10" \
--subnet "default"
```

## Quiz Notes:
- Networks are global; subnets are regional
- `Dedicated Interconnect`options is a Service Level Agreement available
