
# Day 01

- IAM
  - Owner's account AKA The root user
  - MFA
  - Policy (AWS Managed, Customer managed, Inline)
  - Users
  - Groups
  - Permissions boundary
  - IAM Roles (to be revisited)
- KMS
- CloudHSM
- WAF
- Shield
- Resource Access Manager

**Networking:**

- VPC
  - Subnets (Public, Private)
  - VPC FlowLogs
  - Route Tables
  - Gateways
    - Internet Gateway
    - NAT Gateway, NAT Instance
    - VPC Peering
    - Transit Gateway
    - VPC Endpoints
    - Private Link
  - ENI
  - Elastic IP
  - NACL (Stateless)
  - Security Group (Stateful)
  - VPN
  - Direct Connect
- Route 53
  - Routing Policies
- CloudFront
- API gateway
- Global Accelerator

**Compute:**

- EC2
- Creation Modification, Deletion
- Load Balancing
  - ALB
  - NLB
- Auto Scaling
  - Launch Configuration
  - Auto Scaling Group
  - Scaling Policies
    - Target tracking policy
    - Simple scaling policy
    - Step scaling
    - Scheduled scaling policy
- EC2 pricing model
  - On-Demand
  - Reserved
    - Standard Reserved Instances
    - Scheduled Reserved Instances
  - Spot Instances
  - Savings Plan
  - Dedicated Host
- Elastic Beanstalk
- HPC
- Placement Group

# Day 02

**Storage:**

- Block Storage
  - Instance Store
  - EBS
    - EBS Snapshot
- Object Storage
- S3
  - Versioning
  - Static website hosting
  - Presigned url
  - ACL
  - Bucket policy (avoiding accidental deletion)
  - S3 Tiers
  - Lifecycle Rules
  - Encryption
  - Transfer Acceleration
  - Replication
  - Object lock
  - Server access logging
- Consistency Model
- Glacier
- File Storage
  - EFS
  - FSx
  - FSx for Lustre
- Storage Gateway
- DataSync
- Snow Family
  - Snowball, Snowball Edge
  - Snowmobile
- HPC relevant storage

**Application Integration:**

- SQS, features
- SNS

**Management & Governance:**

- Organizations
  - Consolidated Billing
  - Service Control Policies
- CloudWatch
- CloudTrail
- Trusted Advisor
- CloudFormation
- OpsWorks

# Day 03

**Database:**

- RDS
  - Types, Creation, Modification and Deletion
  - Read Replica
  - Aurora global database
- DynamoDB
  - DynamoDB Globle Tables
  - DAX
- ElastiCache
  - Redis vs Memcached
- Redshift

**Compute:**

- ECS
- Fargate
- Lambda

**Analytics:**

- EMR
- Kinesis
  - Data Firehose
  - Data Streams
  - Data Analytics

**Others:**

- Stateless Application
- Decoupling
- Athena
- Quicksight
