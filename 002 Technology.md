# Technology
Largest part of the exam. Will make up at least 34% of the questions.


# Services
Cloud platforms have so many services. The reason they exist is because they each serve a different use case that had to be solved in the past, and so many people rely on cloud infrastructure.

# Compute
## Elastic Cloud Compute (EC2)
Host virtual servers with elastic compute in the cloud, called __instances__.
- Foundation in which AWS first provided as a cloud service.
- Served to entice people to use unused server resources, as a win-win for customer and AWS. Customer has somewhere to run their application and AWS can use up their free resources
- Can provision EC2 instances in a single click
- Can use preconfigured templates called AMIs
- Deploy apps directly to instances
- 750 free compute hours with free tier (basic) plan

#### Use Case
Deplay:
- a database
- a web app
All while getting the benefits of cloud infrastructure.

#### How to access
- AWS Management Console (webpage)
- Command Line Interface (CLI)
- EC2 Instance Connect
- SSH/PuTTY using ssh public/private key pair.

#### Pricing
- On-Demand (pay as you go) - for unpredictable computing that always need to complete
- Spot Instances (CHEAPEST) - Bid for unused compute/resources, great if it compute can be done later on
- Reserved Instances - for predictable workloads, upfront for 1 or 3 year options
- Dedicated Host (physical server, usually for compliance) - can host windows servers.
- Savings Plan (pay compute per hour) - 1 or 3 year options. Can change compute services, OS or instance types at anytime. No capacity reservation.

#### Features
ELB (Elastic Load Balancing) - Distribute incoming traffic across multiple EC2 instances. Demand based.
Your choices:
 - Classic Load Balancers
 - Application Load Balancers
 - Gateway Load Balancers
 - Network Load Balancers

EC2 Auto Scaling
Adds and replaces EC2 instances across AZs. Demand based. i.e. Horizontally scaling. Note: Vertically scaling describes individual resource upgrades, like CPU, storage or RAM.

## Lambda
Serverless released in 2018. Instead of having to host an EC2 instance to run something once, Lambda runs on a trigger. That allows you to run something that does something once, and in response to an event.
Game changer.
e.g. process incoming files from S3 bucket, send an email when a task finishes, upload a file that was processed by Python.

### Features
1. Supports a lot of popular programming languages:
    - Java
    - Go
    - PowerShell
    - NodeJS
    - Python3
    - C#
    - Ruby
2. Author code via IDE or via Cloud9 (the AWS console)
3. Execute code in response to events
4. Has a 15 minute timeout (not good for tasks longer than 15 minutes, use EC2 instead)

### Pricing
Always has a free tier
Charged based on duration and number of requests/executions.
1,000,000 free requests each month on free tier.

## Fargate
Serverless compute for containers, AWS version of Docker is Elastic Container Service (ECS). Don't need to provision hardware or servers.

### Pricing
Has no upfront costs, only pay for resources used

## Lightsail
Deploy all resources needed for quick small projects, like WordPress sites and test environments. Good for people with no cloud experience.
$3.50 monthly fee as a starter.
Simple UI.
Also provides another service called Lightsail for Research

## Outposts
Connects on-prem servers to allow cloud services. Basically supports hybrid deployments. 
Offers 2 services:
 - Outposts Rack
 - Outposts Servers
These services will deliver hardware to your data center to help migrate private clouds to hybrid cloud models

## AWS Batch
Process large workloads into smaller batches. Can run hundreds and thousands of jobs.

## Wavelength
Delivers low latency applications via 5G networking. Useful so mobile users can access your application really fast.
Consists of Zones and Subnets

## Exam tips
Remember EC2 pricing options:
On Demand
Spot
RI
Dedicated Hosts
Savings Plan

Remember EC2 real world use cases. Good for deploying APPLICATIONS and/or DATABASES that you fully control.

Remember horizontal vs vertical scaling

Remember Load Balancers:
- Classic
- Network (layer 4: udp, tls, tcp)
- Application (layer 7: http/https)
- Network

Remember how to connect to EC2 instances:
- Console
- Instance Connect
- SSH (requires keypair)
- Systems Manager

Remember ECS vs EKS. ECS: Docker, EKS: Kubernetes

Remember serverless responsibility. You only have to worry about code, not infrastructure. Fargate is considered a serverless container manager

# Storage

