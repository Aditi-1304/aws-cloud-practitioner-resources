# Descriptions:

### **1. IAM User**

- **IAM (Identity and Access Management)** is used to manage access to AWS services.
- An **IAM user** is an identity created for a person or application.
- Each user has **credentials (username/password or access keys)** and **permissions (via policies)**.
- Best practice: **Use IAM users, not root**, and give **least privilege access**.

---

### **2. Amazon S3 (Simple Storage Service)**

Object storage service for any type of data.

#### ▸ **Versioning**

- Stores **multiple versions** of an object.
- Useful for **data recovery** or rollback.
- Once enabled on a bucket, it **cannot be disabled**, only suspended.

#### ▸ **Replication**

- Automatically copies objects across **buckets in same or different AWS Regions**.
- Two types:

  - **SRR**: Same Region Replication
  - **CRR**: Cross Region Replication (disaster recovery)

#### ▸ **Objects**

- Basic unit of storage in S3.
- Each object = data + metadata + unique key.
- Stored in **buckets**.

#### ▸ **Policy Attach**

- Attach **bucket policies** or **IAM policies** to control access.
- Bucket policies are **resource-based**, while IAM policies are **identity-based**.

#### ▸ **Static Website Hosting**

- You can **host a static website** (HTML, CSS, JS) directly from an S3 bucket.
- Requires enabling **public access**, specifying **index and error documents**.

#### ▸ **Cross Region Replication**

- Automatically replicates objects from one AWS Region to another.
- Must enable **versioning** on both source and destination buckets.
- Useful for **high availability** and **disaster recovery**.

#### ▸ **Event Configuration**

- Configure S3 to trigger **events** (like object upload/delete) to services like:

  - **Lambda**
  - **SNS**
  - **SQS**

- Enables **serverless workflows**, e.g., process files as they're uploaded.

---

### **3. AWS Snowball**

- **Physical device** for moving large volumes of data to/from AWS.
- Use case: when data transfer over the internet is **too slow or expensive**.
- Variants:

  - **Snowball Edge Storage Optimized**
  - **Snowball Edge Compute Optimized**

- Part of **AWS Snow Family** (includes Snowmobile and Snowcone).

---

### **4. AWS Lambda**

- **Serverless compute**: Run code without provisioning servers.
- Triggered by **events** (S3 upload, API Gateway, DynamoDB streams, etc.)
- Pay only for **compute time** used (in milliseconds).
- Supports many languages: Python, Node.js, Java, etc.

---

### **5. Amazon EC2 (Elastic Compute Cloud)**

- Virtual servers in the cloud.
- You choose instance type, OS, network, storage, etc.

#### ▸ **Outbound & Inbound Rules**

- Defined in **security groups**.
- Inbound: controls **incoming traffic** (e.g., allow port 80 for HTTP).
- Outbound: controls **outgoing traffic** from instance.

#### ▸ **Storage Types**

- **EBS (Elastic Block Store)**: Persistent block storage. Remains after instance termination.
- **EFS (Elastic File System)**: Shared file storage across instances.
- **Instance Store**: Temporary storage attached to an instance. **Data lost when stopped**.

#### ▸ **Snapshots**

- **Backups** of EBS volumes.
- Stored in **Amazon S3** (but not accessible as objects).
- Used to **create new volumes or AMIs**.

#### ▸ **Security Group**

- Acts as a **virtual firewall** for your EC2 instances.
- Controls **traffic rules** (inbound & outbound).
- **Stateful**: return traffic is automatically allowed.

#### ▸ **Instance Pricing**

- **On-Demand**: Pay per hour/second.
- **Reserved**: 1- or 3-year commitment for significant discount.
- **Spot**: Bid for unused capacity at discount.
- **Savings Plans**: Flexible pricing model for long-term use.

#### ▸ **Web Server**

- EC2 can be used to host web servers like **Apache**, **Nginx**.
- Often used with **Elastic IP**, **Auto Scaling**, and **Load Balancer**.

#### ▸ **AMI Creation**

- AMI (Amazon Machine Image) is a **template** to launch EC2 instances.
- Includes OS, application server, and applications.
- You can **create custom AMIs** from existing instances.

#### ▸ **Instance Store**

- **Temporary block-level storage**.
- High speed, but **data lost** when instance is stopped, terminated, or crashes.
- Useful for temporary caching, buffers.

---

### **6. AWS CAF (Cloud Adoption Framework)**

The **AWS Cloud Adoption Framework** helps organizations **successfully migrate to the cloud** by providing structured **guidance** across key business areas.

#### ▸ **Six CAF Perspectives**:

| Perspective    | Focus                                                      |
| -------------- | ---------------------------------------------------------- |
| **Business**   | Business goals, value realization, cost management         |
| **People**     | Training, organizational change, roles & responsibilities  |
| **Governance** | Compliance, risk, and cloud policies                       |
| **Platform**   | Cloud architecture, infrastructure, and deployment         |
| **Security**   | Identity, access, detection, protection, incident response |
| **Operations** | Ongoing monitoring, support, and operations processes      |

CAF helps organizations build a **cloud migration strategy** and **align IT with business objectives**.

---

### **7. AWS Well-Architected Framework: Six Pillars**

Helps design **secure, high-performing, resilient, and efficient** cloud architectures.

#### ▸ **Six Pillars**:

| Pillar                     | Description                                          |
| -------------------------- | ---------------------------------------------------- |
| **Operational Excellence** | Monitor and improve systems, automate changes        |
| **Security**               | Protect data, systems, and assets                    |
| **Reliability**            | Ensure workload performs as intended and can recover |
| **Performance Efficiency** | Use resources efficiently and scale to meet demand   |
| **Cost Optimization**      | Avoid unnecessary costs                              |
| **Sustainability**         | Minimize environmental impacts of workloads          |

Each pillar includes **best practices**, **design principles**, and **questions** to assess and improve your architecture.

---

### **8. Load Balancer (Elastic Load Balancing)**

Distributes incoming traffic across **multiple targets** (e.g., EC2 instances) to improve **availability**, **fault tolerance**, and **performance**.

#### ▸ **Application Load Balancer (ALB)**

- **Layer 7 (HTTP/HTTPS)** aware.
- Supports **host-based and path-based routing**.
- Used for web applications, REST APIs, microservices.
- Integrates with **WAF**, **SSL termination**, and **container-based apps**.

#### ▸ **Network Load Balancer (NLB)**

- **Layer 4 (TCP/UDP)** load balancing.
- Handles **high-performance** and **low-latency** traffic.
- Used for applications requiring **static IPs** and high throughput.
- Scales to **millions of requests per second**.

---

### **10. Auto Scaling Group (ASG)**

Automatically adds or removes **EC2 instances** based on **demand** or **defined conditions** (like CPU usage or time schedules).

#### ▸ Key Features:

- Ensures **availability and cost-efficiency**.
- Works with **CloudWatch alarms** for dynamic scaling.
- Can be used with **ALB** to distribute traffic to new instances.
- Defines:

  - **Min**, **Max**, and **Desired** number of instances.
  - **Scaling policies** (manual, scheduled, or dynamic).

#### ▸ Benefits:

- **Resilience**: Replaces unhealthy instances.
- **Cost-effective**: Scales out/in based on need.

---

### **11. AWS VPC (Virtual Private Cloud)**

A **VPC** is your own **isolated network** within AWS where you can launch AWS resources (e.g., EC2, RDS).

#### ▸ **Public Subnet**

- **Accessible from the internet**.
- Typically hosts **web servers**, **ALBs**, etc.
- Requires:

  - **Internet Gateway**
  - **Route table entry to Internet Gateway**

#### ▸ **Private Subnet**

- **No direct internet access**.
- Used for **databases**, **backend servers**, etc.
- Can **access internet** using a **NAT Gateway** (for updates or outbound traffic).

