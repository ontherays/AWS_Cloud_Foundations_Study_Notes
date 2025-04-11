# Module 7 - Storage


Storage is another AWS core service category. Some broad categories of storage include: instance store (ephemeral storage), Amazon EBS, Amazon EFS, Amazon S3, and Amazon S3 Glacier.
- **Instance store**, or ephemeral storage, istemporary storagethat is added to your Amazon EC2 instance.
- **Amazon EBS** is persistent, mountable storage that can be mounted as a device to an Amazon EC2 instance. Amazon EBS can be mounted to an Amazon EC2 instance only within the same Availability Zone. Only one Amazon EC2 instance at a time can mount an Amazon EBS volume.
- **Amazon EFS** is a shared file system that multiple Amazon EC2 instances can mount at the same time. 
- **Amazon S3** is persistent storage where each file becomes an object and is available through a Uniform Resource Locator (URL); it can be accessed from anywhere.
- **Amazon S3 Glacier** is for cold storage for data that is not accessed frequently (for example, when you need long-term data storage for archival or compliance reasons).


## Objectives / Topics

- Identify the different types of storage
- Explain Amazon S3
- Identify the functionality in Amazon S3
- Explain Amazon EBS
- Identify the functionality in Amazon EBS
- Perform functions in Amazon EBS to build an Amazon EC2 storage solution
- Explain Amazon EFS
- Identify the functionality in Amazon EFS
- Explain Amazon S3 Glacier
- Identify the functionality in Amazon S3 Glacier
- Differentiate between Amazon EBS, Amazon S3, Amazon EFS, and Amazon S3 Glacier


<br/>

## Section 1: Amazon Elastic Block Store (EBS)