## Simple Storage Service (S3)
As described in the name, it is an incredibly simple service used to store files and data, like a windows folder.
Files are called __objects__ and are stored in __buckets__ which you can compare to folders within a root directory.
Objects can be configured to be private to AWS instance, or public to the world, great for serving websites.
Essentially unlimited storage.
Can programatically upload, download and manage objects via CLI or SDKs, such as boto3 in Python.
Also supports versioning, and has a great way to see who accessed it via access logs.
Region specific.

In terms of durability, S3 Standard class offers 11 nines of durability (99.999999999%), meaning your chance of losing the file due to corruption in S3 is tiny.

For Availability, S3 Standard class offers 99.99% availability, meaning you can access it virtually anytime you want.

## S3 Storage Classes
1. S3 Standard
2. S3 Intelligent-Tiering
3. S3 Infrequent Access (IA)
4. S3 One Zone IA
5. S3 Glacier
6. S3 Glacier Deep Archive
7. S3 Outposts (on-prem storage, with AWS features allowed)

Pricing becomes lower as you descend down the classes, at the cost of availability.
6 for example, may take 6-12 hours for the data to come back up, which would be great for decade long backups of archival data, like for tax expenses. 

### Use cases
1. Static websites (a webpage with no dynamic content, something like a portfolio or even a JSON file)
2. Data archive (business expenses or historical data)
3. Analytic systems (in tandem with Athena and Redshift)
4. Mobile apps

## EC2 Storage

### Instance Store
These are physical storage connected to EC2 instances that do not persist after the instance is stopped, good for parsing or computing data that doesn't need to be retained.
- High I/O performance
- Temporary storage
- No extra cost

### Elastic Block Store (EBS)
Virtual storage that scales to whatever your application inside EC2 needs, typically good for hosting databases. These EBS can be disconnected from an instance and plugged into another service, like another EC2 instance in the same Availability Zone. Great for persistent data.
- Highly available
- Highly durable
- Scalable with no downtime
- Snapshot capabilities (backups)

### Elastic File System (EFS)
Network file storage like a shared drive, that is __only__ supported in the Linux file system. It can communicate across EC2 instances within the same region, across different availability zones or other AWS managed services.
EFS is more expensive than EBS.
- Fully managed
- Automatic scaling
- Concurrent access

## Storage Gateway
Hybrid storage service to connect on-prem servers and data to AWS services. This services is good for moving backups to cloud, hosting some files on the cloud and some sensitive data on-prem or just reducing costs using hybrid model.

## AWS Backup
Manages backup data from AWS resources such as EC2, EBS, EFS, etc.

# Content Delivery
This relates to delivering content on a global scale, while maintaining low latency. Uses a combination of caching on edge locations and requesting data if there is a high demand or changes from the host.

## CloudFront
Global delivery of content even if your data or application is only hosted inside a single region. This is the main driver to AWS' model of Availability, at a global scale.
The service can serve static websites from S3, stop DDoS attacks and even support geo-restriction, allowing only certain countries access to your content.

## Global Accelerator
This service also is responsible for improving overall availability of applications in AWS. The end-user/accessor of your application will be routed via this service to get the lowest latency possible, if they are not close to your region. Also reroutes traffic to healthy endpoints, incase certain region AZ's are down.

## S3 Transfer Acceleration
This service specifically improves content delivery to and from S3 buckets over long distances thanks to edge locations and the multiple regions. This is how S3 bucket objects are so highly available across the world. This allows users to upload to a central bucket across the world.

# Networking
Networking is a crucial part of the cloud, and there must be ways to manage connections from one point to another, while maintaining privacy and security where necessary.

## Virtual Private Cloud
Allows you to set up a private network where you can launch resources and allows you to manage access to whomever you choose using NACLs (Network Access Control List) and route tables (IP addresses and ranges). Supports internet access via Internet Gateway, site-to-site VPN or hybrid model access.
_"It's like a fence around a perimeter of a shop, only allowing access through the main gate"_

## Route 53
DNS service manager, allows you to sign up and configure domains and domain names. Also provides health checks on AWS resources and supports hybrid models.

## Direct Connect
The service that is the catalyst for hybrid models, connecting on-prem networks to cloud services. Data travels from a private network for private data centers to AWS.

## AWS Site-to-Site VPN
In contrast to Direct Connect, VPN data travels through public internet and encrpyted. Connects on-prem data to AWS.

## API Gateway
Allows you to build and manage APIs, such as REST APIs in AWS. Connects with services such as S3, DynamoDB, RDS and Lambda.

