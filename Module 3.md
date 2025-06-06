# AWS Global infrastructure Overview

### AWS Region:- 22 regions(2019).

An AWS Region is a geographical area.

- Data replication across Regions is controlled by you.
- Communication between Regions uses AWS backbone network infrastructure.
- Each Region provides full redundancy and connectivity to the network.
- A Region typically consists of two or more Availability Zones(data centers)
- AWS regions before march 20th 2019 are enable by default.
- Any region added after that you need to be enabled by yourself. [Like Hongkong(APAC), Beruit(Middle East)]
- We can use AWS management console to enable or disbale the regions.
- Restricted region- China
- Isolated region- USA Gov.

When selecting a region consider the following:

- Laws - Data governance and legal requirements
- Proximity - Select regions close to your customers for reduced latency. (To Test use CloudPing tool)
- Availability - Some services are region locked
- Cost - Cost varies by region
Note- All AWS services are not avalaible in all regions.

#### Availability Zone:
- Eah region has multiple availability zones(Typically 3)
- Each Availability Zone is a fully isolated partition of the AWS infrastructure. There are currently 69 Availability Zones worldwide.
- Availability Zones consist of discrete data centers
- They are interconnected with other Availability Zones by using high-speed private networking
- They are designed for fault isolation
- You choose your Availability Zones but AWS recommends replicating data and resources across Availability Zones for resiliency.
 <image src= "C:\Users\User\Desktop\Repo\AWS_Cloud_Foundations\Images\Availability Zones.jpg">


### **AWS Data Centers**(3 in each availability zone)

- AWS data centers are designed for security. 
- Each data center has redundant power
- Networking, and connectivity, and is housed in a separate facility.
- Data centers are where the data resides and data processing occurs. A data center typically has 50,000 to 80,000 physical servers
- In case of failure of data center traffic is moved from efeected area to different location automatically.

 #### **Point of Presence**(Present in around 30 countries)
- AWS provides a global network of 187 Points of Presence locations:
- Consists of 176 edge locations - where end users access services located at AWS
- 11 Regional edge caches - cache copies of your infrequent content close to your users
- Used with **Amazon CloudFront** -  a fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment.
- Regional Edge caches used for content with infrequent access.

**CLoud Front** Is a content delivery network(CDN) used to distribute content to end user to reduce latency.

**Amazon Route 53** Is a domain name system(DNS) service where request going to either one of these services will be routed to nearest edge location automatically in order to lower latency.
- To reduce latency and increase availability and customer experince many AWS services are used. Like Amazon CloudFront, Amazon route53, AWS Shield and AWS web application API.
- Regional Edge caches are used by default with Amazon Cloud Front.

AWS Infrastructure Features:

1. Elasticity and scalability - dynamically adapts to capacity and growth needs
2. Fault-tolerance - Continues operating properly in the presence of a failure due to built-in redundancy of components
3. High availability - High operational performance with minimized downtime and no human intervention

<br/>

## Section 2: AWS Services and Service Category Overview

### **Infrasture services**
- Regions
- Availability zones
- Point of Presence, Edge Locations

These services provide a broad foundation services

### **Foundation Services**

- Compute
- Networking
- Storage

### Plateform services
- Database 
    - Relational
    - NoSQl
    - Caching

- Analytics
    - Cluster Computing 
    - Real-time Data work flows 
    - Data warehouse

- Application Services
    - Queuing
    - Orchestration
    - App Streaming
    - Transcoding 
    - Email Search

- Deploment and Management
    -  Containers
    - DevOps tools
    - Resource templates
    - Usage tracking
    - Monitoring and logs
   

- Mobile services
    - IdentitySync
    - Mobile Analytics
    - Notification

### Application
- Virtual Desktop 
- Collaborartion and sharing

### **Service Categories**

23 different product or service categories, and each category consists of one or more services. The course covers the most common categories and the ones likely to be on the foundations exam.


### **Service Categories**

23 different product or service categories, and each category consists of one or more services. The course covers the most common categories and the ones likely to be on the foundations exam.

#### AWS Storage Services

