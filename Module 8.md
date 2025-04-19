
# Module 8 - Databases


## Objectives / Topics

- Explain Amazon Relational Database Service (Amazon RDS)
- Identify the functionality in Amazon RDS
- Explain Amazon DynamoDB
- Identify the functionality in Amazon DynamoDB
- Explain Amazon Redshift
- Explain Amazon Aurora
- Perform tasks in an RDS database, such as launching, configuring, and interacting

1. **Unmanaged services** like Amazon EC2 give users full control over configuration and behavior, but require manual setup for scaling, fault-tolerance, and handling errors or load changes—offering flexibility at the cost of more management.

2. **Managed services** like Amazon S3 simplify operations by automatically handling aspects like scaling and availability, requiring minimal configuration from the user, though offering less fine-tuned control.

## Section 1: Amazon Relational Database Service (RDS)

Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while automating time-consuming administration tasks such as hardware provisioning, database setup, patching and backups. RDS provides you with six familiar database engines to choose from: Amazon Aurora, Oracle, Microsoft SQL Server, PostgreSQL, MySQL and MariaDB.

### **Managed vs Unmanaged Service**

Unmanaged Challenges

- Server maintenance and energy footprint
- Software installation and patches
- Database backups and high availability
- Limits on scalability
- Data security
- Operating system (OS) installation and patches

RDS is a managed service that sets up and operates a relational database in the cloud. AWS Manages:

You manage:
- Applicationoptimization
AWS manage
- OS installation and patches
- Database software installation and patches
- Database backups
- High availability
- Scaling
- Power and racking and stacking servers
- Server maintenance

### **RDS Features**

- Step-by-step explanation of the Amazon RDS process:

1. **Create a Database Instance** – This is the core unit of Amazon RDS and acts as an isolated environment for your databases.

2. **Choose a Database Engine** – Select from supported engines: MySQL, Amazon Aurora, SQL Server, PostgreSQL, MariaDB, or Oracle.

3. **Select Instance Class** – Decide the compute and memory capacity based on your performance needs.

4. **Pick Storage Type** – Choose disk types (e.g., SSD or magnetic) that match your performance and budget requirements.

5. **Launch and Connect** – Once created, access your database using standard tools just like any standalone database.

6. **Customize for Cost & Performance** – Adjust instance class and storage to optimize based on your specific workload and budget.

### Amazon RDS in a virtual private cloud (VPC)

1. **Amazon RDS can run within an Amazon Virtual Private Cloud (VPC)**, allowing you to fully control your virtual network environment—including IP address ranges, subnets, routing tables, and access control lists (ACLs).

2. **The core functionality of Amazon RDS remains the same whether or not it’s in a VPC**, but using a VPC provides greater network isolation and security.

3. **Database instances are typically placed in private subnets** to restrict direct access; only specified application instances can communicate with them.

4. **Each subnet in a VPC is tied to a single Availability Zone**, so by choosing a subnet for your database instance, you also define the physical location (Availability Zone) where it will be hosted.

5. **Amazon RDS Multi-AZ deployment** enhances high availability by automatically creating a synchronized standby copy in a different Availability Zone, protecting against instance failure, zone disruptions, and supporting maintenance operations.
6. In a Multi-AZ deployment, if the primary database instance fails, Amazon RDS automatically promotes the standby instance with minimal data loss and no changes needed in application code, thanks to the use of a consistent DNS endpoint.

### Amazon RDS read replicas

1. **Asynchronous Replication**: Amazon RDS supports read replicas for MySQL, MariaDB, PostgreSQL, and Aurora, where updates from the primary are copied asynchronously.

2. **Improved Performance & Scalability**: Read replicas help offload read traffic from the primary database and support scaling for read-heavy workloads.

3. **Cross-Region & Manual Promotion**: Replicas can be created in different Regions for disaster recovery or lower latency and can be manually promoted to a primary if needed.
### **Cost and Usage of RDS**


#### When to use RDS

Use when you require:

- Complex transactions or complex queries
- A medium to high query or write rate – Up to 30,000 IOPS (15,000 reads + 15,000 writes)
- No more than a single worker node or shard
- High durability

Do not use when:

- Massive read/write rates (for example, 150,000 write/second)
- Sharding due to high data size or throughput demands
- Simple GET or PUT requests and queries that a NoSQL database can handle
- Relational database management system (RDBMS) customization

#### Billing

Multiple factors influence the cost of RDS

---