# Database
With the amount of databases types that exist, even before AWS was adopted, there was a need to create similar database models/architecture on AWS to store data, it is a crucial part of a large amount of applications in the world. The following are used to support different use cases.

## Relational Database Service (RDS)
Relational DBs (supports SQL, tables and schemas). This service allows you to launch any type of relational DBs easily in the Cloud. Supports Oracle, MySQL, Aurora, PostgreSQL, MSSQL, MariaDB, etc. Also has a good read-replica service, to give read-only access to applications that need to quickly read data, while also boosting overall availibility and durability.

## Aurora
MySQL and PostgreSQL compatible, created by Amazon. 5x faster than MySQL and 3x faster than Postgres while being cheaper. Get all of the benefits of RDS.

## DynamoDB
NoSQL (key-value DB). Doesn't support a table driven database like relational DBs. Completely serverless, extremely quick to query and overall cheaper.

## DocumentDB
Supports document databases (like MongoDB). Also fully serverless.

## ElastiCache
In-memory datastore, like memcached. Data can be lost because its stored in memory (RAM) and not in storage, but offers high performance and low latency.

## Neptune
Graph DB service, great for high connected data sets like social media networks such as Twitter and Facebook.

# Migration and Transfer
Due to the amount of solutions pre-dating the cloud that can be better managed in the Cloud ecosystem due to its security and cost benefits, AWS offers various ways to migrate legacy systems, usually run on-premises over to the Cloud.

## Database Migration Service (DMS)
Migrate on-prem DBs over to AWS. Supports same-type DB migration (e.g Oracle to Oracle) or different-type DB migration (e.g. Oracle to MySQL).
Big benefits are zero downtime and continuous replication. 

## Server Migration Service (SMS)
Migrate on-prem server(s) over to AWS. Servers will be saved as a new AMI (Amazon Machine Image). These servers can be used as instances in EC2, making for a seamless migration.

## Application Migration Service (AMS)
Converts your existing physical/vms hosting your applications into servers into AWS. Automated Lift-and-Shift, meaning your application is not touched in anyway, only the hardware resources used to be migrated.

Involves installation of replication agents. It performs continuous replication to destination servers in AWS. This replication is encrypted,

You pay for the infrastructure that you require. The application migration is free to use for first 90 days. Windows AND Linux is supported.

## AWS Transfer Family
Transfer files to you from external parties through to AWS Storage. Can be transferred into and from AWS storage like S3 or Elastic File System. Can be transferred either way using SFTP PUT and GET methods 
B2B file transfer using protocols like SFTP (FTP via SSH), AS2 (HTTP/HTTPS), FTPS (FTP via SSL) and FTP. 
Works with 3rd party existing tools like FileZilla, OpenSSH and WinSCP

## Schema Migration Tool
Allows you to migrate from one database schema onto another database platform.
e.g.
- Oracle to Aurora MySQL
- MySQL to RDS MySQL
- SQL Server to Aurora PostreSQL

## Snow Family
A series of various physical hardware devices, with the sole purpose of migrating data over to AWS.
You have 3 types based on the size of data that is needed to migrated:
1. Snowcone (up to 14TB of data), smallest and cheapest family member.
2. Snowball (up to Petabytes of data), also supports transfering FROM cloud into on-prem storage.
3. Snowmobile (a literal semi-trailer truck) used to migrate up to exabytes of data, most expensive option but great for mass migration from on-prem to cloud.

There is also Snowball edge, a hardware device that brings the capabilities of various AWS services to a data center, allowing on-prem remote, disconnected or offline data centers to take advantage of services such as Lambda, EC2.

## DataSync
Allows online data transfer from on-prem to AWS through S3, FSx or EFS. Different from snow family that it requires the source data transfer to also be online or via VPN/Direct Connect.

This service also has the added benefit of syncing data cross-region or across to another AWS account.

Pay per GB pricing model

## Application Discovery Service
A tool that collects data of existing setup. It's collected and sent to AWS via this service and saved in AWS Migration Hub. This data transfer is encrypted. The type of data collected:
- Server inventory
- Config data
- OS versions
- Capicity utilisation
- Network connections.

It requires agents to be installed into your servers/VMs that is responsible for computing the data about your servers. VMWare offers an 'agentless collector' which is VMWare specific that doesn't require an agent to be installed.

The biggest feature is its mostly used to develop a migration plan, onto AWS architecture for you.

