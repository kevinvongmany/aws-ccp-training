# Security and Compliance
25% of the total score in exam

 - Shared Responsibility
 - IAM - management service, also provides reports for password status and MFA devices for account.
 - WAF (Firewall)
 - Shield (DDoS prevention)
 - Macie (discover and protect sensitive data like passports, ID and credit card)

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
    - Scale horizontally (e.g. multiple containers/instances) for availability
    - Stop guessing capacity (let is grow)
    - Manage change via automation
    - Test procudures of recovery (data and systems)
    e.g. RDS / EC2, S3
 - Performance Efficiency
    - Serverless
    - Multi region and AZs
    - Delegate tasks to AWS, focus on code
    - Experiment with managed services to increase efficiency
    e.g. Lambda
 - Cost Optimisation
    - Pay on demand/as you go for resources that applications requires
    - Optimise cost efficiency
    e.g. S3 Intelligent Tiering
 - Sustainability
    - Environmental impacts, like energy consumption and efficiency
    - Use managed services that are already efficient
    - Reduce downstream impact
    e.g. EC2 Auto Scaling, scale as you use it, good for costs and energy use.

## Config
Assess, auditing and evaluation config of resources of managed services. Good for change tracking

### Use case
Allows system level config changes for EC2 instances. 

## Guard Duty
Uses ML for threat detection and unauthorised behavior in AWS account
Built in for EC2, S3 & IAM
Reviews VPC, DNS and Cloudtrail logs
Can automatically take remediation steps

### Use case
Will detect API requests that are suspicious or unusual.

## Inspector
Agent installed in EC2 instance, but now also lambda and ECR containers. Also CI/CD.

Reports vulnerabilities
Checks access from internet.

### Use case
Can ID unintended network access to EC2 instance. Categorises by severity level.

## Artifact
Ondemand security and compliance reports for 3rd party
SOC (Service Organisation Controls) and PCI (Payment Card Industry) reports

### Use case
Need AWS certification for ISO 9### compliance

## Cognito
Authentication & authorisation for web applications and mobile apps.
Helps manage users
Assist with users with sign up and sign in, don't have to use OAuth or some other authentication method

### Use case
Need a social media login (like google or facebook) to log in.

# Data Encryption
__Data in flight__ is data that moves from one location to another. VPC, internet data.
__Data at rest__ is inactive, like S3 or DB (DynamoDB)

Encryption keys will scramble data in a certain way that uses a corresponding decpryption key that the end target needs to unscramble the data.

## KMS (Key Management Service)
Generates and stores encryption keys
AWS manages encryption keys
Decryption keys are given to approved apps, roles or targets by AWS.
Auto in CloudTrail, S3 Glacier and Storage Gateway

### Use case
Create encryption EBS volumes. You can specify KMS customer master key

## CloudHSM
Hardware security module
Dedicated hardware for security
Generate and manage own encryption keys
AWS does not have acces to keys
This is like RSA

May be needed to meet compliance

## Secrets Manager
Manage and retrieve secrets
Securely store secrets like API key, passwords, etc.
Can automatically ROTATE!
Encrypt secrets at rest
Integrates with RDS, Redshift and DocumentsDB
Code doesn't need to update rotated keys if API is used correctly.
Avoids hardcoding secrets

