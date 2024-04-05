# Pricing, Billing and Governance
Represents 12% of the certification exam.

# AWS Pricing

## Pricing
3 drivers:
 - Compute: Hourly from launch to termination, unless reserved
 - Storage: Data stored in the cloud
 - Outbound data transfer: Data in-flight moving between systems (usually no charge if within the same region)

 Ready the whitepaper.

Offer types:
 - 12 months free. After you sign up, you get 12 months free usage
 - Always free. These offers never expire and available to all AWS customers
 - Trials: Short-term. Starts from when you activate. Then you pay as you go after trial ends.

## EC2 Pricing
 - On-Demand (pay as you go) - for unpredictable computing that always need to complete
 - Savings Plan (pay compute per hour) - 1 or 3 year options. Can change compute services, OS or instance types at anytime. No capacity reservation.
 - Reserved Instances - for predictable workloads, upfront for 1 or 3 year options
 - Spot Instances (CHEAPEST) - Bid for unused compute/resources, great if it compute can be done later on
 - Dedicated Host (physical server, usually for compliance)

## Lambda
 - Number of requests
 - Code execution time (seconds)
 - 1 million requests per month

## S3 Pricing
 - You pay for storage used
 - Storage classes (Standard, IA, Glacier / Glacier Deep Archive)
 - Data transfer
 - Request and data retrieval

## RDS (Relational Database Service)
 - Running clock hours (launch til termination)
 - Type of database (e.g. memory class, type, size)
 - Storage
 - Purchase type (ondemand or reserve?)
 - Database count (how many?)
 - API requests
 - Deployment type (single AZ or multi AZ?)
 - Data transfer (inbound free, outbound is charged)

## TCO
Total cost of ownership
An estimation of direct and indirect cost of using AWS services
How much will it cost to migrate?
How can I reduce TCO using AWS?
Will be on the exam!!

## Application Discovery Service
Helps plan migration projects, estiamtes TCO and can migrate other services to migrate servers

 - Minimise CAPEX by using Cloud, and efficient managed services
 - Use Reserved Instances
 - Right size your provisioned resources, based on what is NEEDED (on-demand)

## Pricing Calculator
Can get an estimate for services you plan or may want to use and get a document of estimated costs
Can get quick estimate or advance estimate, which requires detailed estimate metrics.
You can use the calculator to compare pricing strategies, and payment option to get the savings or costs you want to generate.
You can also compare costs per region, which is very handy.

You get upfront costs and/or monthly cost estimates.

## AWS Price List API
Can query price of AWS services via API. Queried via HTML or JSON. Can see when services change.

# Billing Services
A lot of tools that track ongoing spend, via dashboard

## Budgets
Alerts you when your costs, usage or reservation exceed your defined budget using thresholds.
Improves planning and cost control

 - Cost Budgets
 - Usage Budgets
 - Reservation Budgets

Monitor free tier usage, and set up alert notification if you're about to exceed free tier usage.

## Cost & Usage Report
Here is where you go to get a report for retroactive usage when billed by a big amount.
Can get billing info down to the instance, at an hourly and monthly level.
Highly granular data
Can be downloaded via Amazon S3

## AWS Cost Explorer
Visualise (graphs) costs over time
View past year
Forecast 3 months

You can analyse EC2 usage, for weekly, monthly or 6 month usage.

## Cost Allocation Tags
Tags allow you to label resources using a key/value pair
Allow tracking of costs too through tags

# Governance Services
Maintain control over:
 - Costs
 - Compliance
 - Security

## Organizations
Centrally manage multiple AWS accounts into one umbrella, really good for ORGANISATIONS
Single payment for all accounts, consolidated billing (big savings overall)
Automate account creation
Centrally manage access policies across groups.

Organisations are entity that consolidates multiple accounts
Root account is called Master Payer

SCP (Service Control Policy)
Policies that all sub users must follow

Can compartmentalise into multiple groups/org units
Think workgroups

### Benefits
 - Consolidated billing
 - Cost savings
 - Account governance; automated way to create accounts and manage security and compliance policies

## Control Tower
Ensures accounts comply with company-wide policies
Works directly with AWS Organizations
Has a dashboard

### Use case
Prevent users from making deadly changes to S3 buckets, and comply with security policies

## Systems Manager
Gives visiblity over AWS resources
Automate operational tasks
Group resources and apply actions/commands
Run patches and commands on multiple RDS/EC2 instances

### Use case
Deploy OS and software patches. Imagine there's a windows vulnerability that HAS to be patched. You can do it at scale to all your instances on a schedule.

## Trusted Advisor
Real-time guidance for resource provision, as per AWS best practices while using managed services.
Checks accounts and can make recommendations
See service limits

### Popular recommendations that it can do
 - Unrestricted access on certain ports for EC2 instances (free)
 - Public access to S3 buckets (also free)
 - Checks MFA on root account (free)
 - IAM password policy (requires enterprise/business plan)
 - RDS public snapshots (free)
 - Checks service usage (paid)
 - Exposed access keys (paid)
 - Checks CDN optimisation on CloudFront (paid)

## License Manager
Helps manage software license, on-prem and AWS.
Integrates already for MS, Oracle and SAP.

## Certificate Manager
SSL/TLS certificate provider for https. Also handles renewals!
Integrates with AWS managed services like ELB, CloudFront, API Gateway, Route 53 (I'm guessing) and more.

# Management Services
Several services that help migrate and build stuff from on-prem to the cloud if your team lacks the expertise to use AWS themselves, paid service.

## Managed Services
Helps operate AWS infrastructure efficiently.
 - Augments internal staff (training/assistance?)
 - Ongoing management
 - Reduce operation risk and overhead

### Services
 - patch management
 - monitoring
 - reporting
 - logging
 - cost optimisation
 - more
Develop application-specific health monitoring using CloudWatch.

## Professional Services
Helps enterprise customers move over to the cloud ecosystem
 - Propose
 - Architect
 - Implement

## APN (AWS Partner Network)
Global community. Approved partners, solutions and consulting services with rich AWS experience.

## Marketplace
Solutions to buy or sell prebuilt solutions within AWS. License or purchase options available.
Some solutions offer free trials

## Personal Health Dashboard
Troubleshooting and feedback for your own AWS environment

# Support Plans
There are various support cases that have various options for the following:
 - Account and billing
 - Service limit increases
 - Technical support (not available on free/basic plan)

AWS Support does not allow cases for code dev, bug fixes/debugging or performing sysadmin tasks.

## Basic
Free
Access to account & billing and service limit increases
24/7 email customer service
Discussion forums

## Developer
$29USD/month
Testing and Development
Access to account and billing, service limit increases and tech support cases.
You have 1 primary contact via email during business hours and can open unlimited cases.
<24 hours general guidance response times
<12 hours system impaired issues

## Business
$100USD/month
Production workloads
Same access to Developer
Unlimited contacts and full set of Trusted Advisor checks
Can contact via email, phone or chat 24/7
<4 hours production system impaired
<1 hour prod system down

## Enterprise
$15,000/month
Mission critical production workloads
Same as business
Have access to Technical Account Manager (TAM) (level 3+ support)
Concierge Support Team (level 1-2 support)
Infrastructure Event Management (operational support)
<15 minutes business-critical system down response time