# **Summary**

| **S.No.** | **Topic**                      | **Key Point**                                                |
| --------- |------------------------------- | ------------------------------------------------------------ |
| 1.        | **IAM User**                   | Identity to access AWS services with policies                |
| 2.        | **S3**                         | Scalable object storage with versioning, replication, events |
| 3.        | **S3 Versioning**              | Keeps all versions of an object                              |
| 4.        | **S3 Replication**             | Cross/Same region copy for backup/DR                         |
| 5.        | **S3 Objects**                 | File-like units stored in buckets                            |
| 6.        | **S3 Policy**                  | Control access via IAM or bucket policy                      |
| 7.        | **Static Hosting**             | Host websites via S3                                         |
| 8.        | **Events**                     | Triggers Lambda, SNS, SQS on changes                         |
| 9.        | **AWS Snowball**               | Physical device to transfer large data                       |
| 10.       | **Lambda**                     | Run code without managing servers                            |
| 11.       | **EC2**                        | Virtual machine in the cloud                                 |
| 12.       | **Inbound/Outbound**           | Firewall rules for EC2                                       |
| 13.       | **EBS/EFS/Instance Store**     | Different EC2 storage options                                |
| 14.       | **Snapshots**                  | Backup EBS volumes                                           |
| 15.       | **Security Group**             | Virtual firewall around EC2                                  |
| 16.       | **Instance Pricing**           | On-demand, Reserved, Spot, Savings Plan                      |
| 17.       | **Web Server**                 | Host HTTP apps on EC2                                        |
| 18.       | **AMI**                        | EC2 launch template                                          |
| 19.       | **Instance Store**             | Temporary, fast, but ephemeral storage                       |
| 20.       | **AWS CAF**                    | Framework to guide cloud migration using 6 perspectives (Business, People, Governance, Platform, Security, Operations)              |
| 21.       | **Well-Architected Framework** | 6 Pillars to build best-practice cloud solutions (Operational Excellence, Security, Reliability, Performance, Cost, Sustainability) |
| 22.       | **ALB (Application LB)**       | Layer 7 HTTP/HTTPS, content-based routing, supports WAF                                                                             |
| 23.       | **NLB (Network LB)**           | Layer 4 TCP/UDP, ultra-high performance, static IP                                                                                  |
| 24.       | **Auto Scaling Group**         | Auto-manages EC2 fleet size based on rules, improves cost and availability                                                          |
| 25.       | **VPC**                        | Isolated virtual network in AWS                       |
| 26.       | **Public Subnet**              | Has internet access via Internet Gateway              |
| 27.       | **Private Subnet**             | No internet unless via NAT Gateway                    |
| 28.       | **Route Table**                | Determines where traffic is routed                    |
| 29.       | **Internet Gateway**           | Enables internet access for VPC                       |
| 30.       | **NAT Gateway**                | Private subnet access to internet (outbound only)     |
| 31.       | **Flow Logs**                  | Log VPC traffic metadata                              |
| 32.       | **VPC Peering**                | Private communication between VPCs                    |
| 33.       | **VPC Endpoints**              | Private connection to AWS services                    |
| 34.       | **Elastic IP**                 | Static public IP for EC2, useful for fixed addressing |
| 35.       | **PrivateLink**                | Private, secure access to AWS services using private IPs           |
| 36.       | **Site-to-Site VPN**           | Secure tunnel from on-premises to AWS over public internet         |
| 37.       | **Direct Connect**             | Dedicated, high-speed connection between on-prem and AWS           |
| 38.       | **Client VPN**                 | Secure access for remote users to AWS                              |
| 39.       | **Transit Gateway**            | Central hub for connecting multiple VPCs and networks              |
| 40.       | **Global Infrastructure**      | Regions, AZs, Edge locations, built for resilience and low latency |
| 41.       | **CloudFront**                 | CDN for low-latency content delivery, serve static content, media, APIs      |
| 42.       | **Route 53**                   | DNS + domain management for domain routing, health checks          |
| 43.       | **CloudFormation**             | Infrastructure as Code using templates that Automate AWS setup                     |
| 44.       | **CDK**                        | Code-based infrastructure definition and is dev-friendly infrastructure automation |
| 45.       | **ElastiCache**                | In-memory caching service that speed up DB queries and real-time apps |
| 46.       | **Elastic Beanstalk**          | PaaS to deploy full web apps it uploads code, AWS handles infra    |
| 47.       | **CodeDeploy**                 | Automates deployment to EC2/Lambda and is safe, monitored code rollout      |
| 48.       | **CodeCommit**                 | Git repo hosted on AWS that secures source code management     |
| 49.       | **CodeBuild**                  | Compiles, tests, and packages code also automated build process           |
| 50.       | **CodePipeline**               | CI/CD orchestration used to automate the entire release cycle |
| 51.       | **CodeArtifact**               | Artifact/package repo that store and share app dependencies       |
| 52.       | **SSM**                        | Central system management used to patch, access, configure EC2s          |
| 53.       | **S3 Transfer Acceleration**   | Speed up S3 uploads used to upload large files globally            |
| 54.       | **Global Accelerator**         | Boost global app performance used to low-latency access to dynamic apps     |
| 55.       | **Outposts**                   | AWS services on-premises used to run AWS locally with cloud integration |
| 56.       | **Wavelength**                 | AWS at the edge of 5G networks used for ultra-low-latency mobile apps             |
| 57.       | **Local Zones**                | Run AWS closer to users in major cities used for low latency in metros                     |
| 58.       | **Shared Responsibility Model** | Defines security roles used for AWS secures infra; you secure data/config |
| 59.       | **DDoS Protection**            | Infra absorbs attack traffic used to protect your apps’ availability          |
| 60.       | **AWS Shield**                 | DDoS protection service used for auto-protection + paid advanced option    |
| 61.       | **Network Firewall**           | Deep VPC-level traffic inspection used for advanced control over subnet traffic   |
| 62.       | **Firewall Manager**           | Central firewall policy manager used to apply security rules across accounts   |
| 63.       | **Penetration Testing**        | Ethical hacking (allowed on some services) used to test your own AWS setup for weaknesses |
| 64.       | **AWS KMS**                    | Manage encryption keys used to encrypt S3, EBS, RDS, Lambda securely  |
| 65.       | **CloudTrail**                 | Logs all AWS account activity used to audit, security monitoring, compliance |
| 66.       | **Certificate Manager**        | Manage SSL/TLS certs used to secure apps/websites with HTTPS            |
| 67.       | **Secrets Manager**            | Store & rotate credentials used to secure access to DBs/APIs                  |
| 68.       | **Artifact**                   | Access AWS compliance docs used to verify AWS certifications (SOC, PCI, etc.) |
| 69.       | **GuardDuty**                  | Detects AWS threats automatically used for unusual logins, compromised accounts       |
| 70.       | **Inspector**                  | Scans for vulnerabilities used to secure EC2, Lambda, and containers         |
| 71.       | **AWS Config**                 | Tracks resource configuration and compliance     |
| 72.       | **Amazon Macie**               | Detects sensitive data like PII in S3 buckets    |
| 73.       | **Security Hub**               | Centralized security alert and compliance view   |
| 74.       | **Amazon Detective**           | Investigates and visualizes suspicious activity  |
| 75.       | **AWS Abuse**                  | Reports AWS resource misuse (spam, hacking etc.) |
| 76.       | **IAM Access Analyzer**        | Identifies publicly or externally shared resources  |
| 77.       | **CloudWatch Metrics**         | Tracks performance stats like CPU, memory, DB usage |
| 78.       | **CloudWatch Logs**            | Collects application and AWS service logs           |
| 79.       | **EventBridge**                | Automates workflows triggered by AWS service events |
| 80.       | **AWS X-Ray**                  | Traces distributed apps to diagnose latency issues  |
| 81.       | **CodeGuru**                   | AI-based tool for code reviews and application profiling  |
| 82.       | **Health Dashboard**           | Provides real-time alerts on AWS service health           |
| 83.       | **Cloud Integration**          | Enables communication between AWS services                |
| 84.       | **Amazon SQS**                 | Manages asynchronous message queues for decoupled systems |
| 85.       | **Amazon Kinesis**             | Streams real-time data for analytics and processing       |
| 86.       | **Amazon SNS**                 | Publishes messages for alerts via email, SMS, etc. (pub/sub model)    |
| 87.       | **Amazon MQ**                  | Managed message broker for legacy app migration                       |
| 88.       | **CloudTrail**                 | Logs all API calls and user activity for auditing and compliance      |
| 89.       | **AWS Organizations**          | Centralized management of multiple AWS accounts                       |
| 90.       | **Multi-Account Strategy**     | Best practices for account segmentation to enhance control & tracking |
| 91.       | **SCPs**                       | Set permission guardrails for AWS Organizations to restrict actions      |
| 92.       | **Control Tower**              | Automates secure and compliant multi-account AWS environment setup       |
| 93.       | **AWS RAM**                    | Enables sharing of AWS resources (like VPCs, TGWs) across accounts       |
| 94.       | **Service Catalog**            | Provides standardized templates for approved resource provisioning       |
| 95.       | **Pricing Models**             | Offers cost options like On-Demand, Reserved, and Spot to optimize spend |
| 96.       | **Compute Optimizer**          | Suggests right-sized resources to prevent over/under-provisioning    |
| 97.       | **Pricing Calculator**         | Helps estimate AWS service costs for budgeting and planning          |
| 98.       | **Trusted Advisor**            | Recommends best practices for cost, security, and performance        |
| 99.       | **Cost Explorer**              | Provides visual insights into usage and cost trends for optimization |
| 100.      | **Cost**                       | Ranges from Free to \~\$15k/month based on support tier               |
| 101.      | **24/7 Support**               | Available only in Business and above                                  |
| 102.      | **TAM (Technical Manager)**    | Provided fully in Enterprise, partial in Enterprise On-Ramp           |
| 103.      | **Trusted Advisor – Full**     | Full checks available in Business and higher tiers                    |
| 104.      | **Support API**                | Accessible in Business, Enterprise On-Ramp, and Enterprise tiers      |
| 105.      | **Response Time – Prod Down**  | Fastest in Enterprise (<15 min), slower or unavailable in lower tiers |
| 106.      | **Docker**                     | Open-source platform to build and run portable containerized apps |
| 107.      | **EKS**                        | Managed Kubernetes service for running scalable microservices     |
| 108.      | **ECS**                        | AWS-native container orchestration for simple container workloads |
| 109.      | **ECR**                        | Secure repository for storing and managing container images       |
| 110.      | **API Gateway**                | Fully managed service to create, publish, and manage APIs         |
| 111.      | **AWS Batch**                  | Enables efficient batch job execution at any scale                |
| 112.      | **Databases**                  | Used to store structured or unstructured data for applications      |
| 113.      | **NoSQL**                      | Non-relational DB for flexible, real-time, schema-less applications |
| 114.      | **RDS**                        | Managed SQL database for traditional relational workloads           |
| 115.      | **Aurora**                     | High-performance, scalable SQL engine compatible with RDS           |
| 116.      | **Read Replica**               | Read-only copy of a database to distribute and optimize read loads  |
| 117.      | **RDS Multi-Region**           | Cross-region read replicas for disaster recovery and global access |
| 118.      | **ElastiCache**                | In-memory caching layer to speed up RDS/DynamoDB queries           |
| 119.      | **DynamoDB**                   | Fully managed, serverless NoSQL key-value database                 |
| 120.      | **DAX**                        | DynamoDB Accelerator for ultra-fast read performance               |
| 121.      | **Global Tables**              | Enables multi-region, multi-active replication for DynamoDB        |
| 122.      | **Redshift**                   | Data warehouse for OLAP workloads like big data analytics and BI        |
| 123.      | **EMR**                        | Managed big data platform for ETL, ML, and Apache Spark jobs            |
| 124.      | **Athena**                     | Run SQL queries directly on S3 data without provisioning infrastructure |
| 125.      | **QuickSight**                 | BI tool to build dashboards and visual reports                          |
| 126.      | **DocumentDB**                 | Managed NoSQL document database for JSON-based application workloads    |
| 127.      | **Neptune**                    | Graph database for use cases like social networks and fraud detection     |
| 128.      | **Timestream**                 | Time-series database optimized for IoT and DevOps metric data             |
| 129.      | **Managed Blockchain**         | Distributed ledger for trusted, multi-party transactions and traceability |
| 130.      | **Glue**                       | Serverless ETL service for data preparation and cataloging                |
| 131.      | **Amplify**                    | Platform to quickly build full-stack apps with a managed backend          |
| 132.      | **AppSync**                    | Managed GraphQL API service for mobile and web app backends       |
| 133.      | **OpsWorks**                   | Configuration management using Chef or Puppet automation          |
| 134.      | **Cognito**                    | Provides user authentication and authorization (OAuth, SSO, etc.) |
| 135.      | **Cloud9**                     | Cloud-based IDE for coding directly in the browser                |
| 136.      | **CodeStar**                   | Orchestrates CI/CD pipelines for rapid full-stack app development |


