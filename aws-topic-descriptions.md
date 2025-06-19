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

