# Descriptions:

### **1. IAM User**

* **IAM (Identity and Access Management)** is used to manage access to AWS services.
* An **IAM user** is an identity created for a person or application.
* Each user has **credentials (username/password or access keys)** and **permissions (via policies)**.
* Best practice: **Use IAM users, not root**, and give **least privilege access**.

---

### **2. Amazon S3 (Simple Storage Service)**

Object storage service for any type of data.

#### ▸ **Versioning**

* Stores **multiple versions** of an object.
* Useful for **data recovery** or rollback.
* Once enabled on a bucket, it **cannot be disabled**, only suspended.

#### ▸ **Replication**

* Automatically copies objects across **buckets in same or different AWS Regions**.
* Two types:

  * **SRR**: Same Region Replication
  * **CRR**: Cross Region Replication (disaster recovery)

#### ▸ **Objects**

* Basic unit of storage in S3.
* Each object = data + metadata + unique key.
* Stored in **buckets**.

#### ▸ **Policy Attach**

* Attach **bucket policies** or **IAM policies** to control access.
* Bucket policies are **resource-based**, while IAM policies are **identity-based**.

#### ▸ **Static Website Hosting**

* You can **host a static website** (HTML, CSS, JS) directly from an S3 bucket.
* Requires enabling **public access**, specifying **index and error documents**.

#### ▸ **Cross Region Replication**

* Automatically replicates objects from one AWS Region to another.
* Must enable **versioning** on both source and destination buckets.
* Useful for **high availability** and **disaster recovery**.

#### ▸ **Event Configuration**

* Configure S3 to trigger **events** (like object upload/delete) to services like:

  * **Lambda**
  * **SNS**
  * **SQS**
* Enables **serverless workflows**, e.g., process files as they're uploaded.

---

### **3. AWS Snowball**

* **Physical device** for moving large volumes of data to/from AWS.
* Use case: when data transfer over the internet is **too slow or expensive**.
* Variants:

  * **Snowball Edge Storage Optimized**
  * **Snowball Edge Compute Optimized**
* Part of **AWS Snow Family** (includes Snowmobile and Snowcone).

---

### **4. AWS Lambda**

* **Serverless compute**: Run code without provisioning servers.
* Triggered by **events** (S3 upload, API Gateway, DynamoDB streams, etc.)
* Pay only for **compute time** used (in milliseconds).
* Supports many languages: Python, Node.js, Java, etc.

---

### **5. Amazon EC2 (Elastic Compute Cloud)**

* Virtual servers in the cloud.
* You choose instance type, OS, network, storage, etc.

#### ▸ **Outbound & Inbound Rules**

* Defined in **security groups**.
* Inbound: controls **incoming traffic** (e.g., allow port 80 for HTTP).
* Outbound: controls **outgoing traffic** from instance.

#### ▸ **Storage Types**

* **EBS (Elastic Block Store)**: Persistent block storage. Remains after instance termination.
* **EFS (Elastic File System)**: Shared file storage across instances.
* **Instance Store**: Temporary storage attached to an instance. **Data lost when stopped**.

#### ▸ **Snapshots**

* **Backups** of EBS volumes.
* Stored in **Amazon S3** (but not accessible as objects).
* Used to **create new volumes or AMIs**.

#### ▸ **Security Group**

* Acts as a **virtual firewall** for your EC2 instances.
* Controls **traffic rules** (inbound & outbound).
* **Stateful**: return traffic is automatically allowed.

#### ▸ **Instance Pricing**

* **On-Demand**: Pay per hour/second.
* **Reserved**: 1- or 3-year commitment for significant discount.
* **Spot**: Bid for unused capacity at discount.
* **Savings Plans**: Flexible pricing model for long-term use.

#### ▸ **Web Server**

* EC2 can be used to host web servers like **Apache**, **Nginx**.
* Often used with **Elastic IP**, **Auto Scaling**, and **Load Balancer**.

#### ▸ **AMI Creation**

* AMI (Amazon Machine Image) is a **template** to launch EC2 instances.
* Includes OS, application server, and applications.
* You can **create custom AMIs** from existing instances.

#### ▸ **Instance Store**

* **Temporary block-level storage**.
* High speed, but **data lost** when instance is stopped, terminated, or crashes.
* Useful for temporary caching, buffers.

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

* **Layer 7 (HTTP/HTTPS)** aware.
* Supports **host-based and path-based routing**.
* Used for web applications, REST APIs, microservices.
* Integrates with **WAF**, **SSL termination**, and **container-based apps**.