### **No Additional Charge**:
1. **Inbound Data Transfer** – No charge for data coming into Amazon RDS.
2. **Backup Storage (for active DB)** – Free backup storage up to 100% of the provisioned DB storage size, as long as the DB instance is active.

---

### **Charged Items**:
1. **Clock Hour Billing** – Charges apply for resources while they are running, calculated by the hour.
2. **Database Characteristics** – Type and size of DB engine affect cost.
3. **DB Purchase Type**:
   - **On-Demand Instances** – Charged by the hour for compute capacity.
   - **Reserved Instances** – One-time upfront payment for 1-year or 3-year reserved term.
4. **Number of DB Instances** – Each additional instance incurs charges.
5. **Provisioned Storage** – Standard storage charges apply for allocated DB storage.
6. **Backup Storage (for terminated DBs)** – Charged per GB/month after DB termination.
7. **Additional Backup Storage** – Any backup storage beyond the free limit is charged per GB/month.
8. **Number of Requests** – Higher volume may increase cost.
9. **Deployment Type** – Storage and I/O charges vary based on single-AZ or multi-AZ deployment.
10. **Outbound Data Transfer** – Tiered charges apply for data transferred out of RDS.


<br/>

## Section 2: Amazon DynamoDB

- Fast and flexible NoSQL database service for any scale.
- NoSQL database tables with no limits
- Flexible Data Structure: You can store different types of items (e.g., products, users, orders) in one table without needing a fixed schema.
- Virtually unlimited storage
- Items can have differing attributes
- Data stored in solid state drive(SSD)
- Low-latency queries
- Scalable read/write throughput with no limits
- Supports document and key-value store models.
- Replicates your tables automatically across your choice of AWS Regions
- Works well for mobile, web, gaming, adtech, and Internet of Things (IoT) applications
- Provides consistent, single-digit millisecond latency at any scale
- TTL (Time to Live) in Amazon DynamoDB is a feature that automatically deletes expired items from a table after a specified timestamp.

### Amazon DynamoDB core component
Tables, items, and attributes are the core DynamoDB components.

- A table is a collection of data.
- Items are a group of attributes that is uniquely identifiable among all the other items
- Attributes are a fundamental data element, something that does not need to be broken down any further
### Two different kinds of primary keys
- Simple Primery Key(Partition key)
- Composite Primery Key(Partition key + sort key)

<br/>

## Section 3: Amazon Redshift

[Amazon Redshift](https://aws.amazon.com/redshift/) is a fully managed, petabyte-scale data warehouse service in the cloud. The Redshift service manages all of the work of setting up, operating, and scaling a data warehouse. These tasks include provisioning capacity, monitoring and backing up the cluster, and applying patches and upgrades to the Amazon Redshift engine.

- Columnar storage and parallel processing architectures
- Automatically and continuously monitors cluster
- Encryption is built in
- Amazon Redshift supports standard SQL.
- Also provide high performance java database connectivity/open database connectivity.
- Softwareasaservice(SaaS)
- Use case- Enterprise data warehouse, Big data centers.
---
### Leader Node:
1. Communicates with client applications.
2. Parses complex queries and creates execution plans.
3. Compiles query code and assigns tasks to compute nodes.
4. Aggregates intermediate results from compute nodes to produce the final result.
---

### Compute Nodes:
1. Receive and execute compiled code from the leader node.
2. Perform the assigned operations (like filtering, joins, etc.).
3. Send intermediate results back to the leader node for final processing.

<br/>

## Section 4: Amazon Aurora

[Amazon Aurora](https://aws.amazon.com/rds/aurora/) 
- It is a MySQL and PostgreSQL-compatible relational database built for the cloud.
- Combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases. 
- Aurora features a distributed, fault-tolerant, self-healing storage system that auto-scales up to 64 TB per database instance.
- It delivers high performance and availability with up to 15 low-latency read replicas, point-in-time recovery, continuous backup to Amazon S3, and replication across three Availability Zones (AZs). 
- It also automates time-consuming tasks such as provisioning, patching, backup, recovery, failure detection, and repair.
- Pay as you go.
- It’s a managed service that integrates with features such as AWSDatabase Migration Service (AWS DMS)and the AWS Schema Conversion Tool.

1. **Faster Recovery**: Amazon Aurora reduces restart time after a crash (usually under 60 seconds) by avoiding redo log replay during recovery and instead performing it on individual read operations.

2. **Instant Buffer Cache Access**: Aurora keeps the buffer cache outside the database process, making it immediately available after restart and reducing the risk of performance drops ("brownouts").

<br/>

---

<br/>

