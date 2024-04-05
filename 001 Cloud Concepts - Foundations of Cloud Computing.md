# Foundations

This section will represent 24% of the exams

In short, a cloud is someone else's computer that you have to connect to via the internet.
Realistically there are servers, inside data centers that have a LOT of servers

## What is cloud computing?
The below are the various types of categories that AWS services will fall under
 - Compute: EC2 (server instances), Lambda (serverless)
 - Network: VPC, Direct Connect, Route 53, CloudFront
 - Storage: S3, EBS
 - Analytics: Athena, Redshift
 - Development, Messaging & Deployment: Cloud9, CodeCommit, Codebuild
 - Security, Compliance and Governance: IAM, Macie
 - Databases: RDS, DocumentDB, DynamoDB
 - Pricing, Billing and Support: AWS Cost Explorer, AWS Budgets, AWS Partner Network
 - Migration and Transfer: AWS Database Migration Service, AWS Server Migration Service
 - Artificial Intelligence and Machine Learning: SageMaker, Rekognition
 - Auditing, Monitoring and Logging: AWS CloudWatch, AWS CloudTrail

## Preparing for the exam
Read the Overview of Amazon Web Services whitepaper before exam. Read the whitepaper. Understand the different categories and what service falls under which category.

## Virtual Machines
Divides hardware resources (like CPU, memory and storage) on a physical server into smaller units, called VMs or virtual machines.
This is the heart of cloud computing

## Usage
Usage of Cloud is on demand & pay as you go, kind of like utility companies like water or energy.

# Advantages of Cloud Computing
1. Go global in minutes
2. Stop spending money running and maintaing data centers (No data center spend)
3. Benefit from massive economies of scale
4. Agility and Speed
5. Stop guessing capacity
6. Trade CapEx (Capital Expense) for variable expense