Amazon [Elastic Block Store](https://aws.amazon.com/ebs/?ebs-whats-new.sort-by=item.additionalFields.postDateTime&ebs-whats-new.sort-order=desc) (EBS) is an easy to use, high performance [block storage](https://en.wikipedia.org/wiki/Block_(data_storage)) service designed for use with Amazon Elastic Compute Cloud (EC2) for both throughput and transaction intensive workloads at any scale.

With **block storage**, files are split into evenly sized blocks of data, each with its own address but with no additional information (metadata) to provide more context for what that block of data is. **Object storage**, by contrast, doesn’t split files up into raw blocks of data. Instead, entire clumps of data are stored in, yes, an object that contains the data, metadata, and the unique identifier. With block storage you can update a single block without having to update the entire file like in object storage.

Amazon EBS enables you to create individual storage volumes and attach them to an Amazon EC2 instance:

- Offers block-level storage
- HDD and SSD available
- Volumes are automatically replicated within its Availability Zone
- It can be backed up automatically to Amazon S3 through snapshots
- Designed for resiliency - Annual Failure Rate (AFR) is between 0.1% and 1%
- Uses include:
  - Boot volumes and storage for (Amazon EC2) instances
  - Data storage with a file system
  - Database hosts
  - Enterprise applications

- Amazon EBS volumes persist independently from the running life of an EC2 instance.

### **EBS Features and Charges**

Snapshots
- A backup of an Amazon EBS volume is called a snapsho
- Baseline Snapshot- The first snapshot.
- Point-in-time images
- Recreate a new volume at any time
- Added cost of Amazon EBS snapshots to Amazon S3 is per GB-month of data stored
- Only SSDs can be used as boot volumes for EC2 instances
- IOPS- inpout/output operation per second.

Encryption

- Encrypted Amazon EBS volumes
- No additional cost

Elasticity

- Increase capacity
- Change to different types

Volumes

- Amazon EBS volumes persist independently from the instance
- All volume types are charged by the amount that is provisioned per month.

IOPS (Input/Output Operations Per Second)

- General Purpose SSD: Charged by the amount that you provision in GB per month until storage is released
- Magnetic: Charged by the number of requests to the volum
- Provisioned IOPS SSD: Charged by the amount that you provision in IOPS (multiplied by the percentage of days that you provision for the month).

Data transfer

- Inbound data transfer is free
- Outbound data transfer across Regions incurs charges

### Charge
- Volumes: Amazon EBS volumes are independent of EC2 instances and are charged based on the amount provisioned per month.
- General Purpose SSD: Charged by the amount provisioned in GB per month.
- Magnetic: Charged by the number of requests made to the volume.
- Provisioned IOPS SSD: Charged by the amount of IOPS provisioned, multiplied by the percentage of days provisioned for the month.
- Snapshots – Added cost of Amazon EBS snapshots per GB.
- Data transfer – Inbound data transfer is free. Outbound data transfer across Regions incurs charges. 




<br/>

## Section 2: Amazon Simple Storage Service (S3)

[Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/s3/) is an object storage service that offers scalability, data availability, security, and performance. Amazon S3 offers a range of object-level storage classes that are designed for different use cases.
- Bucket names are universal and must be unique across all existing bucket names in Amazon S3.
- S3 stores data as object in a resource called bucket.
- Virtually unlimited storage but a single object is limited to 5 TB.
- database snapshots can also be stored.
- Designed for [11 9s of durability](https://wasabi.com/blog/11-nines-durability/)
- Granular access to bucket and objects.
- Data is redundantly stored in the Region.
- Data can be access via http/htpps/VPC/web-based AWS Management Consol/ Third party API,SDk.
- Access Control data by using AWS Identity and Access Management (IAM) policies, Amazon S3 bucket policies, and even per-object access control lists.
- Amazon S3 includes event notification, Those notifications can be sent to you or trigger other processes like AWS Lambda functions.
- Data can be accessed via AWS Management Console, AWS Command Line Interface, or the SDK.
- **Amazon QuickSight** Dat can be export to an Amazon S3 bucket to analyze by using the business intelligence (BI) tools of your choice, such as Amazon QuickSight.

### S3 Storage type 

1. **Amazon S3 Standard**: Ideal for frequently accessed data, offering high durability, low latency, and high throughput. Commonly used for web apps, mobile apps, content delivery, and big data analytics.

2. **Amazon S3 Intelligent-Tiering**: Automatically moves data between frequent and infrequent access tiers based on usage patterns to optimize cost, with no performance impact or retrieval fees.

3. **Amazon S3 Standard-IA**: Designed for infrequently accessed data that still needs fast retrieval. Offers lower storage costs than S3 Standard, with a retrieval fee. Best for backups and disaster recovery.

4. **Amazon S3 One Zone-IA**: Similar to Standard-IA but stores data in a single Availability Zone, reducing cost. Suitable for secondary backups or recreatable data.

5. **Amazon S3 Glacier**: Low-cost, secure storage for archiving data with flexible retrieval times (minutes to hours). Good for long-term storage needs.

6. **Amazon S3 Glacier Deep Archive**: The lowest-cost option, ideal for long-term retention (7–10+ years). Data is stored across 3+ Availability Zones and can be restored within 12 hours. Suitable for compliance and tape storage replacement.

Common Use Cases and Scenarios

- Storing application assets
- Static web hosting
- Backup and disaster recovery(DR)
- Staging area for big data
- Application hosting
- Media hosting
- Software delivery

### S3 Bucket URL Type
- To upload your data: 1.Create a bucketin an AWS Region.2.Upload almost any number of objectsto the bucket.
- 1- Bucket path-style URL endpoint.
  - https://s3.ap-northeast-1.amazonaws.com/bucket-name
- 2- Bucket virtual hosted-style URL endpoint.
  - https://bucket-name.s3-ap-northeast-1.amazonaws.com

### **S3 Pricing**

Pay only for what you use

- GBs per month
- Transfer OUT to other Regions
- PUT, COPY, POST, LIST, and GET requests

You do not pay for

- Transfers IN to Amazon S3
- Transfers OUT from Amazon S3 to Amazon CloudFront or Amazon EC2 in the same Region

### Estimate Cost
1.Storage class type 
2- Amount of storage
3- Request - GET, PUT, COPY (GET charge is different than other requests)
4- Data Transfer- In free, Also free for Transfers OUT from Amazon S3 to Amazon CloudFront or Amazon EC2 in the same Region.
- Tranfer OUT to other region is chargeable.

#### Estimating S3 Pricing

1. Storage class type
   - Standard storage is designed for: 11 9s of durability and four 9s of availability
   - S3 Standard-Infrequent Access (S-IA) is designed for 11 9s of durability and three 9s of availability
2. Amount of storage
3. Requests
   - The number and type of requests (GET, PUT, COPY)
   - Type of requests: Different rates for GET requests than other requests.
4. Data transfer
   - Pricing is based on the amount of data that is transferred out of the Amazon S3 Region

<br/>

## Section 3: Amazon Elastic File System

[Amazon Elastic File System (Amazon EFS)](https://aws.amazon.com/efs/) provides a simple, scalable, fully managed elastic NFS file system for use with AWS Cloud services and on-premises resources. It is built to scale on demand to petabytes without disrupting applications, growing and shrinking automatically as you add and remove files, eliminating the need to provision and manage capacity to accommodate growth.
- It can attach to multiple EC2 instances as the same time. It a shared file system that uses **Network file System**.

### **EFS Features**

- File storage in the AWS Cloud
- Works well for big data and analytics, media processing workflows, content management, web serving, and home directories
- Petabyte-scale, low-latency file system
- Shared storage
- Elastic capacity
- file system interface - An EC2 instance can access file thorugh this API. These file systems support full file system access semantics, such as strong consistency and file locking.
- Supports Network File System (NFS) versions 4.0 and 4.1 (NFSv4)
- Compatible with all Linux-based AMIs for Amazon EC2
- Can be mounted on VPC.
- Pay for what you use, No setup cost.
- access the EFS from a mount target within the same Availability Zone.
- One availability zone should have only one mount target(Network Interface) to access EFS.

### **EFS Implementation**

1. Create your Amazon EC2 resources and launch your instance.
2. Create your Amazon EFS file system.
3. In the appropriate subnets, create your mount targets.
4. Next, connect to your Amazon EC2 instance and mount the Amazon EFS file system.
5. Finally, clean up your resources and protect your AWS account.

### EFS resources

**EFS properties:**
 ID, Creation token, Creation time, File system size in bytes, Number of mount targets that are created for the file system, File system state. 

**Mount Target Properties**
ID,The subnet ID, The file system ID for the file system where it was created, An IP address where the file system can be mounted, The mount target state.

- Use Tags to identify you can assign your own metadata.

<br/>

## Section 4: Amazon S3 Glacier

[Amazon S3 Glacier](https://aws.amazon.com/glacier/) is a data archiving service that is designed for security, durability, and an extremely low cost.

- Amazon S3 Glacier is designed to provide 11 9s of durability for objects
- It supports the encryption of data in transit and at rest through Secure Sockets Layer (SSL) or Transport Layer Security (TLS)
- The [Vault Lock](https://docs.aws.amazon.com/amazonglacier/latest/dev/vault-lock.html) feature enforces compliance through a policy
- Extremely low-cost design works well for long-term archiving. Pricing is varied on region, and where the data is being sent.
- You can configure lifecycle archiving of Amazon S3 content to Amazon S3 Glacier. Lifecycle policies enable you to delete or move objects based on age.

1. **Archive** – The basic storage unit in Amazon S3 Glacier (e.g., file, photo, video), each with a unique ID.  
2. **Vault** – A container that stores archives; created with a name and AWS Region.  
3. **Vault Access Policy** – Controls who can access the vault and what actions they can perform; includes access and lock policies.

- Retrieval options:
  - Standard: 3–5 hours
  - Bulk: 5–12 hours
  - Expedited: 1–5 minutes

  ### S3 Glacier Management
  - Storing. and access data can be manage from AWS management Console.
  - creating and deleting vaults, Creating and managing archieve policy can be manage from AWS management Console. For other operation use Amazon S3 Glacier REST APIs, the AWS Java or .NET SDKs, or the AWS CLI.

  ### Lifecycle Ploicy

  - You should automate the lifecycle of the data that you store in Amazon S3.

- Secure Storage
- SSE-S3 – Amazon S3 manages encryption with unique object keys and AES-256; keys are encrypted and rotated automatically.
- SSE-C – You provide your own encryption keys; Amazon S3 handles the encryption and decryption during storage and access.
- SSE-KMS – Uses AWS Key Management Service and Customer Master Keys for encryption, with detailed control, auditing, and centralized key management.

  - Control access with IAM
  - Manages your keys

<br/>

---


