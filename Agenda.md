# AWS-SAA-C02

## Get Started

- Basics of Cloud Computing 
- [The NIST definition of cloud computing](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-145.pdf)
- [Introduction and History of AWS](https://techcrunch.com/2016/07/02/andy-jassys-brief-history-of-the-genesis-of-aws/)
- [Certification Roadmap](https://aws.amazon.com/certification/)
- [AWS Certified Solutions Architect – Associate](https://aws.amazon.com/certification/certified-solutions-architect-associate/)
- [Free tier account creation](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/) and [coverage](https://aws.amazon.com/free/)
- [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
- [Regions, Availability Zones, Local Zones](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html) and [Edge Network Locations](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/#AWS_Edge_Network_Locations)
- Exploring the AWS Management Console
- [Setting up free tier billing alerts](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/tracking-free-tier-usage.html)
- [Shared Responsibility Model](https://aws.amazon.com/compliance/shared-responsibility-model/) (to be revisited)
- [AWS Documentation](https://docs.aws.amazon.com/index.html)
- [AWS Slideshare Channel](https://www.slideshare.net/AmazonWebServices)
- [AWS Ramp-Up Guide: Architect](https://d1.awsstatic.com/training-and-certification/ramp-up_guides/Ramp-Up_Guide_Architect.pdf)

## Day 01

### Security

- [IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
  - [The AWS Account Root User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html) and [only when to use it](https://docs.aws.amazon.com/general/latest/gr/aws_tasks-that-require-root.html)
  - [MFA](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html#enable-virt-mfa-for-root)
  - [Policies and Permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html)
  - [Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_identity-management.html)
  - [Groups](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups.html)
  - [Permissions boundary](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html)
  - [IAM Roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) (to be revisited)
  - [Common Tasks](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_quick-links-common-tasks.html)
- [KMS](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)
- [CloudHSM](https://docs.aws.amazon.com/cloudhsm/latest/userguide/introduction.html)
- [WAF](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html)
- [Shield](https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html)
- [Resource Access Manager](https://docs.aws.amazon.com/ram/latest/userguide/what-is.html)

### Networking [Watch this video](https://www.youtube.com/watch?v=hiKPPy584Mg)

- [VPC](https://aws.amazon.com/vpc/), 
  - [Subnets](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html#vpc-subnet-basics) (Public, Private)
  - [VPC FlowLogs](https://docs.aws.amazon.com/vpc/latest/userguide/flow-logs.html)
  - [RouteTables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)
  - Gateways
    - [Internet Gateway](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html)
    - [NAT Gateway](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html), [NAT Instances](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_NAT_Instance.html); [Comparison](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-comparison.html)
    - [VPC Peering](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html)
    - [Transit Gateway](https://aws.amazon.com/transit-gateway/)
    - [VPC Endpoints](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html) (to be revisited)
    - [Private Link](https://docs.aws.amazon.com/vpc/latest/userguide/endpoint-service.html)
  - [ENI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-eni.html), [ENA](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/enhanced-networking-ena.html), [EFA](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/efa.html) (Comparision)
  - [Elastic IP](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html)
  - [Network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html) (Stateless)
  - [Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) (Stateful)
  - [Comparison of security groups and network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html)
  - [Site-to-Site VPN](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html)
  - [Direct Connect](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html)
  - [Very Good Whitepaper](https://d1.awsstatic.com/whitepapers/building-a-scalable-and-secure-multi-vpc-aws-network-infrastructure.pdf)
- [Route 53](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html)
  - [Routing Policies](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html)
- [CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)
- [API gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)


### Compute

- [EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
- Creation Modification, Deletion
- [Userdata, Metadata (Comparison)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html)
- [Elastic Load Balancing](https://docs.aws.amazon.com/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)
  - [ALB](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)
  - [NLB](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html)
- [Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/scaling_plan.html)
  - [Launch Configuration](https://docs.aws.amazon.com/autoscaling/ec2/userguide/LaunchConfiguration.html)
  - [Auto Scaling Group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html)
  - Scaling Policies
    - [Target tracking policy](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-target-tracking.html)
    - [Simple, Step scaling policy](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html)
    - [Scheduled scaling policy](https://docs.aws.amazon.com/autoscaling/ec2/userguide/schedule_time.html)
    - [Scaling Based on SQS](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-using-sqs-queue.html)
  - [Lifecycle Hooks](https://docs.aws.amazon.com/autoscaling/ec2/userguide/lifecycle-hooks.html)
- [EC2 purchasing Options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html), [Tenancy](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-instance.html)
- [Elastic Beanstalk](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html)
- HPC
- [Placement Group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)

## Day 02

### Storage

- Block Storage
  - [Instance Stored Volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)
  - [EBS, EBS Volumes](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html)
    - Types
    - Creation, Modification, Deletion, Movement
    - [Snapshot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html)
- Object Storage
- [S3](https://aws.amazon.com/s3/)
  - [Pricing](https://aws.amazon.com/s3/pricing/)
  - [Versioning](https://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html)
  - [Static Website Hosting](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)
  - [Pre-signed url](https://docs.aws.amazon.com/AmazonS3/latest/dev/ShareObjectPreSignedURL.html)
  - [ACL](https://docs.aws.amazon.com/AmazonS3/latest/dev/S3_ACLs_UsingACLs.html)
  - [Bucket Policy](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-iam-policies.html) 
  - [S3 Storage Classes](https://aws.amazon.com/s3/storage-classes/)
  - [Object lifecycle management](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html)
  - [Encryption](https://docs.aws.amazon.com/AmazonS3/latest/dev/bucket-encryption.html)
  - [Transfer Acceleration](https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html)
  - [Replication](https://docs.aws.amazon.com/AmazonS3/latest/dev/replication.html)
  - [Object lock](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lock.html)
  - [Server access logging](https://docs.aws.amazon.com/AmazonS3/latest/dev/ServerLogs.html)
  - [Avoiding accidental deletion](https://aws.amazon.com/premiumsupport/knowledge-center/s3-audit-deleted-missing-objects/)
- [Data Consistency Model](https://docs.aws.amazon.com/AmazonS3/latest/dev/Introduction.html#ConsistencyModel)
- [Glacier](https://aws.amazon.com/glacier/)
- File Storage
  - [EFS](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)
  - [FSx for Windows File Server](https://docs.aws.amazon.com/fsx/latest/WindowsGuide/what-is.html)
  - [FSx for Lustre](https://docs.aws.amazon.com/fsx/latest/LustreGuide/what-is.html)
- [Storage Gateway](https://aws.amazon.com/storagegateway/)
- [DataSync](https://docs.aws.amazon.com/datasync/latest/userguide/what-is-datasync.html)
- [Snow Family](https://aws.amazon.com/snow/)
  - [Snowball](https://docs.aws.amazon.com/snowball/latest/ug/whatissnowball.html)
  - [Snowmobile](https://aws.amazon.com/snowmobile/)
  - [Snowcone](https://docs.aws.amazon.com/snowball/latest/snowcone-guide/snowcone-what-is-snowcone.html)
- [HPC relevant storage](https://d1.awsstatic.com/whitepapers/AWS%20Partner%20Network_HPC%20Storage%20Options_2019_FINAL.pdf)

### Application Integration

- [SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)
- [SNS](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)

### Management & Governance

- [Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_introduction.html)
  - Consolidated Billing
  - Service Control Policies
- [CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)
- [CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)
- [Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/)
- [CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html), [Sample Templates](https://aws.amazon.com/cloudformation/resources/templates/)

## Day 03

### Database

- [RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)
  - Types, Creation, Modification and Deletion
  - Read Replica
  - [Aurora global database](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Concepts.Aurora.GlobalDB.html)
  - [Hands-on Tutorial](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/TUT_WebAppWithRDS.html)
- [DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)
  - [DynamoDB Globle Tables](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GlobalTables.html)
  - [DAX](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html)
- ElastiCache
  - [Redis](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html), [Memcached](https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/index.html), [Comparision](https://aws.amazon.com/elasticache/redis-vs-memcached/)


### Containers

- ECS, Fargate [Workshop](https://ecs-cats-dogs.workshop.aws/en/)
- EKS, [Workshop](https://www.eksworkshop.com/)
- [Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)

### Analytics

- [Redshift](https://aws.amazon.com/redshift/)
- [EMR](https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-what-is-emr.html)
- Kinesis
  - [Data Firehose](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html)
  - [Data Streams](https://docs.aws.amazon.com/streams/latest/dev/introduction.html)
  - [Data Analytics](https://docs.aws.amazon.com/kinesisanalytics/latest/dev/what-is.html)

### Miscellaneous

- [Serverless Application Workshop](https://aws.amazon.com/getting-started/hands-on/build-serverless-web-app-lambda-apigateway-s3-dynamodb-cognito/)
- Decoupling
- [Athena](https://docs.aws.amazon.com/athena/latest/ug/what-is.html)
- [Quicksight](https://docs.aws.amazon.com/quicksight/latest/user/welcome.html)
- [Simple Monthly Calculator](https://calculator.s3.amazonaws.com/index.html), [AWS Pricing Calculator](https://calculator.aws/#/), [AWS TCO Calculator](https://awstcocalculator.com/)
- [AWS Services quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)
- Scope of service e.g. Global, Regional and AZ resources

### Wrap up


- [Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/wellarchitected-framework.pdf#welcome), [Online free training](https://www.aws.training/Details/Curriculum?id=42037), [WellArchitectedLabs](https://wellarchitectedlabs.com/)
- [AWS Blog](https://aws.amazon.com/blogs/)
- [AWS Knowledge Center](https://aws.amazon.com/premiumsupport/knowledge-center/)
- [AWS Samples](https://github.com/aws-samples), [AWS Labs](https://github.com/awslabs), [AWS Workshops](https://workshops.aws/)
- [Application Migration Workshop](https://application-migration-with-aws.workshop.aws/en)
- [AWS Solutions](https://aws.amazon.com/solutions/)
- [AWS Events](https://aws.amazon.com/events/)
- [Ramp-Up Guides](https://aws.amazon.com/training/ramp-up-guides/)
- [AWS YouTube Channel](https://www.youtube.com/channel/UCd6MoB9NC6uYN2grvUNT-Zg) reInvent, breakout sessions, aws.training, [whitepapers](https://aws.amazon.com/whitepapers/?whitepapers/), [customer case studies](https://aws.amazon.com/solutions/case-studies/), [this is my architecture](https://aws.amazon.com/this-is-my-architecture/), [Video Collection](https://awsvideocatalog.com/)
- [AWS Blog](https://aws.amazon.com/blogs/aws/), [AWS Online Tech Talks](https://aws.amazon.com/events/online-tech-talks/)
- [Exam Readiness: AWS Certified Solutions Architect – Associate](https://www.aws.training/Details/Curriculum?id=20685)