#### ▸ **Network Load Balancer (NLB)**

* **Layer 4 (TCP/UDP)** load balancing.
* Handles **high-performance** and **low-latency** traffic.
* Used for applications requiring **static IPs** and high throughput.
* Scales to **millions of requests per second**.

---

### **10. Auto Scaling Group (ASG)**

Automatically adds or removes **EC2 instances** based on **demand** or **defined conditions** (like CPU usage or time schedules).

#### ▸ Key Features:

* Ensures **availability and cost-efficiency**.
* Works with **CloudWatch alarms** for dynamic scaling.
* Can be used with **ALB** to distribute traffic to new instances.
* Defines:

  * **Min**, **Max**, and **Desired** number of instances.
  * **Scaling policies** (manual, scheduled, or dynamic).

#### ▸ Benefits:

* **Resilience**: Replaces unhealthy instances.
* **Cost-effective**: Scales out/in based on need.

---

### **11. AWS VPC (Virtual Private Cloud)**

A **VPC** is your own **isolated network** within AWS where you can launch AWS resources (e.g., EC2, RDS).

#### ▸ **Public Subnet**

* **Accessible from the internet**.
* Typically hosts **web servers**, **ALBs**, etc.
* Requires:

  * **Internet Gateway**
  * **Route table entry to Internet Gateway**

#### ▸ **Private Subnet**

* **No direct internet access**.
* Used for **databases**, **backend servers**, etc.
* Can **access internet** using a **NAT Gateway** (for updates or outbound traffic).

#### ▸ **Route Table**

* Controls **network traffic routing**.
* Each subnet must be associated with a **route table**.
* Routes specify where traffic is sent (e.g., to Internet Gateway, NAT, VPC Peering).

---

### **12. Internet Gateway (IGW)**

* A **managed gateway** that connects your **VPC to the internet**.
* Required for **outbound and inbound** internet access to/from **public subnets**.
* Must be **attached to the VPC** and **used in route tables**.

---

### **13. NAT Gateway (Network Address Translation)**

* Enables instances in a **private subnet** to **access the internet** for things like OS updates or downloading packages.
* **Prevents internet-initiated inbound traffic** (i.e., maintains privacy).
* Must be placed in a **public subnet**.
* **Paid AWS managed service**, scales automatically.

---

### **14. VPC Advanced Features**

#### ▸ **Flow Logs**

* Captures **network traffic metadata** for:

  * Security analysis
  * Troubleshooting
  * Compliance
* Logs stored in **CloudWatch** or **S3**.

#### ▸ **VPC Peering**

* Connects **two VPCs** to communicate **privately** using **AWS backbone**.
* Peered VPCs can be in **same or different regions/accounts**.
* **No transitive peering**: VPC A ↔ VPC B ↔ VPC C does NOT mean A ↔ C.

#### ▸ **VPC Endpoints**

* Allow **private connection** to AWS services (e.g., S3, DynamoDB) **without using the internet**.
* Two types:

  * **Interface endpoint**: Powered by **ENI (Elastic Network Interface)**.
  * **Gateway endpoint**: Used for **S3 & DynamoDB**.

---

### **15. Elastic IP**

* A **static, public IPv4 address** that you can assign to an EC2 instance.
* Useful when you need a **fixed IP** for external access.
* Can **reassociate** it if an instance is stopped or terminated.
* **Limited by default**, charges apply if **not in use**.

---

### **16. AWS PrivateLink**

* Allows you to **privately access services** hosted in **another VPC** or **AWS service** using **private IPs**.
* Uses **interface VPC endpoints** (powered by ENIs).
* Traffic **stays within the AWS network**, not over the public internet.
* Common use: Accessing services like **S3**, **SNS**, or **3rd-party SaaS apps** securely.

▸ **Key Benefit**: **Secure**, **private**, and **scalable** connectivity to services **without exposing traffic to the internet**.

---

### **17. Site-to-Site VPN & AWS Direct Connect**

#### ▸ **Site-to-Site VPN**

* Creates a **secure encrypted tunnel** between **your on-premises network** and **AWS VPC** over the **public internet**.
* Uses **IPSec**.
* Easy to set up and **cost-effective**, but may have **latency** or **bandwidth fluctuations**.

#### ▸ **AWS Direct Connect**

* Provides a **dedicated physical connection** from your on-premises data center to AWS.
* **More reliable**, **lower latency**, and **higher bandwidth** than VPN.
* Used when you need **stable, consistent network performance** (e.g., for large data transfers, hybrid cloud setups).