#### ▸ **Route Table**

- Controls **network traffic routing**.
- Each subnet must be associated with a **route table**.
- Routes specify where traffic is sent (e.g., to Internet Gateway, NAT, VPC Peering).

---

### **12. Internet Gateway (IGW)**

- A **managed gateway** that connects your **VPC to the internet**.
- Required for **outbound and inbound** internet access to/from **public subnets**.
- Must be **attached to the VPC** and **used in route tables**.

---

### **13. NAT Gateway (Network Address Translation)**

- Enables instances in a **private subnet** to **access the internet** for things like OS updates or downloading packages.
- **Prevents internet-initiated inbound traffic** (i.e., maintains privacy).
- Must be placed in a **public subnet**.
- **Paid AWS managed service**, scales automatically.

---

### **14. VPC Advanced Features**

#### ▸ **Flow Logs**

- Captures **network traffic metadata** for:

  - Security analysis
  - Troubleshooting
  - Compliance

- Logs stored in **CloudWatch** or **S3**.

#### ▸ **VPC Peering**

- Connects **two VPCs** to communicate **privately** using **AWS backbone**.
- Peered VPCs can be in **same or different regions/accounts**.
- **No transitive peering**: VPC A ↔ VPC B ↔ VPC C does NOT mean A ↔ C.

#### ▸ **VPC Endpoints**

- Allow **private connection** to AWS services (e.g., S3, DynamoDB) **without using the internet**.
- Two types:

  - **Interface endpoint**: Powered by **ENI (Elastic Network Interface)**.
  - **Gateway endpoint**: Used for **S3 & DynamoDB**.

---

### **15. Elastic IP**

- A **static, public IPv4 address** that you can assign to an EC2 instance.
- Useful when you need a **fixed IP** for external access.
- Can **reassociate** it if an instance is stopped or terminated.
- **Limited by default**, charges apply if **not in use**.

---

### **16. AWS PrivateLink**

- Allows you to **privately access services** hosted in **another VPC** or **AWS service** using **private IPs**.
- Uses **interface VPC endpoints** (powered by ENIs).
- Traffic **stays within the AWS network**, not over the public internet.
- Common use: Accessing services like **S3**, **SNS**, or **3rd-party SaaS apps** securely.

▸ **Key Benefit**: **Secure**, **private**, and **scalable** connectivity to services **without exposing traffic to the internet**.

---

### **17. Site-to-Site VPN & AWS Direct Connect**

#### ▸ **Site-to-Site VPN**

- Creates a **secure encrypted tunnel** between **your on-premises network** and **AWS VPC** over the **public internet**.
- Uses **IPSec**.
- Easy to set up and **cost-effective**, but may have **latency** or **bandwidth fluctuations**.

#### ▸ **AWS Direct Connect**

- Provides a **dedicated physical connection** from your on-premises data center to AWS.
- **More reliable**, **lower latency**, and **higher bandwidth** than VPN.
- Used when you need **stable, consistent network performance** (e.g., for large data transfers, hybrid cloud setups).

---

### **18. AWS Client VPN**

- A **managed VPN service** that allows **remote users (e.g., employees)** to securely connect to AWS or on-premises networks.
- **OpenVPN-based** and supports **multi-factor authentication (MFA)**.
- Scales automatically and supports **access from laptops, desktops, etc.**

▸ Think: **Site-to-Site = office to AWS**,
**Client VPN = remote worker to AWS**.

---

### **19. AWS Transit Gateway**

- A **central hub** to connect **multiple VPCs**, **on-prem networks**, and **VPNs**.
- Replaces the need for **complex VPC peering** (which is 1-to-1).
- Uses a **hub-and-spoke** model.
- Simplifies **routing**, **security**, and **management** across large architectures.

▸ Scales well for **enterprise and hybrid cloud** setups.

---

### **20. AWS Global Infrastructure**

The **foundation of AWS services worldwide**, designed for **resilience, low latency, and compliance**.

#### ▸ Key Components:

| Component                    | Description                                                                          |
| ---------------------------- | ------------------------------------------------------------------------------------ |
| **Regions**                  | Geographically isolated locations (e.g., `us-east-1`, `ap-south-1`)                  |
| **Availability Zones (AZs)** | Physically separated data centers within a region (min 2, usually 3)                 |
| **Edge Locations**           | Global CDN endpoints for low-latency content delivery (used by CloudFront, Route 53) |
| **Local Zones**              | Extend AWS closer to end-users in large metro areas                                  |
| **Wavelength Zones**         | For ultra-low-latency applications with **5G networks**                              |

▸ AWS designs infrastructure for **high availability, fault tolerance, and redundancy**.

---

### **21. Amazon CloudFront**

A **Content Delivery Network (CDN)** that delivers **web content, videos, APIs**, and other assets to users **faster** by caching them at **edge locations**.

#### ▸ Key Points:

- Uses a **global network of edge locations** (200+ worldwide).
- Reduces **latency** and **server load**.
- Integrates with **S3**, **ALB**, **EC2**, and **Route 53**.
- Supports **HTTPS**, **Geo-restriction**, and **DDoS protection** via AWS Shield.

▸ **Use case**: Serving static assets for websites, streaming video, securing APIs.

---

### **22. Amazon Route 53**

A **scalable and highly available Domain Name System (DNS)** web service.

#### ▸ Key Functions:

- **Domain Registration**: Buy and manage domain names (e.g., `example.com`).
- **DNS Resolution**: Converts domain names into IP addresses.
- **Health Checks**: Route traffic only to healthy resources.
- **Routing Policies**:

  - **Simple routing**
  - **Failover routing**
  - **Latency-based routing**
  - **Geolocation routing**
  - **Weighted routing**

▸ **Use case**: Directing user traffic to the nearest or healthiest AWS resource (e.g., EC2 or ALB).

---

### **23. AWS CloudFormation**

A service that helps you **automate infrastructure deployment** using **code (Infrastructure as Code – IaC)**.

#### ▸ How it works:

- You define resources (EC2, S3, IAM, etc.) in a **YAML/JSON template**.
- CloudFormation creates and manages them automatically.

▸ **Key Benefits**:

- **Repeatability**: Same setup in dev/test/prod.
- **Automation**: No manual provisioning.
- **Rollback support**: Automatically reverts on failure.

---

### **24. AWS Cloud Development Kit (CDK)**

A **software development framework** to define AWS infrastructure using **programming languages** like **Python, TypeScript, Java, or C#**.

#### ▸ Key Differences from CloudFormation:

- CDK is **code-first**, CloudFormation is **declarative**.
- CDK synthesizes into a CloudFormation template under the hood.
- Great for **developers comfortable with code**, supports abstraction and reuse.

▸ **Use case**: Automating infrastructure with real programming logic and reusable constructs.

---

### **25. Amazon ElastiCache**

A **fully managed in-memory data store** that boosts application performance by **caching frequently accessed data**.

#### ▸ Two Engine Options:

- **Redis**: Supports advanced data structures, pub/sub, backups.
- **Memcached**: Simple and fast caching engine.

#### ▸ Benefits:

- **Low latency** data access (microseconds).
- Reduces **load on databases**.
- Supports **real-time apps**, leaderboards, session stores, etc.

▸ **Use case**: Caching frequent queries, speeding up web apps, offloading DBs.

---

### **26. AWS Elastic Beanstalk**

A **Platform-as-a-Service (PaaS)** that lets you **deploy web applications** without managing servers, networking, or infrastructure.

#### ▸ Key Features:

- Supports **Java, Python, Node.js, PHP, .NET, Go, Ruby**, and Docker.
- You just upload your code — AWS handles provisioning:

  - EC2, ELB, Auto Scaling, RDS, etc.

- You can still **access the infrastructure** (like EC2) if needed.

