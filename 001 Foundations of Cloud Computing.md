# Foundations

In short, a cloud is someone else's computer that you have to connect to via the internet.
Realistically there are servers, inside data centers that have a LOT of servers

## What is cloud computing?
 - Compute: EC2 (server instances), Lambda (serverless)
 - Network: VPC, Direct Connect, Route 53, CloudFront
 - Storage: S3, EBS
 - Analytics: Athena, Redshift
 - Development: Cloud9, CodeCommit, Codebuild
 - Security: IAM, Macie
 - Databases: RDS, DocumentDB, DynamoDB

Read the Overview of Amazon Web Services whitepaper before exam.

## Virtual Machines
Divides hardware resources (like CPU, memory and storage) on a physical server into smaller units, called VMs or virtual machines.
This is the heart of cloud computing

## Usage
Usage of Cloud is on demand & pay as you go, kind of like utility companies like water or energy.

# Advantages of Cloud Computing
1. Go global in minutes
2. Stop spending money running and maintaing data centers
3. Benefit from massive economies of scale
4. Agility and Speed
5. Stop guessing capacity
6. Trade CapEx (Capital Expense) for OpEx/variable expense (Operation Expense)

## Benefits
1. High availability (your app won't go down, due to how its hosted on multiple AZs)
2. Elasticity (scales usage towards your demand; e.g. small API requests will use less resources)
3. Agility (the managed services will help you get your solution up faster)
4. Durability (data won't be lost)

## CapEx vs OpEx
Capital Expenditures are upfront costs. Like paying for a physical server.
Operating Expenses are funds spent on day-to-day ops, like staff and hosting.

# Cloud computing models
1. Infrastructure as a Service (IaaS): Think web hosting or EC2.
2. Software as a Service (SaaS): Think Scala/Broadsign or gmail.
3. Platform as a Service (Paas): think Jira/GitHub/GitLab.

## Private Cloud
Also known as on-premisis.
Internal data center, usually physical hardware you have direct or network access to from your office or organisation.
No advantages of cloud computing

## Public Cloud
AWS/Azure/GCP

## Hybrid Cloud
A mix of AWS and on-prem. Think of servers hosted in a locked down network, but the application logs to CloudWatch, runs a Lambda function or hosts DynamoDB.
Usually for sensitive data or for compliance.

# AWS Global Infrastructure

## Regions
Various geographic points around the world that hosts various AZs. e.g. ap-southeast-2 (Sydney). Usually have 3-6 AZs.

## Availability Zones (AZs)
Physical group of data centers within a few KMs of each other. All connected, and hidden away from the world but have different power grides. Cannot be accessed by public, only AWS employees. This is how AWS can serve data/content/services if one data centre goes down due to network or power issues.

## Edge Locations
Node locations, helps deliver content globally across regions faster using caching and CloudFront. Enables low latency.

# AWS Account

## AWS Management Console
Webpage where you can manage and view the services on a browser. Can change regions, view and use services, and manage account and billing here.

## Root User
The ultimate owner of the AWS account, has the highest privileges that can delete account, change emails and manage billing. This should not be used for day-to-day. 
Should have MFA (multi factor authentication) setup and enabled.