## AWS Migration Hub
A central location to manage migration services in AWS. Has information on application and server inventory. This servcers also allows you to logically group servers together for migration
Integrates with existing AWS services like ADS, AMS and DMS.
Also oofers recommendations about modernising apps. Provides a running cost estimate to migrate your services into AWS for EC2 usage.

# Analytics
AWS offers various types of data warehousing, and various services to assist with reporting and data analytics within the cloud.

## Redshift
A fully managed data warehouse service that allows scalable storage of large data, useful for big data. Handles up to exabytes of data. This is the service that most of the following analytics services can easily work with.
Combines multiple sources of data into one place. Online Analytical Processing (OLAP)

Allows for:
- Complex querying and reporting
- Data Lakes integration

### Redshift Serverless
Option that means you don't need to manage infrastructure

## Athena
Allows querying of S3 objects using SQL. Serverless model, pay per query.

## Glue
ETL (Extract, transform and load) service that preps the data for future analysis.

## Kinesis
Realtime analytics for videos and streaming data. A family of services. Can also build custom apps too related to realtime analytics.
Good for:
- Game data
- Financial transcations
- Stock prices
- Social Media feeds
- Location-tracking (Uber)
- IoT sensors

Offers 2 services: Kinesis Data Streams and Kinesis Video Streams

## EMR
Allows analytics of massive, complex, interconnected data like Social Media networks. Works with Hadoop.

## Data Pipeline
Main service that helps move __data__ between compute and storage service. Supports Cloud, On-Prem and hybrid models.

## QuickSight
Useful for creating dashboards and visualising data.

# ML (Machine Learning)
ML is AI driven technology, that learns about environments and accelerates learning beyond a human level capacity.

## Rekognition
Helpful AI tool that helps process images and identify metrics within input images and videos, such as detecting if there is a person, chair or object within a photo or video.

## Comprehend
Natural-language processing service that reads text and finds relationships within input text.

## Polly
AI tool that provides an audio reading of a certain input AI voice, to read out input text in a convincing human conversational way.

## SageMaker
AWS' flagship AI and machine learning service that is the foundation for improving systems and processes via ML.

## Translate
AI tool used to translate text from one language to another.

## Lex
Chatbot AI tool, used to create AI driven chatbots.

# Developer Tools
Amazon's suite of development tools, built for developers by Amazon developers, which integrates seamlessly with AWS.

## Continuous Integration/Continuous Deployment (CI/CD)
CI is about integration or merging small code changes frequently, at least once per day.
CD is about automating the build, test and deployment process. This helps catch bugs early.
Best practice for software development in devops.

In a CI/CD workflow:
Merge > Prepare > Deploy
CodeCommit is the code repository where you manage your code, CodeBuild prepares the code for deployment automatically by compiling and running tests on the code, CodeDeploy deploys the code automatically into an environment like EC2 instance.
CodePipeline manages this entire workflow.

## AWS CloudShell
Browser based shell that accepts AWS CLI commands. Installed into your AWS account environment.

## AWS CLI
Allows you to interact with your AWS services through commands in a command line/terminal. Supports most popular programming languages like JS, Python, Ruby and C++

## Cloud9
Web-based IDE created by Amazon, supports an array of languages. Primarily can be found in AWS Lambda.

## CodeArtifact
Artifacts are approved packages, that includes deployable packages, compiled apps, libraries and documentation.
Artifact repository. Allows you to store software packages, includes open-source software, or in-house packages. e.g. NPM, Python packages in PyPi.
Makes it easy for devs to find software versions needed.
Devs can find approved packages or build their own.

## CodeCommit
AWS' version of GitHub and BitBucket. A code repository management tool.

## CodeBuild
AWS service used to compile, test and build code. Preps for CI/CD (Continuous Integration & Continuous Delivery).

## CodeDeploy
AWS development tool used to deploy code to a test or prod environment, either on-prem or in the cloud. Works with EC2, Fargate, Lambda and on-prem servers.

## CodePipeline
AWS automation tool primarily used for CI/CD (Continuous Integration & Continuous Delivery) pipelines. Integrates closely with CodeCommit, CodeBuild and CodeDeploy.

## X-Ray
Debugging tool for code commited in AWS environment, useful for debugging or finding potential vulnerabilities within code and also seeing how the code interacts with environments and services within the Cloud.

## CodeStar
Collaborative engine for development, allows AWS accounts to collaborate within an environment, and _also has a dashboard for issue tracking_ (similar to Jira).