▸ **Use case**: Quickly deploy a web app with minimal configuration.

---

### **27. AWS CodeDeploy**

A **deployment automation tool** that helps you **deploy code to EC2, Lambda, or on-prem servers** safely and consistently.

#### ▸ Features:

- Supports **rolling updates**, **blue/green deployments**, and **canary releases**.
- Minimizes **downtime** and supports **automatic rollback** if something fails.
- Tracks **deployment status** and logs.

▸ **Use case**: Automated code rollout to your servers or serverless apps.

---

### **28. AWS CodeCommit**

A **fully managed Git-based source code repository** similar to GitHub or GitLab.

#### ▸ Key Points:

- **Secure** (integrates with IAM).
- No size limits on repos or files.
- Code is stored **privately in AWS**.

▸ **Use case**: Store source code, track versions, and collaborate with your team on AWS.

---

### **29. AWS CodeBuild**

A **build service** that compiles source code, runs tests, and produces artifacts.

#### ▸ How it fits in DevOps:

- Runs as part of CI/CD pipeline.
- You define **build commands** in a `buildspec.yml` file.
- Scales automatically and **charges by the minute**.

▸ **Use case**: Compile code, run tests, and package the app automatically after every change.

---

### **30. AWS CodePipeline**

A **CI/CD service** to **automate the full software release process**.

#### ▸ Key Concepts:

- Connects **CodeCommit** → **CodeBuild** → **CodeDeploy** into stages.
- Automatically runs each stage on code change.
- Supports integration with **GitHub, Jenkins**, third-party tools.

▸ **Use case**: Automate and visualize your app release pipeline from source to deployment.

---

### **31. AWS CodeArtifact**

A **fully managed software artifact repository** for storing packages (dependencies) used in development.

#### ▸ Supports:

- **Maven, npm, PyPI, NuGet** (JavaScript, Python, Java, .NET)
- Integrates with **CodeBuild**, **CodePipeline**

▸ **Use Case**: Share and manage **build dependencies** across teams or projects securely.

---

### **32. AWS Systems Manager (SSM)**

A **central management service** for AWS infrastructure — think of it as a _Swiss Army knife_ for system admins.

#### ▸ Key Features:

- **Session Manager**: Secure shell access (SSH-less) to EC2.
- **Run Command**: Execute shell commands across multiple EC2 instances.
- **Patch Manager**: Automate OS patching.
- **Parameter Store**: Securely store configuration variables like API keys.

▸ **Use Case**: Operate, secure, and automate large-scale EC2 and hybrid environments.

---

### **33. S3 Transfer Acceleration**

Speeds up **uploading large files to S3 buckets** over long distances using Amazon's **global edge network**.

#### ▸ How it works:

- Users upload to a **nearby AWS edge location** (like CloudFront).
- Data is then transferred quickly through AWS’s **backbone network** to your S3 bucket.

▸ **Use Case**: Upload files from far-away locations (e.g., from India to a US S3 bucket) **faster** than regular internet uploads.

---

### **34. AWS Global Accelerator**

Improves **performance and availability** of global applications by **routing traffic through the AWS global network**.

#### ▸ Features:

- Uses **static IPs** that route users to the **optimal AWS endpoint**.
- Unlike CloudFront (which caches content), Global Accelerator accelerates **non-cacheable, dynamic content** (like APIs).

▸ **Use Case**: Real-time applications (like gaming, streaming, APIs) that need **global, low-latency access**.

---

### **35. AWS Outposts**

Brings **AWS infrastructure and services to your on-premises** data center.

#### ▸ What It Does:

- You run AWS services **locally** while staying connected to the **AWS cloud**.
- Supports services like EC2, EBS, RDS, S3, and ECS locally.

▸ **Use Case**: Companies needing **low latency**, **data residency**, or operating in areas with **limited AWS region access**.

---

### **36. AWS Wavelength**

Brings **AWS services to telecom 5G networks** for **ultra-low-latency** applications.

#### ▸ Key Points:

- Deployed in **Wavelength Zones** inside **telecom provider data centers**.
- Ideal for apps like **AR/VR, IoT, video streaming, real-time gaming**.
- Keeps traffic closer to end users, bypassing long internet routes.

▸ **Use case**: Deliver **real-time services over 5G** with extremely low latency (single-digit milliseconds).

---

### **37. AWS Local Zones**

AWS infrastructure that brings **compute, storage, database** services **closer to large population centers**.

#### ▸ Key Points:

- Extends AWS regions to **cities where there's no full region**.
- Reduces **latency** for end-users in metros like Los Angeles, Mumbai, etc.
- You can run services like **EC2, EBS, ELB, RDS, ECS** locally.

▸ **Use case**: Latency-sensitive workloads (like video editing, gaming) in cities **far from existing AWS regions**.

---

### **38. AWS Shared Responsibility Model**

Explains **who is responsible** for what in AWS: **AWS vs. YOU (the customer)**.

#### ▸ AWS is responsible for:

- **Security “of” the cloud**: physical infrastructure, networking, hardware, managed services (like RDS platform).

#### ▸ Customer is responsible for:

- **Security “in” the cloud**: your data, access controls, OS patching (for EC2), configuration, IAM, etc.

#### ▸ Examples:

| Service | AWS is responsible for                      | Customer is responsible for                  |
| ------- | ------------------------------------------- | -------------------------------------------- |
| **RDS** | DB engine patching, backups, infrastructure | Data security, access via IAM, DB configs    |
| **S3**  | Physical storage, replication               | Bucket policies, data encryption, versioning |

▸ **Exam Tip**: AWS handles the infra, you handle access, config, and data.

---

### **39. DDoS Protection**

A **Distributed Denial of Service (DDoS)** attack floods a server or app with massive traffic, disrupting availability.

#### ▸ AWS Protects You By:

- Built-in protections with **Route 53, CloudFront, ELB**.
- Using **scalable and redundant infrastructure** to absorb traffic.
- Integrating services like **AWS Shield** and **WAF (Web App Firewall)**.

▸ **Use case**: Automatically protect high-traffic apps from malicious spikes.

---

### **40. AWS Shield**

A **managed DDoS protection service** for AWS-hosted applications.

#### ▸ Two Tiers:

| Tier                | Description                                                                                            |
| ------------------- | ------------------------------------------------------------------------------------------------------ |
| **Shield Standard** | Free for all AWS users. Automatically protects against common, low-volume attacks.                     |
| **Shield Advanced** | Paid. Includes 24x7 DDoS response team (DRT), deeper insights, and **cost protection** during attacks. |

▸ **Use case**: Shield Standard is sufficient for most; large enterprises may opt for **Advanced**.

---

### **41. AWS Network Firewall**

A **managed network firewall** for **VPCs** to inspect and control traffic at the **network level**.

#### ▸ Key Features:

- Stateful firewall rules to allow/block **IP addresses, ports, protocols**.
- Deep packet inspection (DPI).
- Protects **VPCs** from common threats like **port scanning, malware, and exploits**.
- Integrates with **VPC route tables** and **subnets**.

▸ **Use Case**: Add **advanced traffic filtering** for VPCs in sensitive workloads (e.g., finance, healthcare).

---

### **42. AWS Firewall Manager**

A **centralized security management service** for managing **firewall rules across multiple AWS accounts**.

#### ▸ Manages:

- **AWS WAF** (Web Application Firewall)
- **Shield Advanced**
- **VPC Network Firewall**
- **Security Groups**

▸ **Use Case**: Enterprises using **AWS Organizations** to apply consistent firewall/security policies across multiple accounts and regions.

---

### **43. Penetration Testing on AWS Cloud**

AWS **allows penetration testing** (ethical hacking) on **certain approved services** without prior approval.

#### ▸ Allowed Services (no approval needed):

- EC2, RDS, CloudFront, Aurora, API Gateway, Lambda, etc.

