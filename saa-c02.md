
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
- [WAF](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)
- [Shield](https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html)
- Resource Access Manager

**Networking:**

- [VPC](https://aws.amazon.com/vpc/)
  - [Subnets](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html#vpc-subnet-basics) (Public, Private)
  - VPC FlowLogs
  - [RouteTables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)
  - Gateways
    - Internet Gateway
    - [NAT Gateway](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html), [NAT Instances](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_NAT_Instance.html); [Comparison](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-comparison.html)
    - [VPC Peering](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html)
    - [Transit Gateway](https://aws.amazon.com/transit-gateway/)
    - [VPC Endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html) (to be revisited)
    - Private Link
  - ENI
  - [Elastic IP](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)
  - [Network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html) (Stateless)
  - [Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) (Stateful)
  - [Comparison of security groups and network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html)
  - [Site-to-Site VPN](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html)
  - [Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html)
- Route 53
  - Routing Policies
- [CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)
- API gateway
- Global Accelerator

**Compute:**

- [EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
- Creation Modification, Deletion
- [Userdata, Metadata (Comparison)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html)
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
- [EC2 purchasing Options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html), [Tenancy](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-instance.html)
  - On-Demand
  - Reserved
    - Standard Reserved Instances
    - Scheduled Reserved Instances
  - Spot Instances
  - Savings Plan
  - Dedicated Host
- [Elastic Beanstalk](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html)
- HPC
- Placement Group

# Day 02

**Storage:**

- Block Storage
  - [Instance Stored Volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)
  - [EBS, EBS Volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)
    - Types
    - Creation, Modification, Deletion, Movement
    - Snapshot
- Object Storage
- [S3](https://aws.amazon.com/s3/)
  - [Pricing](https://aws.amazon.com/s3/pricing/)
  - [Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html)
  - [Static Website Hosting](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)
  - [Pre-signed url](https://docs.aws.amazon.com/AmazonS3/latest/dev/ShareObjectPreSignedURL.html)
  - [ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html)
  - [Bucket Policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-iam-policies.html) (avoiding accidental deletion)
  - [S3 Storage Classes](https://aws.amazon.com/s3/storage-classes/)
  - [Object lifecycle management](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html)
  - Encryption
  - [Transfer Acceleration](https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html)
  - [Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html)
  - Object lock
  - Server access logging
- Consistency Model
- [Glacier](https://aws.amazon.com/glacier/)
- File Storage
  - EFS
  - FSx
  - FSx for Lustre
- [Storage Gateway](https://aws.amazon.com/storagegateway/)
- DataSync
- Snow Family
  - [Snowball](https://docs.aws.amazon.com/snowball/latest/ug/whatissnowball.html)
  - [Snowmobile](https://aws.amazon.com/snowmobile/)
- HPC relevant storage

**Application Integration:**

- [SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)
- [SNS](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)

**Management & Governance:**

- Organizations
  - Consolidated Billing
  - Service Control Policies
- CloudWatch
- CloudTrail
- Trusted Advisor
- [CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)
- [OpsWorks](https://docs.aws.amazon.com/opsworks/latest/userguide/welcome.html)

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