---

### **18. AWS Client VPN**

* A **managed VPN service** that allows **remote users (e.g., employees)** to securely connect to AWS or on-premises networks.
* **OpenVPN-based** and supports **multi-factor authentication (MFA)**.
* Scales automatically and supports **access from laptops, desktops, etc.**

▸ Think: **Site-to-Site = office to AWS**,
**Client VPN = remote worker to AWS**.

---

### **19. AWS Transit Gateway**

* A **central hub** to connect **multiple VPCs**, **on-prem networks**, and **VPNs**.
* Replaces the need for **complex VPC peering** (which is 1-to-1).
* Uses a **hub-and-spoke** model.
* Simplifies **routing**, **security**, and **management** across large architectures.

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

* Uses a **global network of edge locations** (200+ worldwide).
* Reduces **latency** and **server load**.
* Integrates with **S3**, **ALB**, **EC2**, and **Route 53**.
* Supports **HTTPS**, **Geo-restriction**, and **DDoS protection** via AWS Shield.

▸ **Use case**: Serving static assets for websites, streaming video, securing APIs.

---

### **22. Amazon Route 53**

A **scalable and highly available Domain Name System (DNS)** web service.

#### ▸ Key Functions:

* **Domain Registration**: Buy and manage domain names (e.g., `example.com`).
* **DNS Resolution**: Converts domain names into IP addresses.
* **Health Checks**: Route traffic only to healthy resources.
* **Routing Policies**:

  * **Simple routing**
  * **Failover routing**
  * **Latency-based routing**
  * **Geolocation routing**
  * **Weighted routing**

▸ **Use case**: Directing user traffic to the nearest or healthiest AWS resource (e.g., EC2 or ALB).

---

### **23. AWS CloudFormation**

A service that helps you **automate infrastructure deployment** using **code (Infrastructure as Code – IaC)**.

#### ▸ How it works:

* You define resources (EC2, S3, IAM, etc.) in a **YAML/JSON template**.
* CloudFormation creates and manages them automatically.

▸ **Key Benefits**:

* **Repeatability**: Same setup in dev/test/prod.
* **Automation**: No manual provisioning.
* **Rollback support**: Automatically reverts on failure.

---

### **24. AWS Cloud Development Kit (CDK)**

A **software development framework** to define AWS infrastructure using **programming languages** like **Python, TypeScript, Java, or C#**.

#### ▸ Key Differences from CloudFormation:

* CDK is **code-first**, CloudFormation is **declarative**.
* CDK synthesizes into a CloudFormation template under the hood.
* Great for **developers comfortable with code**, supports abstraction and reuse.

▸ **Use case**: Automating infrastructure with real programming logic and reusable constructs.

---

### **25. Amazon ElastiCache**

A **fully managed in-memory data store** that boosts application performance by **caching frequently accessed data**.

#### ▸ Two Engine Options:

* **Redis**: Supports advanced data structures, pub/sub, backups.
* **Memcached**: Simple and fast caching engine.

#### ▸ Benefits:

* **Low latency** data access (microseconds).
* Reduces **load on databases**.
* Supports **real-time apps**, leaderboards, session stores, etc.

▸ **Use case**: Caching frequent queries, speeding up web apps, offloading DBs.

---

### **26. AWS Elastic Beanstalk**

A **Platform-as-a-Service (PaaS)** that lets you **deploy web applications** without managing servers, networking, or infrastructure.

#### ▸ Key Features:

* Supports **Java, Python, Node.js, PHP, .NET, Go, Ruby**, and Docker.
* You just upload your code — AWS handles provisioning:

  * EC2, ELB, Auto Scaling, RDS, etc.
* You can still **access the infrastructure** (like EC2) if needed.

▸ **Use case**: Quickly deploy a web app with minimal configuration.

---

### **27. AWS CodeDeploy**

A **deployment automation tool** that helps you **deploy code to EC2, Lambda, or on-prem servers** safely and consistently.

#### ▸ Features:

* Supports **rolling updates**, **blue/green deployments**, and **canary releases**.
* Minimizes **downtime** and supports **automatic rollback** if something fails.
* Tracks **deployment status** and logs.

▸ **Use case**: Automated code rollout to your servers or serverless apps.

---

### **28. AWS CodeCommit**

A **fully managed Git-based source code repository** similar to GitHub or GitLab.

#### ▸ Key Points:

* **Secure** (integrates with IAM).
* No size limits on repos or files.
* Code is stored **privately in AWS**.