#### ▸ Rules:

- Must **not impact other AWS customers**.
- Must follow AWS's **[Penetration Testing Policy](https://aws.amazon.com/security/penetration-testing/)**.
- Some types of tests (e.g., DDoS, port flooding) **are NOT allowed** without special permission.

▸ **Use Case**: Customers wanting to **test their own cloud infrastructure’s security**.

---

### **44. AWS KMS (Key Management Service)**

A **secure, managed encryption key service** for creating and controlling encryption keys.

#### ▸ Key Features:

- Generates **Customer Master Keys (CMKs)**.
- Supports **encryption at rest** for services like S3, EBS, RDS, etc.
- Integrates with **CloudTrail** for audit logging.
- Keys can be **customer-managed** or **AWS-managed**.

▸ **Use Case**: Encrypting sensitive data and controlling who can decrypt it using **IAM + KMS** permissions.

---

### **45. AWS CloudTrail**

A **logging service** that records **all account-level activity** and API calls made in your AWS environment.

#### ▸ Tracks:

- **Who did what**, when, and from where.
- Actions taken via **AWS Console, CLI, SDKs, and APIs**.
- Stored in **S3** and can be analyzed in **CloudWatch or Athena**.

▸ **Use Case**: **Security auditing**, **compliance**, **incident response**, and **troubleshooting**.

---

### **46. AWS Certificate Manager (ACM)**

Manages **SSL/TLS certificates** to enable secure HTTPS connections to your websites or applications.

#### ▸ Key Features:

- **Provision, manage, and renew** certificates automatically.
- Use with services like **Elastic Load Balancer, CloudFront, API Gateway**.
- No manual steps for validation or renewal (for ACM-provided certs).

▸ **Use Case**: Secure websites or APIs with **free, auto-renewing SSL certificates**.

---

### **47. AWS Secrets Manager**

A **secure store** for managing **secrets** like API keys, database credentials, and tokens.

#### ▸ Key Features:

- Automatically **rotates secrets** (e.g., DB passwords).
- **Encrypts secrets** using AWS KMS.
- Fine-grained access control via **IAM**.
- Logs secret access with **CloudTrail**.

▸ **Use Case**: Securely store and rotate app credentials or tokens.

---

### **48. AWS Artifact**

Provides **on-demand access to AWS compliance reports** and **agreements**.

#### ▸ Includes:

- SOC 1, SOC 2, PCI, ISO, GDPR compliance docs.
- **NDA-based access** to AWS audit documentation.
- Reports are downloadable and updated regularly.

▸ **Use Case**: Organizations needing to **verify AWS compliance** for legal/regulatory needs.

---

### **49. Amazon GuardDuty**

An **intelligent threat detection** service that monitors AWS accounts for **malicious activity**.

#### ▸ Detects:

- Unusual login attempts.
- Compromised IAM users or EC2 instances.
- Reconnaissance (e.g., port scanning).
- Uses **machine learning** and **threat intel feeds**.

▸ **Use Case**: Automatically monitor for **suspicious behavior** without installing anything.

---

### **50. Amazon Inspector**

Automatically **scans AWS workloads** for **vulnerabilities** and **security issues**.

#### ▸ Scans:

- EC2 instances for **CVEs (Common Vulnerabilities and Exposures)**.
- Lambda functions for **code flaws**.
- **ECR (container images)** for known risks.

▸ **Use Case**: Continuous **security assessment** of EC2, Lambda, and containers.

---

### **51. AWS Config**

Tracks **configuration changes** in your AWS resources and ensures they **comply with rules** you define.

#### ▸ What it does:

- Continuously **monitors and records** resource configuration changes.
- Shows how a resource **was configured at any point in time**.
- Checks **compliance** (e.g., S3 buckets must be private).

▸ **Use Case**: **Audit trail + compliance checking** for your infrastructure.

---

### **52. Amazon Macie**

A **data security and privacy service** that uses **ML** to discover and protect **sensitive data** in **S3**.

#### ▸ What it does:

- Automatically finds **PII** (names, addresses, credit card info, etc.).
- Flags **unprotected or publicly exposed** data.
- Provides dashboards for **data classification**.

▸ **Use Case**: **Protect personal and sensitive data** stored in S3.

---

### **53. AWS Security Hub**

A **centralized dashboard** for managing and prioritizing **security alerts** from various AWS services.

#### ▸ Integrates with:

- **GuardDuty, Macie, Inspector, Firewall Manager**, and third-party tools.
- Aggregates findings and **ranks by severity**.
- Helps meet compliance frameworks like **CIS AWS Foundations**.

▸ **Use Case**: One place to **view, analyze, and act on security alerts**.

---

### **54. Amazon Detective**

Helps **investigate and analyze suspicious activity** in your AWS accounts using data from **CloudTrail, GuardDuty, and VPC Flow Logs**.

#### ▸ What it does:

- Automatically collects and links events.
- Builds **visual timelines and graphs** to show what happened.
- Useful during **security incident investigations**.

▸ **Use Case**: Dig deeper into “what happened” after a **security alert** is triggered.

---

### **55. AWS Abuse**

A **reporting system** for notifying AWS if **someone is using AWS resources maliciously**.

#### ▸ Used when:

- You see spam, phishing, port scanning, DDoS originating from AWS IPs.
- **Not for reporting issues with your own AWS account**.
- Report via: [aws.amazon.com/forms/report-abuse](https://aws.amazon.com/forms/report-abuse)

▸ **Use Case**: **Report misuse** of AWS resources by others (e.g., suspicious traffic from EC2 instance not owned by you).

---

### **56. IAM Access Analyzer**

Helps you **identify resources in your AWS account that are accessible publicly or from other accounts**.

#### ▸ What it does:

- Analyzes **S3 buckets, IAM roles, KMS keys, Lambda functions**, etc.
- Alerts you if a resource is **shared with external accounts or made public**.
- Works **automatically** and shows findings in IAM or via AWS CLI.

▸ **Use Case**: **Detect accidental public access** to sensitive AWS resources.

---

### **57. AWS CloudWatch Metrics**

Part of **Amazon CloudWatch** — tracks **performance metrics** for AWS services and custom applications.

#### ▸ Examples:

- **EC2**: CPU utilization, disk I/O, network usage.
- **RDS**: DB connections, read/write throughput.
- **Custom metrics**: App-level stats like user counts or transaction speeds.

▸ **Use Case**: **Monitor AWS services** and get alerts when usage crosses thresholds.

---

### **58. CloudWatch Logs**

Lets you **collect, monitor, and store logs** from AWS services and your applications.

#### ▸ Examples:

- **Lambda function output logs**
- **EC2 system logs**
- **Application logs**

#### ▸ Features:

- Can set up **log-based alarms**
- Integrates with **CloudWatch Insights** for log analysis

▸ **Use Case**: **Store and analyze logs** for troubleshooting and audits.

---

### **59. Amazon EventBridge**

_(Previously CloudWatch Events)_

A **serverless event bus** that connects AWS services with your own apps, based on **events and rules**.

#### ▸ Key Uses:

- **Trigger Lambda functions** when new S3 objects are uploaded.
- Send events from **SaaS apps (like Zendesk, Auth0)** to AWS.
- **Automated workflows** based on AWS service events.

▸ **Use Case**: **Event-driven automation** between services and apps.

---

### **60. AWS X-Ray**

A **distributed tracing tool** for debugging and analyzing **microservices and serverless applications**.

#### ▸ What it shows:

- Latency across services (e.g., API Gateway → Lambda → DynamoDB)
- Service maps with bottlenecks highlighted
- Errors and performance traces

▸ **Use Case**: **Troubleshoot slow or error-prone APIs** and pinpoint performance issues.

---

### **61. Amazon CodeGuru**

An **AI-powered tool** for **code reviews** and **application performance profiling**.

#### ▸ Two Main Features:

- **CodeGuru Reviewer**: Analyzes Java/Python code for **bugs, inefficiencies, and security issues**.
- **CodeGuru Profiler**: Finds **performance bottlenecks** in live apps.

▸ **Use Case**: Help developers **write better, more efficient, and secure code** using AI recommendations.

---

### **62. AWS Health Dashboard**

Provides **real-time and personalized alerts** about **AWS service health** and **account-specific issues**.

#### ▸ Types of Notifications:

- Service outages or disruptions.
- Planned maintenance.
- Issues **specifically affecting your AWS resources**.

▸ **Use Case**: **Stay informed** about ongoing or upcoming events that affect **your AWS infrastructure**.

---

### **63. Cloud Integration** (General Concept)

This isn’t a specific AWS service but refers to **how AWS enables different services to communicate seamlessly**, often using:

- **Amazon EventBridge** (event bus)
- **Amazon SQS** (message queue)
- **Amazon SNS** (notifications)
- **API Gateway** (connect APIs)
- **Step Functions** (workflow orchestration)

▸ **Use Case**: Build **loosely coupled, scalable cloud applications** that communicate reliably.

---

### **64. Amazon SQS (Simple Queue Service)**

A **message queuing service** that allows **decoupling** of components in a cloud application.

#### ▸ Types:

- **Standard Queue** (default): High throughput, at-least-once delivery.
- **FIFO Queue**: Ensures messages are processed **once** and **in order**.

▸ **Use Case**: Enable **asynchronous communication** between microservices or serverless components (e.g., Lambda).

---

### **65. Amazon Kinesis**

A **real-time data streaming service** for collecting, processing, and analyzing data.

### ▸ Components:

- **Kinesis Data Streams**: Custom real-time stream processing.
- **Kinesis Data Firehose**: Load real-time data into S3, Redshift, etc.
- **Kinesis Analytics**: Run SQL on streaming data.

▸ **Use Case**: **Monitor clickstreams, IoT telemetry, or logs** in real-time and take action quickly.

---

### **66. Amazon SNS (Simple Notification Service)**

A **fully managed pub/sub messaging service** for sending notifications or alerts to subscribers.

#### ▸ Features:

- Supports multiple **protocols**: email, SMS, Lambda, HTTP, etc.
- **Topic-based messaging**: Publishers send messages to a topic, and all subscribers receive it.
- Used for **real-time push notifications**.

▸ **Use Case**: **Send alerts** (e.g., CloudWatch alarm to Ops team via email/SMS).

---

### **67. Amazon MQ**

A **managed message broker** service for applications that use **traditional messaging protocols** like **AMQP, MQTT, STOMP, OpenWire**.

#### ▸ Key Point:

- Supports **ActiveMQ** and **RabbitMQ** engines.
- Useful when **migrating legacy apps** that can’t use modern services like SQS or SNS.

▸ **Use Case**: Migrate enterprise apps that use **standard messaging protocols**.

---

### **68. AWS CloudTrail**

Records **API calls** and **user activity** across your AWS account for **audit and compliance**.

#### ▸ Tracks:

- Who did what, when, and from where (console, SDK, CLI).
- Supports **multi-region** and **organization-wide trails**.
- Integrates with **S3 (storage)** and **CloudWatch (monitoring)**.

▸ **Use Case**: **Track changes, troubleshoot issues**, or **prove compliance**.

---

### **69. AWS Organizations**

Used to **centrally manage and govern multiple AWS accounts**.

#### ▸ Key Features:

- Create **Organizational Units (OUs)**: Group accounts by team or purpose.
- Apply **Service Control Policies (SCPs)**: Restrict what services/accounts can do.
- **Consolidated Billing**: One bill for all accounts, plus shared volume discounts.

▸ **Use Case**: Manage **large-scale AWS usage** across departments or environments.

---

### **70. Multi-Account Strategies**

Refers to **best practices** in setting up **multiple AWS accounts** for security, cost control, and organization.

#### ▸ Strategy Examples:

- Use **separate accounts** for **dev, test, prod**.
- Apply **least privilege** via SCPs.
- Use **AWS Organizations** for structure, governance, and billing.

▸ **Use Case**: Isolate workloads, improve **security, billing visibility, and fault isolation**.

---

### **71. Service Control Policies (SCPs)**

A **feature of AWS Organizations** used to define **guardrails** for what **accounts and OUs** can and cannot do.

#### ▸ Key Points:

- SCPs don’t grant permissions; they **limit maximum permissions** available.
- Applied to **organizational units (OUs)** or individual accounts.
- Common use: **Prevent deleting critical resources**, or **deny regions or services**.

▸ **Use Case**: **Restrict services/actions across multiple accounts**.

---

### **72. AWS Control Tower**

A **setup-and-go** solution for quickly deploying a **secure multi-account AWS environment** using **best practices**.

#### ▸ What It Provides:

- Automated setup of **landing zones** (preconfigured accounts + OUs).
- Includes: AWS Organizations, SCPs, Config, CloudTrail, and Guardrails.
- Simplifies governance for **multi-account environments**.

▸ **Use Case**: Set up a **pre-configured, secure AWS environment** with governance built-in.

---

### **73. **AWS Resource Access Manager (RAM)\*\*

Lets you **share AWS resources across accounts** without copying them.

#### ▸ Shareable resources:

- VPC subnets
- Transit Gateways
- Route53 Resolver Rules
- License Manager configurations, etc.

▸ **Use Case**: Allow **multiple AWS accounts to use shared resources** (e.g., shared VPC).

---

### **74. AWS Service Catalog**

Allows organizations to **create and manage approved catalogs** of AWS resources (products).

#### ▸ What it does:

- Admins define **pre-approved templates** (CloudFormation stacks).
- Users (e.g., developers) can **launch resources without needing full access**.
- Helps maintain **compliance, security, and standardization**.

▸ **Use Case**: Enable self-service provisioning of **standardized infrastructure**.

---

### **75. AWS Pricing Models**

Understanding AWS pricing is **key for the exam**. Major pricing models include:

#### ▸ Compute (EC2, Lambda):

- **On-Demand**: Pay per second/minute. No commitment.
- **Reserved Instances**: Up to 75% discount for 1–3 year commitment.
- **Spot Instances**: Up to 90% discount. Can be interrupted.
- **Savings Plans**: Flexible discount model across instance families.

#### ▸ Storage (S3, EBS, Glacier):

- Charged by **GB stored**, **requests**, and **data transfer**.

#### ▸ Free Tier:

- Always Free: e.g., 25 GB DynamoDB, 1 million Lambda requests.
- 12-Month Free: e.g., 750 hours EC2 t2.micro.

▸ **Use Case**: Choose the right pricing model to **optimize cost** based on workload patterns.

---

### **76. AWS Compute Optimizer**

Uses **machine learning** to recommend optimal **compute resources** for your workload.

#### ▸ Key Features:

- Analyzes usage of **EC2, Lambda, EBS, and Auto Scaling groups**.
- Suggests instance types and sizes to reduce **underutilization or over-provisioning**.
- Recommendations based on **past 14 days** of usage.

▸ **Use Case**: **Optimize cost and performance** by right-sizing resources.

---

### **77. AWS Pricing Calculator**

A **free web-based tool** to **estimate costs** of AWS services before you use them.

#### ▸ Key Features:

- Supports pricing estimation for **EC2, S3, RDS, Lambda**, etc.
- Allows you to **customize usage patterns, region, storage, duration**.
- Output includes **detailed cost breakdowns** and **monthly estimates**.

▸ **Use Case**: **Forecast AWS spend** for budgeting or pre-project approval.

---

### **78. AWS Trusted Advisor**

A **management tool** that provides **real-time recommendations** for improving:

- **Security**
- **Cost optimization**
- **Performance**
- **Fault tolerance**
- **Service limits**

#### ▸ Tiers:

- **Basic (free)**: 7 core checks.
- **Full (Business/Enterprise support plan)**: All checks across 5 categories.

▸ **Use Case**: Proactive **best practice checks** to improve your AWS environment.

---

### **79. AWS Cost Explorer**

An **interactive tool** to **visualize, analyze, and forecast** AWS usage and spending.

#### ▸ Key Features:

- **Daily, monthly, or hourly spend breakdowns**
- **Filtering by service, region, linked account**
- Forecast **future usage** based on trends
- Works well with **Budgets, Tags, and Consolidated Billing**

▸ **Use Case**: **Track and control AWS costs**, especially in multi-account setups.

---

### **80. AWS Basic Support Plan** (Free)

#### ▸ Included by default:

- **24/7 access** to:

  - **AWS documentation**
  - **Whitepapers**
  - **AWS Trusted Advisor – 7 core checks**
  - **AWS Health Dashboard**

▸ **Use Case**: For **individuals and small teams** not needing direct support.

---

### **81. AWS Developer Support Plan** (\~\$29/month or 3% usage)

#### ▸ Features:

- **Business-hours email access** to Cloud Support Associates (unlimited cases).
- Response time:

  - **< 12 hrs** for general guidance
  - **< 24 hrs** for system impaired

- Access to best practices, SDKs, and forums.

▸ **Use Case**: For **development and testing** in non-production environments.

---

### ▸ 82. **AWS Business Support Plan** (\~\$100/month or 10%/7%/5% tiered pricing)

#### ▸ Features:

- 24/7 **phone, chat, and email support**
- Response time:

  - **< 1 hr** for production system down
  - **< 12 hrs** for production impaired

- Access to **full Trusted Advisor checks**
- Access to AWS **Support API**

▸ **Use Case**: For **production workloads** needing **faster support and guidance**.

---

### **83. AWS Enterprise On-Ramp Support Plan** (\~\$5,500/month+)

#### ▸ Features:

- Designed for **mid-sized or fast-growing businesses**.
- Includes everything in Business plan plus:

  - Access to **Technical Account Manager (TAM)**
  - **Monthly technical reviews**
  - **Proactive case management**

- Priority case handling and faster escalation.

▸ **Use Case**: For companies beginning to scale and needing **hands-on guidance**.

---

### **84. AWS Enterprise Support Plan** (starts at \~\$15,000/month+)

#### ▸ Features:

- Everything from On-Ramp plus:

  - **Designated Technical Account Manager (TAM)**
  - **24/7 white-glove support**
  - **Well-Architected Reviews**
  - Access to **Infrastructure Event Management (IEM)** for large launches
  - Concierge billing & account support

▸ **Use Case**: **Large-scale enterprises** with mission-critical apps on AWS needing **highest level of support**.

---

### **85. Docker**

A **platform** used to **build, package, and run applications in containers**.

#### ▸ Components:

- **Docker Containers**: Lightweight, portable, isolated environments to run apps.
- **Docker Hub**: Public repository to store and share container images.

▸ **Use Case**: Package an app and its dependencies into a **single container** for portability and consistency.

> _Docker is not AWS-specific_, but AWS services like ECS, EKS, and Fargate support Docker-based containers.

---

### **86. Amazon EKS (Elastic Kubernetes Service)**

A **managed Kubernetes** service that makes it easy to run Kubernetes clusters on AWS.

#### ▸ Key Benefits:

- AWS **manages the Kubernetes control plane** (secure, scalable).
- Integrates with **IAM, VPC, ALB, CloudWatch**.
- You deploy your Docker containers using **Kubernetes YAML files**.

▸ **Use Case**: Run **containerized microservices** using Kubernetes.

---

### **87. Amazon ECS (Elastic Container Service)**

A **fully managed container orchestration** service built by AWS.

#### ▸ Key Features:

- Run and scale **Docker containers**.
- **Launch types**:

  - **Fargate**: Serverless (no EC2 needed)
  - **EC2**: You manage the infrastructure

- Simple to use compared to EKS (no Kubernetes knowledge needed)

▸ **Use Case**: Deploy and manage containers **without Kubernetes complexity**.

---

### **88. Amazon ECR (Elastic Container Registry)**

A **fully managed Docker container registry** for storing and versioning container images.

#### ▸ Key Features:

- Works with **ECS, EKS, Fargate**.
- Private registry (unlike Docker Hub).
- Supports **image scanning** for security.

▸ **Use Case**: Store **container images** securely for use in ECS/EKS deployments.

---

### **89. Amazon API Gateway**

A **fully managed service** to create, publish, secure, and monitor **APIs at any scale**.

#### ▸ Key Features:

- Supports **REST, HTTP, and WebSocket APIs**
- Integrates with **Lambda**, **EC2**, **ECS**, **backend services**
- **Built-in throttling, authorization (IAM/Cognito), caching**

▸ **Use Case**: Build secure, scalable **APIs** for your application backend.

---

### **90. AWS Batch**

A **fully managed service for running batch computing workloads** on AWS.

#### ▸ Key Features:

- Dynamically provisions **compute resources**.
- Runs jobs on **EC2 or Fargate**, including Docker containers.
- Ideal for **scientific modeling, simulations, data transformation**.

▸ **Use Case**: Process large volumes of **batch jobs** like rendering or big data processing.

---

### **91. Databases on AWS**

AWS offers **fully managed** and **self-managed** database options for both **SQL (relational)** and **NoSQL (non-relational)** use cases.

#### ▸ Key Points:

- Managed services: **RDS, DynamoDB, Aurora**
- Self-managed: You install/manage databases on **EC2**
- Scalable, durable, with backups and high availability

▸ **Use Case**: Store and manage application data, user data, transactions, logs, etc.

---

### **92. NoSQL Databases**

NoSQL databases are designed for **unstructured, semi-structured**, or **rapidly changing** data, and they scale **horizontally**.

#### ▸ AWS Example:

- **Amazon DynamoDB** (fully managed NoSQL key-value store)

  - Microsecond latency
  - Serverless
  - Auto-scaling
  - Built-in security and backup

▸ **Use Case**: Real-time gaming, IoT, mobile apps, user sessions.

---

### **93. Amazon RDS (Relational Database Service)**

Fully managed **relational database service** for common engines:

> MySQL, PostgreSQL, MariaDB, Oracle, SQL Server, and Amazon Aurora

#### ▸ Key Features:

- Automated **backups**, **patching**, **failover**, **monitoring**
- **Multi-AZ deployment** for high availability
- **Read Replicas** for scalability
- **Encryption at rest & in transit**

▸ **Use Case**: Traditional applications needing ACID-compliant relational databases.

---

### **94. Amazon Aurora**

A **MySQL/PostgreSQL-compatible** RDS engine built by AWS — offers **performance & availability at 1/10th the cost** of enterprise DBs.

#### ▸ Key Features:

- 5x faster than MySQL, 3x faster than PostgreSQL
- **Auto-scaling storage**
- Up to **15 read replicas**
- Fault-tolerant and self-healing

▸ **Use Case**: Modern high-throughput apps needing **enterprise-grade relational DB** performance with full compatibility.

---

### **95. Read Replica (in RDS & Aurora)**

Creates **read-only copies** of a database to offload **read traffic** and improve scalability.

#### ▸ Key Points:

- Not used for **failover** (except in Aurora)
- Can create multiple replicas in same or different regions
- Replication is **asynchronous**

▸ **Use Case**: **High-traffic applications** with more reads than writes (e.g., analytics dashboards, reporting tools).

---

### **96. RDS Multi-Region Deployment**

#### ▸ What it is:

A setup where an RDS instance (usually **Read Replica**) is created in **another AWS region**.

#### ▸ Key Features:

- Provides **disaster recovery**, **data locality**, and **latency reduction**
- Not automatic failover (unless you use **Aurora Global Database**)

▸ **Use Case**: Mission-critical applications needing **geo-redundancy** or **faster global access** to relational DBs.

---

### **97. Amazon ElastiCache**

#### ▸ What it is:

A **fully managed in-memory cache** service for **speeding up data access**.

#### ▸ Supported Engines:

- **Redis**: Cache + pub/sub + streams + geospatial
- **Memcached**: Simple in-memory key-value store

#### ▸ Benefits:

- **Microsecond latency**
- Reduces load on primary DB (RDS or DynamoDB)

▸ **Use Case**: Caching frequently accessed data (e.g., sessions, product catalogs, leaderboards).

---

### **98. Amazon DynamoDB**

#### ▸ What it is:

A **NoSQL key-value and document database** with:

- **Serverless architecture**
- **Millisecond latency at scale**
- **Auto-scaling**, **on-demand mode**

#### ▸ Core Features:

- Point-in-time recovery
- Encryption at rest
- Backup & restore
- Global Tables
- Streams (change tracking)

▸ **Use Case**: IoT, mobile apps, gaming, shopping carts, user data.

---

### **99. DAX (DynamoDB Accelerator)**

#### ▸ What it is:

An **in-memory caching layer** for DynamoDB that **reduces read latency** from milliseconds → **microseconds**.

#### ▸ Key Features:

- Fully managed
- Write-through caching (DAX handles consistency)
- No code change to existing DynamoDB calls (uses DAX SDK)

▸ **Use Case**: **Read-heavy workloads** that need ultra-fast performance (e.g., recommendation engines).

---

### **100. DynamoDB Global Tables**

#### ▸ What it is:

A **multi-region, multi-active replication** setup for DynamoDB tables.

#### ▸ Key Features:

- **Active-active replication** (can write from multiple regions)
- Automatically replicates data across specified regions
- Ideal for high availability and low-latency access globally

▸ **Use Case**: Global applications requiring **real-time, multi-region writes** (e.g., collaborative apps, gaming).

---

### **101. Amazon Redshift**

#### ▸ What It Is:

A **fully managed data warehouse** service for **analytical querying (OLAP)** of petabyte-scale structured data.

#### ▸ Key Features:

- Uses **SQL-like queries**
- Columnar storage + compression = **fast performance**
- Integrates with **S3 (Spectrum), QuickSight, Glue**
- Redshift Serverless: No infrastructure to manage

▸ **Use Case**: Business Intelligence, dashboards, big data analytics.

---

### **102. Amazon EMR (Elastic MapReduce)**

#### ▸ What It Is:

A **big data platform** that runs open-source frameworks like **Apache Spark, Hadoop, Hive** on AWS.

#### ▸ Key Features:

- Run data processing jobs on **EC2 or Spot instances**
- Auto-scaling and optimized pricing
- Works with **S3, DynamoDB, Redshift**

▸ **Use Case**: Large-scale **data transformation**, **ETL**, **log analysis**, **machine learning preprocessing**.

---

### **103. Amazon Athena**

#### ▸ What It Is:

A **serverless query service** to analyze data directly in **Amazon S3 using SQL**.

#### ▸ Key Features:

- No infrastructure to manage
- Pay per query (based on data scanned)
- Integrated with **QuickSight**, **Glue Data Catalog**

▸ **Use Case**: Fast ad-hoc querying of S3-stored CSV, JSON, Parquet, etc., without loading into a database.

---

### **104. Amazon QuickSight**

#### ▸ What It Is:

A **business intelligence (BI) and data visualization** tool like Tableau or Power BI.

#### ▸ Key Features:

- Connects to **Redshift, Athena, S3, RDS**
- Supports **ML-powered insights** (AutoNarratives)
- Accessible via web browser or app

▸ **Use Case**: Creating **dashboards, KPIs, and reports** for decision-making across business teams.

---

### **105. Amazon DocumentDB (with MongoDB compatibility)**

#### ▸ What It Is:

A **fully managed document database** designed to store, query, and index **JSON-like data** (MongoDB compatible).

#### ▸ Key Features:

- Scalable, highly available, secure
- Used in apps that need flexible document structures
- Built for **semi-structured** data

▸ **Use Case**: Content management systems, catalogs, user profiles — anything needing a **document-style database**.

---

### **106. Amazon Neptune**

#### ▸ What It Is:

A **fully managed graph database** optimized for **connected data** and relationships.

#### ▸ Supported Graph Models:

- **Property Graph** (via Apache TinkerPop / Gremlin)
- **RDF / SPARQL** (semantic web queries)

#### ▸ Key Features:

- Low-latency performance for traversing millions of relationships
- Used for **social networks, recommendation engines, fraud detection**

▸ **Use Case**: Apps that need fast, complex relationship queries like **"friends of friends"**, or **knowledge graphs**.

---

### **107. Amazon Timestream**

#### ▸ What It Is:

A **serverless time series database** for IoT and operational applications.

#### ▸ Key Features:

- Optimized for **time-stamped data** (e.g., metrics, logs)
- Automatic storage tiering (recent = fast, old = cheap)
- Built-in **data lifecycle management**

▸ **Use Case**: **IoT sensor data**, **app performance metrics**, **log analytics**, **devops monitoring**.

---

### **108. Amazon Managed Blockchain**

#### ▸ What It Is:

A **fully managed service for creating and managing blockchain networks** using:

- **Hyperledger Fabric**
- **Ethereum (retired)**

#### ▸ Key Features:

- Decentralized ledger
- Tamper-proof transactions
- Access control for participants

▸ **Use Case**: **Supply chain**, **healthcare records**, **finance consortia** requiring transparency and trust.

---

### **109. AWS Glue**

#### ▸ What It Is:

A **fully managed ETL (Extract, Transform, Load)** service used to prepare and move data between sources and destinations.

#### ▸ Key Features:

- **Serverless** data integration
- Supports **PySpark** & **Python**
- Has a **Data Catalog**
- **Glue Studio**: No-code visual ETL builder

▸ **Use Case**: Clean, transform, and load data into **data lakes (S3)** or **data warehouses (Redshift)**.

---

### **110. AWS Amplify**

#### ▸ What It Is:

A platform to **build, host, and manage full-stack web and mobile apps** using AWS services (like Cognito, API Gateway, S3, Lambda, DynamoDB).

#### ▸ Key Features:

- Easy integration with **React, Angular, Vue, Flutter**
- Auto-deploy from GitHub/Bitbucket
- Authentication, storage, API, hosting — all managed

▸ **Use Case**: **Frontend/backend apps**, **JAMstack** apps, mobile backends.

---

### **111. AWS AppSync**

#### ▸ What It Is:

A **fully managed service for GraphQL APIs** that lets apps query data from multiple sources.

#### ▸ Key Features:

- Supports **GraphQL**, integrates with **Lambda, DynamoDB, RDS, OpenSearch**
- Real-time data via **subscriptions**
- Offline data sync for mobile apps

▸ **Use Case**: Unified APIs for mobile/web apps that pull from different AWS data sources.

---

### **112. AWS OpsWorks**

#### ▸ What It Is:

A **configuration management** service that uses **Chef and Puppet** to automate server setup, deployment, and management.

#### ▸ Key Features:

- Automates infrastructure as code
- Manages EC2 instances and on-prem servers
- Can configure EBS, Auto Scaling, and ELBs

▸ **Use Case**: Teams already using **Chef/Puppet** and need automated config management.

---

### **113. Amazon Cognito**

#### ▸ What It Is:

A service for **user authentication, authorization, and user management** in apps.

###$ ▸ Key Features:

- Sign-up, sign-in, password reset
- Social logins (Google, Facebook, Apple)
- Federated identity + SSO
- Token-based auth (OAuth2, OpenID Connect)

▸ **Use Case**: Web/mobile apps needing secure and scalable **user login systems** without building one from scratch.

---

### **114. AWS Cloud9**

#### ▸ What It Is:

A **browser-based IDE** for writing, running, and debugging code using just a browser.

#### ▸ Key Features:

- Pre-installed SDKs, CLI tools
- Collaborate in real-time
- Integrated terminal with AWS CLI
- No setup required — runs on EC2 or Lambda

▸ **Use Case**: Cloud-native development environment for **Python, Node.js, C++, etc.**, accessible from any device.

---

### **115. AWS CodeStar**

#### ▸ What It Is:

An **all-in-one development dashboard** that helps teams quickly start and manage full CI/CD projects.

#### ▸ Key Features:

- Templates for common app stacks (Node.js, Python, Java, etc.)
- Auto-integrates with **CodeCommit, CodePipeline, CodeDeploy**
- Centralized DevOps management

▸ **Use Case**: Teams looking to quickly spin up an **end-to-end CI/CD pipeline** with monitoring.

---

### **116. AWS IAM Access Analyzer**

#### ▸ What It Is:

A **security tool** that helps you **identify resources in your AWS account that are shared externally** (outside your org or publicly accessible).

#### ▸ Key Features:

- Works with IAM, S3, KMS, SQS, etc.
- Shows external access to roles, buckets, etc.
- Helps maintain **least-privilege access**

▸ **Use Case**: Security auditing to detect **unintended public exposure**.

---

### **117. Amazon QLDB (Quantum Ledger Database)**

#### ▸ What It Is:

A **ledger database** for applications that need an **immutable, cryptographically verifiable record of transactions**.

#### ▸ Key Features:

- Immutable and **append-only** (you can’t delete/change history)
- Verifiable with cryptographic hashes
- Fully managed

▸ **Use Case**: Financial, supply chain, or legal systems where **auditability** is required without using blockchain.

---

### **118. Amazon Lightsail**

#### ▸ What It Is:

A **simple VPS (Virtual Private Server)** service designed for **easy deployment of websites, blogs, and apps**.

#### ▸ Key Features:

- Pre-configured with WordPress, Node.js, LAMP, etc.
- Fixed pricing
- Built-in DNS, static IP, snapshots

▸ **Use Case**: Small businesses, students, or developers who need **a simpler alternative to EC2**.

---

### **119. Amazon Rekognition**

#### ▸ What It Is:

A **computer vision service** that uses AI to analyze **images and videos**.

#### ▸ Key Features:

- Face detection and recognition
- Object and scene detection
- Celebrity recognition, unsafe content detection

▸ **Use Case**: Security cams, facial access, content moderation, photo tagging.

---

### **120. Amazon Transcribe**

#### ▸ What It Is:

A **speech-to-text service** that uses AI to **convert audio to written text**.

#### ▸ Key Features:

- Real-time or batch transcription
- Speaker identification
- Custom vocabulary

▸ **Use Case**: Transcribe **customer calls**, **video subtitles**, or **voice-enabled apps**.

---

### **121. Amazon Polly**

#### ▸ What It Is:

A **Text-to-Speech (TTS)** service that converts written text into **lifelike spoken audio** using AI.

#### ▸ Key Features:

- Supports **multiple languages and voices**
- Offers **Neural TTS (NTTS)** for realistic voice output
- Allows speech synthesis to MP3, OGG, etc.

▸ **Use Case**: Voice assistants, reading apps, accessibility (screen readers), voice-enabled apps.

---

### **122. Amazon Translate**

#### ▸ What It Is:

A **real-time language translation service** powered by neural networks.

#### ▸ Key Features:

- Supports **100+ languages**
- Can translate plain text or HTML documents
- Scalable and secure — used in multilingual apps or sites

▸ **Use Case**: Real-time **language localization** for global web apps, chat systems, or documentation.

---

### **123. Amazon Lex & Amazon Connect**

#### ▸ **Amazon Lex**

- A service to **build conversational chatbots** using **voice and text**.
- Uses same deep learning as Alexa (speech recognition + NLU).
- Works with **Lambda**, **DynamoDB**, etc.

▸ Use Case: Build **AI chatbots** for support, sales, bookings, etc.

#### ▸ **Amazon Connect**

- A **cloud-based contact center** solution.
- Integrates with Lex, Lambda, and other AWS services.
- Automatically scales up/down with usage.

▸ Use Case: Run a **call center** with AI voice agents and customer support chatbots.

---

### **124. Amazon Comprehend**

#### ▸ What It Is:

A **natural language processing (NLP)** service that understands **text content**.

#### ▸ Key Features:

- Detects **sentiment**, **entities**, **key phrases**, **language**
- Topic modeling and document classification
- Works on structured or unstructured text

▸ **Use Case**: Analyze **customer feedback**, emails, social media, or support tickets.

---

### **125. Amazon SageMaker**

#### ▸ What It Is:

A **fully managed machine learning platform** to build, train, and deploy ML models at scale.

#### ▸ Key Features:

- Jupyter-based notebooks
- AutoML, built-in algorithms
- Real-time and batch inference
- MLOps support (monitoring, pipelines)

▸ **Use Case**: For **data scientists or ML engineers** building custom prediction models for fraud detection, recommendation engines, etc.

---

### **126. Amazon Kendra**

#### ▸ What It Is:

An **intelligent enterprise search service** powered by ML that helps users search **unstructured data** across multiple data sources.

#### ▸ Key Features:

- Connects to **SharePoint, S3, RDS, Salesforce, etc.**
- Understands **natural language queries**
- Delivers **contextual and ranked results**

▸ **Use Case**: Internal company knowledge base or documentation search.

---

### **127. Amazon Personalize**

#### ▸ What It Is:

A **real-time recommendation engine** service based on the tech used by Amazon.com.

#### ▸ Key Features:

- No ML expertise required
- Takes in user behavior (clicks, views, etc.)
- Outputs personalized **product, content, or search** recommendations

▸ **Use Case**: E-commerce sites, streaming platforms, or news apps.

---

### **128. Amazon Textract**

#### ▸ What It Is:

A **document AI service** that automatically extracts **text, tables, and forms** from scanned documents and PDFs.

#### ▸ Key Features:

- Detects printed and handwritten text
- Extracts **structured data** from invoices, IDs, etc.
- Integrates with **Comprehend** for document classification

▸ **Use Case**: Automate **form/data extraction** from scanned documents.

---

### **129. AWS Cost and Usage Reports (CUR)**

#### ▸ What It Is:

A detailed **CSV/Parquet report** that includes **hourly, daily, or monthly cost and usage data** for your AWS services.

#### ▸ Key Features:

- Delivered to S3
- Can be analyzed with **Athena, Redshift, QuickSight**
- Used for **cost allocation, chargeback, or trend analysis**

▸ **Use Case**: Deep dive into **billing and usage metrics**.

---

### **130. AWS Budgets**

#### ▸ What It Is:

A cost management tool to **set custom budgets** and receive **alerts** when you're forecasted to exceed them.

#### ▸ Key Features:

- Monitor **cost, usage, RI & Savings Plan coverage**
- Alerts via **email or SNS**
- Tracks by **service, account, or tag**

▸ **Use Case**: Enforce **spending limits** or notify stakeholders.

---

### **131. Amazon API Gateway**

#### ▸ What It Is:

A fully managed service for creating, publishing, monitoring, and securing **RESTful or WebSocket APIs**.

#### ▸ Key Features:

- Fronts **Lambda, EC2, any backend**
- Handles **rate limiting, caching, auth (Cognito/IAM)**
- Scales automatically

▸ **Use Case**: Build **serverless APIs** (especially for mobile/web apps) easily.

---