# Deployment and Infrastructure Management
Amazing tools that enables IaC (Infrastructure as Code) and various other ways to standup or provision infrastructure within the Cloud.

## CloudFormation
Enables IaC, which allows you to formulate infrastructure as written code, all the way from creating an S3 bucket, to setting up an EC2 instance or a Lambda Function. This can all be done programmatically, which is awesome for tracking changes within the infrastructure using tools such as CodeCommit, GitHub or GitLab.

This also enables building infrastructures from templates, which means you can reproduce how to standup well-known infrastructures (like a static website) all within a code, and send it off to other developers, AWS accounts or regions. 

Supports code written in JSON or YAML, and also has a Designer interface within the browser to help visualise the infrastructure.

## Elastic Beanstalk
A compute service used to deploy web apps or services to AWS. Handles all of the deployment so you don't have to think about provisioning hardware or resources. Also provides a CloudWatch health dashboard of any apps you deploy through Elastic Beanstalk.

## OpsWorks
Integrates with Chef or Puppet which are tools used to automate configuration of servers.

# Messaging and Integration
Queues are a crucial concept when handling large amounts of processing tasks or data via compute. It's the main driver that supports loosely coupled modules within an application, allowing tasks to be queued up and processed in a First-In-First-Out (FIFO) fashion.

## Simple Queue Service
Messaging queue service that supports loosely coupled microservices to process data or tasks FIFO. Messages within the SQS queue are processed asynchronously. Messages are Pull-Based, so the queue does not send messages to consumers. It instead waits for the consumer to request a message from the queue.
SQS queues are Standard by default. They guarantee that a msg is delivered AT LEAST once. Is not a FIFO queue, so some messages can go out of order. Best effort ordering.
FIFO queues follow a strict order, and no duplicates occur.

### Short Polling
Returns a response immediately even if queue is empty.
Note, that empty responses are still billed.

### Long Polling
Queue doesn't respond until messages arrive, or times out. Long polling is more cost effective as a result.

## Simple Notification Service
A service that sends text messages or emails from AWS. This can be triggered by Lambda, CloudWatch events to notify users important info, ranging from reporting slow processing times of an application or if the AWS account is about to surpass a budget quota.

## Simple Email Service
Similar to SNS, but only sends emails that are written and designed in HTML, great for marketing material or fancy looking professional emails.

# Auditing, Monitoring and Logging
These services are crucial in allowing users within AWS see what is generally going on with the services that are deployed within the Cloud. Ranging from looking deep into application logs, seeing resource usage or just seeing who logged in at what time, these services give users and administrators full visibility so they can react or prepare accordingly.

## CloudWatch
Service that tracks and monitors resource metrics, events and logs used by deployed services within AWS. This service will let you see what applications within EC2 or Lambda are logging, and help troubleshoot anomalies or issues if anything is going wrong. 

A huge benefit that CloudWatch provide is alarms, which you can set up metric thresholds, and if they are surpassed or met, then it can trigger an event such as an SNS message that emails a set of users.

This service also allow you to visualise metrics and logs.

## CloudTrail
This service will give you a full audit of any user or service activity within the AWS ecosystem. This allows you to narrow down who or what was responsible for certain events, and ensures that any issues that arise as a result of a user can be found.
The following metrics are what you can track via CloudTrail:
- Username
- Event time
- Name
- IP address
- Access Key
- Region
- Error code.

## EventBridge
All about **event-driven architecture**. An event is a change in state, which can be triggered by AWS services like EC2, CloudWatch and CloudTrail.
You setup rules and targets and give it an action to another AWS service whenever a state change (trigger) occurs.
You can also use this service to handle scheduled events, like Jenkins, using hourly schedules or cron time rules.

## Step Functions
Allow you to set breakpoint functions for a distributed workflow. Allows you to visualise your logic, and build and run serverless applications (like lambda funcs) as a series of steps.
The output of one step maybe the input of the next.
This also manages error handling, in case the logical workflow is broken in anyway, like a file upload process getting interrupted.

# Additional services
Some additional cool services that AWS offers that may be covered in the exam.

## Amazon Workspaces
Allows you to boot up a virtual desktop within the cloud, great for allowing people to work from home and access the cloud ecosystem with a nice familiar desktop interface. Supports Windows & Linux.

## Amazon Connect
Allows you to build a contact center or help-desk in the cloud (not to be confused with AWS support).