▸ **Use case**: Store source code, track versions, and collaborate with your team on AWS.

---

### **29. AWS CodeBuild**

A **build service** that compiles source code, runs tests, and produces artifacts.

#### ▸ How it fits in DevOps:

* Runs as part of CI/CD pipeline.
* You define **build commands** in a `buildspec.yml` file.
* Scales automatically and **charges by the minute**.

▸ **Use case**: Compile code, run tests, and package the app automatically after every change.

---

### **30. AWS CodePipeline**

A **CI/CD service** to **automate the full software release process**.

#### ▸ Key Concepts:

* Connects **CodeCommit** → **CodeBuild** → **CodeDeploy** into stages.
* Automatically runs each stage on code change.
* Supports integration with **GitHub, Jenkins**, third-party tools.

▸ **Use case**: Automate and visualize your app release pipeline from source to deployment.

---

### **31. AWS CodeArtifact**

A **fully managed software artifact repository** for storing packages (dependencies) used in development.

#### ▸ Supports:

* **Maven, npm, PyPI, NuGet** (JavaScript, Python, Java, .NET)
* Integrates with **CodeBuild**, **CodePipeline**

▸ **Use Case**: Share and manage **build dependencies** across teams or projects securely.

---

### **32. AWS Systems Manager (SSM)**

A **central management service** for AWS infrastructure — think of it as a *Swiss Army knife* for system admins.

#### ▸ Key Features:

* **Session Manager**: Secure shell access (SSH-less) to EC2.
* **Run Command**: Execute shell commands across multiple EC2 instances.
* **Patch Manager**: Automate OS patching.
* **Parameter Store**: Securely store configuration variables like API keys.

▸ **Use Case**: Operate, secure, and automate large-scale EC2 and hybrid environments.

---

### **33. S3 Transfer Acceleration**

Speeds up **uploading large files to S3 buckets** over long distances using Amazon's **global edge network**.

#### ▸ How it works:

* Users upload to a **nearby AWS edge location** (like CloudFront).
* Data is then transferred quickly through AWS’s **backbone network** to your S3 bucket.

▸ **Use Case**: Upload files from far-away locations (e.g., from India to a US S3 bucket) **faster** than regular internet uploads.

---

### **34. AWS Global Accelerator**

Improves **performance and availability** of global applications by **routing traffic through the AWS global network**.

#### ▸ Features:

* Uses **static IPs** that route users to the **optimal AWS endpoint**.
* Unlike CloudFront (which caches content), Global Accelerator accelerates **non-cacheable, dynamic content** (like APIs).

▸ **Use Case**: Real-time applications (like gaming, streaming, APIs) that need **global, low-latency access**.

---

### **35. AWS Outposts**

Brings **AWS infrastructure and services to your on-premises** data center.

#### ▸ What It Does:

* You run AWS services **locally** while staying connected to the **AWS cloud**.
* Supports services like EC2, EBS, RDS, S3, and ECS locally.

▸ **Use Case**: Companies needing **low latency**, **data residency**, or operating in areas with **limited AWS region access**.

---

### **36. AWS Wavelength**

Brings **AWS services to telecom 5G networks** for **ultra-low-latency** applications.

#### ▸ Key Points:

* Deployed in **Wavelength Zones** inside **telecom provider data centers**.
* Ideal for apps like **AR/VR, IoT, video streaming, real-time gaming**.
* Keeps traffic closer to end users, bypassing long internet routes.

▸ **Use case**: Deliver **real-time services over 5G** with extremely low latency (single-digit milliseconds).

---

### **37. AWS Local Zones**

AWS infrastructure that brings **compute, storage, database** services **closer to large population centers**.

#### ▸ Key Points:

* Extends AWS regions to **cities where there's no full region**.
* Reduces **latency** for end-users in metros like Los Angeles, Mumbai, etc.
* You can run services like **EC2, EBS, ELB, RDS, ECS** locally.

▸ **Use case**: Latency-sensitive workloads (like video editing, gaming) in cities **far from existing AWS regions**.

---

### **38. AWS Shared Responsibility Model**

Explains **who is responsible** for what in AWS: **AWS vs. YOU (the customer)**.

#### ▸ AWS is responsible for:

* **Security “of” the cloud**: physical infrastructure, networking, hardware, managed services (like RDS platform).

#### ▸ Customer is responsible for:

* **Security “in” the cloud**: your data, access controls, OS patching (for EC2), configuration, IAM, etc.

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