- [Amazon Simple Storage Services (S3)](https://aws.amazon.com/s3/) - is an object storage service that offers scalability, data availability, security, and performance. Use it to store and protect any amount of data for websites, mobile apps, backup and restore, archive, enterprise applications, Internet of Things (IoT) devices, and big data analytics.
- [Amazon Elastic Block Storage (EBS)](https://aws.amazon.com/ebs) - is high-performance block storage that is designed for use with Amazon EC2 for both throughput and transaction intensive workloads. It is used for a broad range of workloads, such as relational and non-relational databases, enterprise applications, containerized applications, big data analytics engines, file systems, and media workflows
- [Amazon Elastic File System (EFS)](https://aws.amazon.com/efs/) - A simple, scalable, fully managed elastic NFS file system for use with AWS Cloud services and on-premises resources.  It is built to scale on demand to petabytes, growing and shrinking automatically as you add and remove files. It reduces the need to provision and manage capacity to accommodate growth. 
- [Amazon Simple Storage Service Glacier](https://aws.amazon.com/glacier/) - A secure, durable, and extremely low-cost Amazon S3 cloud storage classes for data archiving and long-term backup.
It is designed to deliver high durability, and to provide comprehensive security and compliance capabilities to meet stringent regulatory requirements.

#### AWS Compute Services

- [Amazon EC2](https://aws.amazon.com/ec2/) - A web service that provides secure, resizable compute capacity in the cloud.
- [Amazon EC2 Auto Scaling](https://aws.amazon.com/ec2/autoscaling/) - Helps to maintain application availability and allows you to automatically add or remove EC2 instances according to conditions you define.
- [Amazon Elastic Container Services (ECS)](https://aws.amazon.com/ecs/) - A fully managed container orchestration service.
- [Amazon EC2 Container Registry (ECR)](https://aws.amazon.com/ecr/) -  A fully-managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images.
- [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/) - An easy-to-use service for deploying and scaling web applications and services developed with Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker on familiar servers such as Apache, Nginx, Passenger, and IIS.
- [AWS Lambda](https://aws.amazon.com/lambda/) - Lets you run code without provisioning or managing servers.
- [Amazon Elastic Kubernetes Services (EKS)](https://aws.amazon.com/eks/) - A fully managed [Kubernetes](https://en.wikipedia.org/wiki/Kubernetes) service.
- [AWS Fargate](https://aws.amazon.com/fargate/) - A serverless compute engine for containers that works with both Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS).

#### AWS Database Services

- [Amazon Relational Database Service (RDS)](https://aws.amazon.com/rds/) - Makes it easy to set up, operate, and scale a relational database in the cloud.
- [Amazon Aurora](https://aws.amazon.com/rds/aurora/) - A MySQL and PostgreSQL compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases.
- [Amazon Redshift](https://aws.amazon.com/redshift/) - A fully managed, petabyte-scale data warehouse service in the cloud.
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb/) - A key value and document database that delivers single-digit millisecond performance at any scale.

#### Networking and Content Delivery Services

- [Amazon VPC](https://aws.amazon.com/vpc/) - Lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.
- [Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing/) - Automatically distributes incoming application traffic across multiple targets, such as Amazon EC2 instances, containers, IP addresses, and Lambda functions.
- [Amazon CloudFront](https://aws.amazon.com/cloudfront/) - A fast content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency, high transfer speeds, all within a developer-friendly environment.
- [AWS Transit Gateway](https://aws.amazon.com/transit-gateway/) - A service that enables customers to connect their Amazon Virtual Private Clouds (VPCs) and their on-premises networks to a single gateway.
- [Amazon Route 53](https://aws.amazon.com/route53/) - A highly available and scalable cloud Domain Name System (DNS) web service.
- [AWS Direct Connect](https://aws.amazon.com/directconnect/) - A cloud service solution that makes it easy to establish a dedicated network connection from your premises to AWS.
- [AWS VPN](https://aws.amazon.com/vpn/) - Lets you establish a secure and private encrypted tunnel from your network or device to the AWS global network.

#### Security, Identity, and Compliance Services

- [AWS Identity and Access Management (IAM)](https://aws.amazon.com/iam/) -  Enables you to manage access to AWS services and resources securely. You can create and manage AWS users and groups, and use permissions to allow and deny their access to AWS resources. IAM is a feature of your AWS account offered at no additional charge.
- [AWS Organizations](https://aws.amazon.com/organizations/) - helps you centrally govern your environment as you grow and scale your workloads on AWS.
- [Amazon Cognito](https://aws.amazon.com/cognito/) - Lets you add user sign-up, sign-in, and access control to your web and mobile apps quickly and easily.
- [AWS Artifact](https://aws.amazon.com/artifact/) - A central resource for compliance related information that matters to you.
- [AWS Key Management Service (KMS)](https://aws.amazon.com/kms/) - Makes it easy for you to create and manage cryptographic keys and control their use across a wide range of AWS services and in your applications.
- [AWS Shield](https://aws.amazon.com/shield/) - A managed Distributed Denial of Service (DDoS) protection service that safeguards applications running on AWS.

#### Cost Management Services

- [AWS Cost and Usage Report](https://aws.amazon.com/aws-cost-management/aws-cost-and-usage-reporting/) - contains the most comprehensive set of AWS cost and usage data available, including additional metadata about AWS services, pricing, and reservations (e.g., Amazon EC2 Reserved Instances (RIs)).
- [AWS Budgets](https://aws.amazon.com/aws-cost-management/aws-budgets/) - gives you the ability to set custom budgets that alert you when your costs or usage exceed (or are forecasted to exceed) your budgeted amount.
- [AWS Cost Explorer](https://aws.amazon.com/aws-cost-management/aws-cost-explorer/) - an easy-to-use interface that lets you visualize, understand, and manage your AWS costs and usage over time.

#### AWS Management and Governance Services

- [AWS Management Console](https://aws.amazon.com/console/) - A secure, easy-to-access, web-based portal for AWS.
- [AWS Config](https://aws.amazon.com/config/) - A service that enables you to assess, audit, and evaluate the configurations of your AWS resources.
- [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) - A monitoring and observability service that provides you with data and actionable insights to monitor your applications, respond to system-wide performance changes, optimize resource utilization, and get a unified view of operational health. You can use it to detect anomalous behavior in your environments, set alarms, visualize logs and metrics side by side, take automated actions, troubleshoot issues, and discover insights.
- [AWS Auto Scaling](https://aws.amazon.com/autoscaling/) - monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost.
- [AWS Command Line Interface (CLI)](https://aws.amazon.com/cli/) -  a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.
- [AWS Trusted Advisor](https://aws.amazon.com/premiumsupport/technology/trusted-advisor/) - An online tool that provides you real time guidance to help you provision your resources following AWS best practices.
- [AWS Well-Architected Tool](https://aws.amazon.com/well-architected-tool/) - Helps you review the state of your workloads and compares them to the latest AWS architectural best practices.
- [AWS CloudTrail](https://aws.amazon.com/cloudtrail/) - A service that enables governance, compliance, operational auditing, and risk auditing of your AWS account.

<br/>

---

<br/>