## Benefits
1. High availability (your app won't go down, due to how its hosted on multiple AZs)
2. Elasticity (scales usage towards your demand; e.g. small API requests will use less resources)
3. Agility (the managed services will help you get your solution up faster)
4. Durability (long term data protection, data won't be lost)

## CapEx vs OpEx
Capital Expenditures are upfront costs. Like paying for a physical server or software.
Operating Expenses are funds spent on day-to-day ops, like staff, hosting and R&D.

# Cloud computing models
1. Infrastructure as a Service (IaaS): Think web hosting or EC2. Monthly subscription hosting a webpage
2. Software as a Service (SaaS): Think Scala/Broadsign or gmail.
3. Platform as a Service (Paas): Think Jira/GitHub/GitLab.

## Private Cloud
Also known as on-premises.
Internal data center, usually physical hardware you have direct or network access to from your office or organisation.
No advantages of cloud computing

## Public Cloud
AWS/Azure/GCP
No hardware responsibility
All the advantages of cloud

## Hybrid Cloud
A mix of AWS and on-prem, with safe connections. Think of servers hosted in a locked down network, but the application logs to CloudWatch, runs a Lambda function or hosts DynamoDB.
Usually for sensitive data or for compliance. 

## Preparing for the exam
- Understand the 6 Advantages of the cloud
- Learn cloud benefits and the terminology
- Know the computing models (IaaS, SaaS, PaaS)
- Know the deployment models (Private cloud, Public cloud and Hybrid)
- Know hybrid is supported via Direct Connect, another service in AWS

# AWS Global Infrastructure

## Regions
Various physical geographic points around the world that hosts various AZs. e.g. ap-southeast-2 (Sydney). Usually have 3-6 AZs. Fully isolated and independent and not service specific. Means if one region goes down, others will still remain, but deployed solutions will not be replicated across regions automatically.

## Availability Zones (AZs)
Physical group of data centers within a few KMs of each other. All connected, and hidden away from the world but have different power grids. Cannot be accessed by public, only AWS employees. This is how AWS can serve data/content/services if one data centre goes down due to network or power issues. Each are connected with low latency zones
Highly fault tolerant and makes data, applications or services highly available.

## Local Zones (New in C-02)
Extensions of regions that host AWS services like compute, storage, DBs and other services closer to end-users. Allows for low (ms) time latency. Good for real-time gaming.

## Edge Locations
Node locations, helps deliver content globally across regions faster using caching and CloudFront. Enables low latency.

## Preparing for the exam
Understand that regions are global, and made up for 2 or more AZs.
AZs is made up of multiple data centers
Multi AZ deployments provide high availability (the only way it goes down is if the whole region goes offline)
Edge locations ensures low latency by placing content closer to users. There are more edge locations then there are regions.
Local Zones are an extension of Regions, enabling low latency requirements like real-time gaming

# Cloud Adoption Framework

## Perspectives and Foundational Capabilities

### Security
Covers:
 - Security: Governance, Assurance and Application security
 - Protection: Infrastructure and Data
 - Management: Identity & access vulnerability
 - Incident Response
 - Threat Detection

### Business
- Management: Strategy, Portfolio, Innovation and Product
- Data: Monetization and Science
- Business Insight

### Platform:
- Architecture and Engineering: Platform and Data
- CI/CD (Continuous Integration/Continuous Delivery)
- Modern Application Development
- Provisioning and Orchestration

### Operations
- Management:
    - Event (AIOps)
    - Incident and Problem
    - Change and Release
    - Performance and Capacity
    - Configuration
    - Patch
    - Availability and Continuity
    - Application
- Observability

### Governance
- Management:
    - Program and Project Benefits
    - Risk
    - Cloud Financial
    - Application Portfolio
- Data: Governance and Curation

### People
- Transformation: Leadership and Workforce
- Organization: Design and Alignment
- Cloud Fluency
- Change Acceleration
- Culture Evolution

## Cloud Transformation Domains

### Technology
Migrate and Modernize

### Process
Digitize, automate and optimize

### Organization
Reimagine orchestration

### Product
Reimagine your business model

## Cloud Transformation Journey Phases

### Envision
Benefits to business outcomes

### Align
Gaps across perspectives

### Launch
Deliver initiatives with value

### Scaling
Expand sustainable initiatives

## Well Architectured Framework
 - Operational Excellence
    - Producing application that support production workloads
    - Plan and anticipate worst-case scenarios (failure)
    - Deploy small changes that are reversible
    - Script operations as code (IAC)
    - Learn from failure and refine
    e.g. CodeCommit, CloudFormation
 - Security
    - Assign least privileged access
    - Track who and what in AWS
    - Security at all app layers
    - Automate security tasks
    - Encryption
    e.g CloudTrail
 - Reliability
    - Auto recover from failure
    - Disaster recovery
    - Scale horizontally (e.g. multiple containers/instances) for availability
    - Stop guessing capacity (let is grow)
    - Manage change via automation
    - Test procedures of recovery (data and systems)
    e.g. RDS / EC2, S3
 - Performance Efficiency
    - Serverless
    - Maximising resource usage
    - Trade-offs
    - Multi region and AZs
    - Delegate tasks to AWS, focus on code
    - Experiment with managed services to increase efficiency
    e.g. Lambda
 - Cost Optimisation
    - Pay on demand/as you go for resources that applications requires
    - Optimise cost efficiency
    - Right-sizing
    - Implementing lifecycles
    e.g. S3 Intelligent Tiering
 - Sustainability
    - Environmental impacts, like energy consumption and efficiency
    - Use managed services that are already efficient
    - Reduce downstream impact
    - Region selection
    e.g. EC2 Auto Scaling, scale as you use it, good for costs and maintaining required energy use.

### General Design Principles
- Stop guessing capacity; Auto Scaling
- Test systems at production scale
- Consider evolutionary architectures; adopt new tech and services when needed
- Automate with architectural experimentation in mind
- Drive architectures using data
- Improve through game days

## Exam tips
Understand the CAF perspectives and journey phases as a whole (Envision > Align > Launch > Scale > Repeat)
Understand the well-architected framework pillars.

# AWS Account

## AWS Management Console
Webpage where you can manage and view the services on a browser. Can change regions, view and use services, and manage account and billing here.

## Root User
The ultimate owner of the AWS account, has the highest privileges that can delete account, change emails and manage billing. This should not be used for day-to-day. 
Should have MFA (multi factor authentication) setup and enabled.

## CLI
AWS command-line interface. Provides a terminal to access AWS services programmatically. CLI can also be accessed via Application Code and SDKs
