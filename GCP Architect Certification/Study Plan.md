### Job Role Description
A Professional Cloud Architect enables organizations to leverage Google Cloud technologies. With a thorough understanding of cloud architecture and Google Cloud Platform, this individual can design, develop, and manage robust, secure, scalable, highly available, and dynamic solutions to drive business objectives.

The Google Cloud Certified - Professional Cloud Architect exam assesses your ability to:

- Design and plan a cloud solution architecture
- Manage and provision the cloud solution infrastructure
- Design for security and compliance
- Analyze and optimize technical and business processes
- Manage implementations of cloud architecture
- Ensure solution and operations reliability

### Study Material
- [Certification Exam Guide](Certification-Exam-Guide.md)


### Sample Case Studies
During the exam for the Cloud Architect Certification, some of the questions may refer you to a case study that describes a fictitious business and solution concept. These case studies are intended to provide additional context to help you choose your answer(s). Review some sample case studies that may be used in the exam.

- [Mountkirk Games](https://cloud.google.com/certification/guides/cloud-architect/casestudy-mountkirkgames-rev2/)
- [Dress4Win](https://cloud.google.com/certification/guides/cloud-architect/casestudy-dress4win-rev2/)
- [TerramEarth](https://cloud.google.com/certification/guides/cloud-architect/casestudy-terramearth-rev2/)

### Practice Exam
The Cloud Architect practice exam will familiarize you with types of questions you may encounter on the certification exam and help you determine your readiness or if you need more preparation and/or experience.
- [Launch The Exam](https://forms.gle/SHcLhSXckievBNBn6)

## Online Learning
### Coursera
- [Preparing for the Google Cloud Professional Cloud Architect Exam](https://www.coursera.org/learn/preparing-cloud-professional-cloud-architect-exam/home/welcome)

### QwikLabs
- [GCP Essentials](GCP-Essentials.md)

Cloud Architecture

This fundamental-level quest is unique amongst the other Qwiklabs offerings. The labs have been curated to give IT professionals hands-on practice with topics and services that appear in the Google Cloud Certified Associate Cloud Engineer Certification. From IAM, to networking, to Kubernetes engine deployment, this quest is composed of specific labs that will put your GCP knowledge to the test. Be aware that while practice with these labs will increase your skills and abilities, we recommend that you also review the exam guide and other available preparation resources.

#### [Orchestrating the Cloud with Kubernetes](https://google.qwiklabs.com/focuses/557?parent=catalog)
In this lab you will learn how to: Provision a complete Kubernetes cluster using Google Container Engine; Deploy and manage Docker containers using kubectl; and Break an application into microservices using Kubernetes’ Deployments and Services.
#### [Deployment Manager - Full Production](https://google.qwiklabs.com/focuses/981?parent=catalog)
In this lab you will launch a service using Deployment Manager, and monitor it using Stackdriver. You will set up basic black box monitoring with Stackdriver Dashboard and establish uptime check alert notification to trigger incident response.
#### [Continuous Delivery with Jenkins in Kubernetes Engine](https://google.qwiklabs.com/focuses/1104?parent=catalog)
In this lab you will deploy and completely configure a continuous delivery pipeline using Jenkins running on Kubernetes Engine and go through the dev - deploy process.
#### [Networking 102](https://google.qwiklabs.com/focuses/556?parent=catalog)
Properly secured networks control connections and access into, out of, and among your resources. In this lab, you will practice deploying Networks and Subnetworks in two different GCP projects and multiple instances within the Google Cloud.
#### [Site Reliability Troubleshooting with Stackdriver APM](https://google.qwiklabs.com/focuses/4186?parent=catalog)
The objective of this lab is to familiarize yourself with the specific capabilities of Stackdriver to monitor GKE cluster infrastructure, Istio, and applications deployed on this infrastructure.

### Documentation
Visit the [documentation page](https://cloud.google.com/docs/) with overviews and in-depth discussions on the concepts and critical components of GCP.

* [Shared VPC](https://cloud.google.com/vpc/docs/shared-vpc)
* [VPC Network Peering](https://cloud.google.com/vpc/docs/vpc-peering)


### Possible Exam Scenario's
#### Preemptible VM's
- Create and terminate machine to save costs, but preserve disk state.
    - --no-auto-delete --disk example-disk
- Managed instance group with PVM's keep recreating every minute.
    - Health check / firewall configuration
#### Backup and Disaster Recovery
- Rollback plan for managed instance group serving website - 100's of instances
    - Object versioning on static data in Cloud Storage
    - Rolling updates
    - NOT snapshots
- Backup critical database with zero downtime and minimal resource usage
    - Scheduled cron jobs
    - Backup database data to another location(persistent disk/Cloud Storage)
- App Engine - need to push risky update to live environment
    - Versioning/traffic splitting
    - Deploy update to small % of traffic as canary update
#### Network Design for Security and Isolation
- Instance group VM's keep restarting every minute
    - Failing health check
    - Configure firewall to allow proper access to instance group VM's (subnet, tag) from load balancer IP
- On-premises network access to proper network resources
    - Restrict ingress firewall access to on-premises network IP range
- Failover from on-premises load balancer hosted application to GCP hosted instance group (hot standby)
    - Consider security and compliance
    - Allow firewall access at instance group level (subnet/tag) from outside source
- External SSH access disabled, but operations team needs to remotely manage VM's
    - Give operations team access to Cloud Shell
    - Not same scenario as removing external IP's
#### Legal Compliance and Audits


# Study Plan

To learn the technologies to become a Google Cloud Architect you need to become familiar with the products and services offered by the platform. Not only that you will need an understanding of application development using the following methodologies:

* Monolithic application design (the old way).
* Database and other storage technologies (blob stores etc).
* Container based development and deployment.
* Microservices architecture.
* Serverless architecture.
* Application supporting technologies such as message queues etc.

The reason for using or not using the design components in the above list is not part of this study plan.

## Study Plan Steps

### Ad-hock Tasks

* Read your notes every day.
* Talk to skilled professionals.

### Review Certification Resources

* [Certification Exam Guide](https://cloud.google.com/certification/guides/cloud-architect/)

### Attend Instructor-Led Training

* [Cloud Infrastructure](https://cloud.google.com/training/cloud-infrastructure)

### Attend Online Training

* Coursera: [Architecting with Google Cloud Platform Specialization](https://www.coursera.org/programs/google-cloud-platform-training-specializations-vccvz)
  * [Google Cloud Platform Fundamentals: Core Infrastructure](https://www.coursera.org/learn/gcp-fundamentals/)
  * [Essential Cloud Infrastructure: Fundamentals](https://www.coursera.org/learn/gcp-infrastructure-foundation/)
  * [Essential Cloud Infrastructure: Core Services](https://www.coursera.org/learn/gcp-infrastructure-core-services)
  * [Elastic Cloud Infrastructure: Scaling and Automation](https://www.coursera.org/learn/gcp-infrastructure-scaling-automation)
  * [Elastic Cloud Infrastructure: Containers and Services](https://www.coursera.org/learn/gcp-infrastructure-containers-services)
  * [Reliable Cloud Infrastructure: Design and Process](https://www.coursera.org/learn/cloud-infrastructure-design-process)

### Review Exam Resources

* [Google Cloud Architect Exam Study Materials](https://medium.com/@earlg3/google-cloud-architect-exam-study-materials-5ab327b62bc8)
* [Google cloud certification cloud architect review](https://www.slideshare.net/JosephHolbrookVetera/google-cloud-certification-cloud-architect-review)
* [Cloud Architect exam: Tips & Resources](https://www.cloudreach.com/blog/google-certified-professional-cloud-architect-exam/)
* [Google Cloud Architect Quiz](https://cloudquiz.guru/google-cloud/google-cloud-architect/)

### Final Hands-On

* [Quiklabs Cloud Architecture Quest - 8:45](https://google.qwiklabs.com/quests/24)
* [Google Codelabs - Cloud](https://codelabs.developers.google.com/?cat=Cloud)

### Take the Practice Exam

* [FAQs about the exam](https://cloud.google.com/certification/faqs/#0)
* [Practice Exam](https://cloud.google.com/certification/practice-exam/cloud-architect)

### Book the Exam

At this point in time you should feel comfortable about booking the exam. If you are feeling a little weak on some of the subjects, spend more time reading and practicing them. Then book the exam.

* [Bottom of the Cloud Architect page](https://cloud.google.com/certification/cloud-architect)