* Built-in protections with **Route 53, CloudFront, ELB**.
* Using **scalable and redundant infrastructure** to absorb traffic.
* Integrating services like **AWS Shield** and **WAF (Web App Firewall)**.

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

* Stateful firewall rules to allow/block **IP addresses, ports, protocols**.
* Deep packet inspection (DPI).
* Protects **VPCs** from common threats like **port scanning, malware, and exploits**.
* Integrates with **VPC route tables** and **subnets**.

▸ **Use Case**: Add **advanced traffic filtering** for VPCs in sensitive workloads (e.g., finance, healthcare).

---

### **42. AWS Firewall Manager**

A **centralized security management service** for managing **firewall rules across multiple AWS accounts**.

#### ▸ Manages:

* **AWS WAF** (Web Application Firewall)
* **Shield Advanced**
* **VPC Network Firewall**
* **Security Groups**

▸ **Use Case**: Enterprises using **AWS Organizations** to apply consistent firewall/security policies across multiple accounts and regions.

---

### **43. Penetration Testing on AWS Cloud**

AWS **allows penetration testing** (ethical hacking) on **certain approved services** without prior approval.

#### ▸ Allowed Services (no approval needed):

* EC2, RDS, CloudFront, Aurora, API Gateway, Lambda, etc.

#### ▸ Rules:

* Must **not impact other AWS customers**.
* Must follow AWS's **[Penetration Testing Policy](https://aws.amazon.com/security/penetration-testing/)**.
* Some types of tests (e.g., DDoS, port flooding) **are NOT allowed** without special permission.

▸ **Use Case**: Customers wanting to **test their own cloud infrastructure’s security**.

---

### **44. AWS KMS (Key Management Service)**

A **secure, managed encryption key service** for creating and controlling encryption keys.

#### ▸ Key Features:

* Generates **Customer Master Keys (CMKs)**.
* Supports **encryption at rest** for services like S3, EBS, RDS, etc.
* Integrates with **CloudTrail** for audit logging.
* Keys can be **customer-managed** or **AWS-managed**.

▸ **Use Case**: Encrypting sensitive data and controlling who can decrypt it using **IAM + KMS** permissions.

---

### **45. AWS CloudTrail**

A **logging service** that records **all account-level activity** and API calls made in your AWS environment.

#### ▸ Tracks:

* **Who did what**, when, and from where.
* Actions taken via **AWS Console, CLI, SDKs, and APIs**.
* Stored in **S3** and can be analyzed in **CloudWatch or Athena**.

▸ **Use Case**: **Security auditing**, **compliance**, **incident response**, and **troubleshooting**.

---

### **46. AWS Certificate Manager (ACM)**

Manages **SSL/TLS certificates** to enable secure HTTPS connections to your websites or applications.

#### ▸ Key Features:

* **Provision, manage, and renew** certificates automatically.
* Use with services like **Elastic Load Balancer, CloudFront, API Gateway**.
* No manual steps for validation or renewal (for ACM-provided certs).

▸ **Use Case**: Secure websites or APIs with **free, auto-renewing SSL certificates**.

---

### **47. AWS Secrets Manager**

A **secure store** for managing **secrets** like API keys, database credentials, and tokens.

#### ▸ Key Features:

* Automatically **rotates secrets** (e.g., DB passwords).
* **Encrypts secrets** using AWS KMS.
* Fine-grained access control via **IAM**.
* Logs secret access with **CloudTrail**.

▸ **Use Case**: Securely store and rotate app credentials or tokens.

---

### **48. AWS Artifact**

Provides **on-demand access to AWS compliance reports** and **agreements**.

#### ▸ Includes:

* SOC 1, SOC 2, PCI, ISO, GDPR compliance docs.
* **NDA-based access** to AWS audit documentation.
* Reports are downloadable and updated regularly.

▸ **Use Case**: Organizations needing to **verify AWS compliance** for legal/regulatory needs.

---

### **49. Amazon GuardDuty**

An **intelligent threat detection** service that monitors AWS accounts for **malicious activity**.

#### ▸ Detects:

* Unusual login attempts.
* Compromised IAM users or EC2 instances.
* Reconnaissance (e.g., port scanning).
* Uses **machine learning** and **threat intel feeds**.

▸ **Use Case**: Automatically monitor for **suspicious behavior** without installing anything.

---

### **50. Amazon Inspector**

Automatically **scans AWS workloads** for **vulnerabilities** and **security issues**.

#### ▸ Scans:

* EC2 instances for **CVEs (Common Vulnerabilities and Exposures)**.
* Lambda functions for **code flaws**.
* **ECR (container images)** for known risks.

▸ **Use Case**: Continuous **security assessment** of EC2, Lambda, and containers.

---

### **51. AWS Config**

Tracks **configuration changes** in your AWS resources and ensures they **comply with rules** you define.

#### ▸ What it does:

* Continuously **monitors and records** resource configuration changes.
* Shows how a resource **was configured at any point in time**.
* Checks **compliance** (e.g., S3 buckets must be private).

▸ **Use Case**: **Audit trail + compliance checking** for your infrastructure.

---

### **52. Amazon Macie**

A **data security and privacy service** that uses **ML** to discover and protect **sensitive data** in **S3**.

#### ▸ What it does:

* Automatically finds **PII** (names, addresses, credit card info, etc.).
* Flags **unprotected or publicly exposed** data.
* Provides dashboards for **data classification**.

▸ **Use Case**: **Protect personal and sensitive data** stored in S3.

---

### **53. AWS Security Hub**

A **centralized dashboard** for managing and prioritizing **security alerts** from various AWS services.

#### ▸ Integrates with:

* **GuardDuty, Macie, Inspector, Firewall Manager**, and third-party tools.
* Aggregates findings and **ranks by severity**.
* Helps meet compliance frameworks like **CIS AWS Foundations**.

▸ **Use Case**: One place to **view, analyze, and act on security alerts**.

---

### **54. Amazon Detective**

Helps **investigate and analyze suspicious activity** in your AWS accounts using data from **CloudTrail, GuardDuty, and VPC Flow Logs**.

#### ▸ What it does:

* Automatically collects and links events.
* Builds **visual timelines and graphs** to show what happened.
* Useful during **security incident investigations**.

▸ **Use Case**: Dig deeper into “what happened” after a **security alert** is triggered.

---

### **55. AWS Abuse**

A **reporting system** for notifying AWS if **someone is using AWS resources maliciously**.

#### ▸ Used when:

* You see spam, phishing, port scanning, DDoS originating from AWS IPs.
* **Not for reporting issues with your own AWS account**.
* Report via: [aws.amazon.com/forms/report-abuse](https://aws.amazon.com/forms/report-abuse)

▸ **Use Case**: **Report misuse** of AWS resources by others (e.g., suspicious traffic from EC2 instance not owned by you).

---

### **56. IAM Access Analyzer**

Helps you **identify resources in your AWS account that are accessible publicly or from other accounts**.

#### ▸ What it does:

* Analyzes **S3 buckets, IAM roles, KMS keys, Lambda functions**, etc.
* Alerts you if a resource is **shared with external accounts or made public**.
* Works **automatically** and shows findings in IAM or via AWS CLI.

▸ **Use Case**: **Detect accidental public access** to sensitive AWS resources.

---

### **57. AWS CloudWatch Metrics**

Part of **Amazon CloudWatch** — tracks **performance metrics** for AWS services and custom applications.

#### ▸ Examples:

* **EC2**: CPU utilization, disk I/O, network usage.
* **RDS**: DB connections, read/write throughput.
* **Custom metrics**: App-level stats like user counts or transaction speeds.

▸ **Use Case**: **Monitor AWS services** and get alerts when usage crosses thresholds.

---

### **58. CloudWatch Logs**

Lets you **collect, monitor, and store logs** from AWS services and your applications.

#### ▸ Examples:

* **Lambda function output logs**
* **EC2 system logs**
* **Application logs**

#### ▸ Features:

* Can set up **log-based alarms**
* Integrates with **CloudWatch Insights** for log analysis

▸ **Use Case**: **Store and analyze logs** for troubleshooting and audits.

---

### **59. Amazon EventBridge**

*(Previously CloudWatch Events)*

A **serverless event bus** that connects AWS services with your own apps, based on **events and rules**.

#### ▸ Key Uses:

* **Trigger Lambda functions** when new S3 objects are uploaded.
* Send events from **SaaS apps (like Zendesk, Auth0)** to AWS.
* **Automated workflows** based on AWS service events.

▸ **Use Case**: **Event-driven automation** between services and apps.

---

### **60. AWS X-Ray**

A **distributed tracing tool** for debugging and analyzing **microservices and serverless applications**.

#### ▸ What it shows:

* Latency across services (e.g., API Gateway → Lambda → DynamoDB)
* Service maps with bottlenecks highlighted
* Errors and performance traces

▸ **Use Case**: **Troubleshoot slow or error-prone APIs** and pinpoint performance issues.

---

