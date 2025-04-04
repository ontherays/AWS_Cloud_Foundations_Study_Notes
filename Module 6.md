# Module 6 - Compute


## Objectives / Topics

- Provide an overview of different AWS compute services in the cloud
- Demonstrate why to use Amazon Elastic Compute Cloud (Amazon EC2)
- Identify the functionality in the EC2 console•Perform basic functions in Amazon EC2 to build a virtual computing environment
- Identify Amazon EC2 cost optimization elements
- Demonstrate when to use AWS Elastic Beanstalk
- Demonstrate when to use AWS Lambda
- Identify how to run containerized applications in a cluster of managed servers

<br/>

## Labs / Activities

<br/>

## Section 1: Compute Services Overview

AWS offers many compute services

- **Amazon Elastic Compute Cloud (Amazon EC2) :** provides resizable virtual machines.
- **Amazon EC2 Auto Scaling:** supports application availability by allowing you to define conditions that will automatically launch or terminate EC2 instances.
- **Amazon Elastic Container Registry (Amazon ECR):** is used to store and retrieve Docker images. 
- **Amazon Elastic Container Service (Amazon ECS):** is a container orchestration service that supports Docker
- **VMware Cloud on AWS :** enables you to provision a hybrid cloud without custom hardware.
- **AWS Elastic Beanstalk :** provides a simple way to run and manage web applications.
- **AWS Lambda:** is a serverless compute solution. You pay only for the compute time that you use.
- **Amazon Elastic Kubernetes Service (Amazon EKS):** enables you to run managed Kubernetes on AWS.
- **Amazon Lightsail:** provides a simple-to-use service for building an application or website.
- **AWS Batch:** provides a tool for running batch jobs at any scale.
- **AWS Fargate:** provides a way to run containers that reduce the need for you to manage servers or clusters.
- **AWS Outposts:** provides a way to run select AWS services in your on-premises data center.
- **AWS Serverless Application Repository:** provides a way to discover, deploy, and publish serverless applications

### Categorizing compute services

| Services       | Key Concepts | Characteristics      |  Ease of Use |
|--------------|--------|----------------------------------------------------------------------|--------------|
| •Amazon EC2 | •Infrastructure as a service (IaaS)•Instance-based•Virtual machines   | •Provision virtual machines that you can manage as you choose.                |  A familiar concept to many IT professionals.     |
| •AWS Lambda | •Serverlesscomputing•Function-based •Low-cost    | •Write and deploy code that runs on a schedule or that can be triggered by events•Use when possible (architect for the cloud)         |  A relatively new concept for many IT staff members, but easy to use after you learn how.     |
| •Amazon ECS •Amazon EKS •AWS Fargate •Amazon ECR | •Container-basedcomputing•Instance-based     | •Spin up and run jobs more quickly                |   AWS Fargate reduces administrative overhead, but you can use options that give you more control    |
| •AWS Elastic Beanstalk | •Platform as a service (PaaS)•For web applications      | •Focus on your code (building your application)•Can easily tie into other services—databases, Domain Name System (DNS), etc.                |   Fast and easy to get started.AWS Training and Certification  |
    

The optimal compute service or services that you use will depend on your use case, some aspects to consider:

- What is your application design?
- What are your usage patterns?
- Which configuration settings will you want to manage?

<br/>

## Section 2: Amazon Elastic Compute Cloud (EC2)

### **Overview**

- Provides virtual machines — referred to as EC2 instances — in the cloud
- Gives you full control over the guest operating system (Windows or Linux) on each instance
- You can launch instances of any size into an Availability Zone anywhere in the world with just a few clicks or a line of code, and they are ready in minutes
- Resizable compute capacity
- You can launch instances from Amazon Machine Images (AMIs)
- You can control traffic to and from instances using security groups.
- Provides tools to build failure resilient applications and isolate them from common failure scenarios
- 

### **Launching an EC2 Instance**

- First time you launch an Amazon EC2 instance, you will likely use the AWS Management Console _Launch Instance Wizard_.

These are the nine key decisions to make when you create an EC2 instance by using the AWS Management Console Launch Instance Wizard.

1. Select Amazon Machine Image (AMI)
   - Is a template that is used to create an EC2 instance (a virtual machine)
   - Contains a Windows or Linux operating system and often has some software pre-installed
   - AMI choices:
     - Quick Start – Linux and Windows AMIs that are provided by AWS
     - My AMIs – Any AMIs that you created
     - AWS Marketplace – Pre-configured templates from third parties
     - Community AMIs – AMIs shared by others; use at your own risk
     - You can Create EC2 instance from Quick Start or My AMIs and then after configuration according to your need you can turn/capture modified EC2 instances into AMIs templet. 
2. Select an Instance Type
   - Optimized to fit different use cases
   - The instance type that you choose determines
     - Memory (RAM)
     - Processing power (CPU)
     - Disk space and disk type (Storage)
     - Network performance
   - Instance type categories
     - General purpose
     - Compute optimized
     - Memory optimized
     - Storage optimized
     - Accelerated computing
   - Instance types offer family, generation, and size (Example - `t3.large`: Family - `T`, Generation - `3`, Size - `large`)
   - T3 instances provide burstable performance general purpose instances.
   - C5 instances are optimized for compute-intensive workloads.
   - R5instances are optimized for memory-intensive applications.
   - Networking Features
     - The network bandwidth (Gbps) varies by instance type.
     - To maximize networking and bandwidth performance of your instance type enable enhanced networking and if you have interdependent instances, launch them into a cluster placement group.
     - Enhanced networking types are supported on most instance types. Enhanced networking types:
       - Elastic Network Adapter (ENA): Supports network speeds of up to 100 Gbps.
       - Intel 82599 Virtual Function interface: Supports network speeds of up to 10 Gbps.
       - **Network performance level** Each instance type provides a documented network performance level. For example, an a1.medium instance will provide up to 10 Gbps, but a p3dn.24xlarge instance provides up to 100 Gbps. Choose an instance type that meets your requirements.
    
3. Specify Network Settings
   - The choice of Region must be made before you start the Launch Instance Wizard.
   - Where should the instance be deployed? Identify the VPC and optionally the subnet
   - Should a public IP addressbe automatically assigned?
   - You can have multiple networks, such as different ones for development, testing and production
   - If you dont specify VPC and subnet it goes to default VPC and Public subnet with as public ip address assigned.
   - By default, AWS will not assign a public IP address to instances that are launched in a non default subnet.

4. Attach IAM Role (optional)
   - Will software on the EC2 instance need to interact with other AWS services? If yes, attach an appropriate IAM Role. IAM Roles can be attached at any time, not just launch.
   - An instance profileis a container for an IAM role.
   - An AWS Identity and Access Management (IAM) role that is attached to an EC2 instance is kept in an instance profile.
5. User Data Script (optional)
   - Specify a user data script at instance launch. Use user data scripts to customize the runtime environment of your instance.
   - When the EC2instance is created, the user data script will run with root privileges during the final phases of the boot process.
   - On Linux instances, it is run by the cloud-initservice. On Windows instances, it is run by the EC2Config or EC2Launch.
   - By default, user data only runs the first time that the instance starts up.
   - Create Multipurpose Internet Mail Extensions (MIME) multipart file user data script to run each time EC2 instance boot.
6. Specify Storage
   - Configure the root volume
   - Attach additional storage volumes(optional). For each volume, specify:
     - Disk Size (in GB)
     - Volume type (SSDs or HDDs)
     - If the volume will be deleted when the instance is terminated
     - If encryption should be used
   - Storage Options:
     - Amazon Elastic Block Store (Amazon EBS) –
       - Durable, [block-level storage](https://en.wikipedia.org/wiki/Block-level_storage) volumes.
       - You can stop the instance and start it again, and the data will still be there.
       - increase volume size without disrupting your critical applications,
     - Amazon EC2 Instance Store
       - Storage is provided on disks that are attached to the host computer where the EC2 instance is running.
       - This storage is located on disks that are physically attached to the host computer.
       - If the instance stops, data stored here is deleted.
       - An instance with an Instance Store root volume cannot be stopped by an Amazon EC2 API call. It can only be terminated.
     - Other options for storage (not for the root volume)
       - Mount an Amazon Elastic File System (EFS) file system.
            -  It is built to scale on-demand to petabytes without disrupting applications. It grows and shrinks automatically as you add and remove files
       - Connect to Amazon Simple Storage Service (S3).
            - For a variety of use cases, such as websites, mobile apps, backup and restore, archive, enterprise applications, Internet of Things (IoT) devices, and big data analytics.
7. Add Tags
   - Consists of a key and an optional value.
   - Tag keys and tag values are case-sensitive.
   - Tagging is how you can attach metadata to an EC2 instance
   - Potential benefits: Filtering, automation, cost allocation, and access control.
8. Security Group Settings
   - A security group is a set of firewall rules that control traffic to the instance
   - When you launch an instance, you associate one or more security groups with it
   - Create rules that specify the source, which ports that network communications can use and the protocol (TPC, UDP, ICMP)
   - One must either create a new security group or use one that already exists in that VPC
   - Modify the rules for a security group at any time; the new rules are automatically applied to all instances that are associated with the security group
9. Identify or Create the Key Pair
   - At instance launch, you specify an existing key pair or create a new key pair
   - A key pair consists of a public key that AWS stores and a private key file that you store
   - It enables secure connections to the instance
   - Login to EC2 requires private key.
   - For Windows AMIs – Use the private key to obtain the administrator password that you need to log in to your instance
   - For Linux AMIs – Use the private key to use SSH to securely connect to your instance
  
     **EC2 Instance Launch Screen**

     <img width="631" alt="image" src="https://github.com/user-attachments/assets/d2850606-b604-4c05-bc2b-1ccfb9c30f23" />


### Elastic IP address

- Consider using an Elastic IP Address if you require a persistent public IP address.
- If you require a persistent public IP address, you might want to associate an Elastic IP address with the instance. 
- first allocate a new Elastic IP address in the Region where the instance exists. After the Elastic IP address is allocated, you can associate the Elastic IP address with an EC2 instance.
- By default, all AWS accounts are limited to five (5) Elastic IP addresses per Region.

### Instance metadata
- Instance metadata can be viewed in browser or a terminal window, and can be used to configure or manage a running instance.
- Can be access in browser by http://169.254.169.254/latest/meta-data/
- Public IP address, private IP address, public hostname, instance ID, security groups, Region, Availability Zone.
- Any user data specified at instance launch can also be accessed at: 
http://169.254.169.254/latest/user-data/

### Amazon CloudWatch
- Amazon CloudWatch can be used to monitor an EC2 instance to provide near-real-time metrics, charts, and 15 months of historical data. CloudWatch has basic monitoring (no additional cost) 
- By default, Amazon EC2provides basic monitoring,which sends metric data to CloudWatch in 5-minute periods.
- detailed monitoringon the instance provide data each minute.
- By default, Amazon CloudWatch does not provide RAM metrics for EC2 instances but can be enabled.



<br/>

## Section 3: Amazon EC2 Cost Optimization

### **Amazon Pricing Models**

On-Demand Instances

- Pay by the hour
- No long-term commitments.
- Eligible for the AWS Free Tier.

Dedicated Hosts

- A physical server with EC2 instance capacity fully dedicated to your use.

Dedicated Instances

- Instances that run in a VPC on hardware that is dedicated to a single customer.

Spot Instances

- Instances run as long as they are available and your bid is above the Spot Instance price.
- They can be interrupted by AWS with a 2-minute notification
- Interruption options include terminated, stopped or hibernated
- Prices can be significantly less expensive compared to On-Demand Instances
- Good choice when you have flexibility in when your applications can run.

Reserved Instances

- Full, partial, or no upfront payment for instance you reserve
- Discount on hourly charge for that instance
- 1-year or 3-year term

Scheduled Reserved Instances

- Purchase a capacity reservation that is always available on a recurring schedule you specify
- 1-year term

Per second billing available for On-Demand Instances, Reserved Instances, and Spot Instances that run Amazon Linux or Ubuntu

**On-Demand Instances**
- offer the most flexibility, with no long-term contract and low rates.
- Short-term, spiky, or unpredictable workloads, Application development or testing
**Spot Instances** 
- provide large scale at a significantly discounted price.
- Applications with flexible start and end times•Applications only feasible at very low compute prices Users with urgent computing needs for large amounts of additional capacity
**Reserved Instances** 
- are a good choice if you have predictable or steady-state compute needs (for example, an instance that you know you want to keep running most or all of the time for months or years).
- Steady state or predictable usage workloads•Applications that require reserved capacity, including disaster recovery•Users able to make upfrontpayments to reduce total computing costs even further.

**Dedicated Hosts** are a good choice when you have licensing restrictions for the software you want to run on Amazon EC2, or when you have specific compliance or regulatory requirements that preclude you from using the other deployment options.
- Bring your own license (BYOL) •Compliance and regulatory restrictions•Usage and licensing tracking•Control instance placement AWS Training and Certification.

### **Four Pillars of Cost Optimization**

Right Size

- Provision instances to match the need - CPU, memory, storage, and network throughput
- Use Amazon CloudWatch metrics to dowsize as needed - How idle are instances? When?
- Best practice: Right size, then reserve

Increase Elasticity

- Stop or hibernate Amazon EBS-backed instances that are not actively in use
- Use automatic scaling to match needs based on usage

Optimal Pricing Model

- Leverage the right pricing model for your use case
- Optimize and combine purchase types
  - Examples: Use On-Demand Instance and Spot Instances for variable workloads, use Reserved Instances for predictable workloads
- Consider serverless solutions (AWS Lambda)

Optimize Storage Choices

- Reduce costs while maintaining storage performance and availability
- Resize EBS volumes and change EBS volume types
- Delete EBS snapshots that are no longer needed
- Identify the most appropriate destination for specific types of data

### **Wrap-up**

Cost optimization is an ongoing process.

- Define and enforce cost allocation tagging
- Define metrics, set targets, and review regularly.
- Encourage teams to architect for cost
- Assign the responsibility of optimization to an individual or to a team.
- AWS cost explorer is a free tool that can be use to view graph of your cost. 

<br/>

## Section 4: Container Services

### **Container Basics**
 
- **Operating System Virtualization**: Containers allow running applications and dependencies in resource-isolated processes.  
- **Self-Contained Packages**: They include an application’s code, configurations, and dependencies, ensuring consistency and efficiency.  
- **Smaller than Virtual Machines**: Containers share the host OS rather than running a full OS, making them lightweight.  
- **Fast Deployment**: Containers start within milliseconds, making them highly efficient for rapid scaling.  
- **Environmental Consistency**: Applications run the same way across different environments.  
- **Resource Efficiency**: Containers offer granular resource control, improving infrastructure utilization.  
- **Portability & Agnosticism**: Containers can run seamlessly across different platforms without modifications.

**Docker Conainer**
Its provide templete for container and act as an engine to containers.
- Docker is a software platform that enables you to build, test, and deploy applications quickly. Containers are created from a template called an image.
- Docker is installed on each server that will host containers, and it provides simple commands that you can use to build, start, or stop containers.

**VM vs Containers**
- virtual machines run directly on a hypervisor, but containers can run on any Linux OS if they have the appropriate kernel feature support and the Docker daemon is present. 

<img width="230" alt="image" src="https://github.com/user-attachments/assets/6e264eca-b285-4bb3-bce1-dd7a71c876f4" />


### **Amazon Elastic Container Service (ECS)**

- A highly scalable, fast, container management service
- Key benefits
  - Orchestrates the execution of Docker containers
  - Maintains and scales the fleet of nodes that run your containers
  - Removes the complexity of standing up the infrastructure
- Integrated with features that are familiar to Amazon EC2 service users
  - Elastic Load Balancing
  - Amazon EC2 security groups
  - Amazon EBS volumes
  - IAM roles

**Essential Amazon ECS features include the ability to:** 
- Launch up to tens of thousands of Docker containers in seconds
- Monitor container deployment
- Manage the state of the cluster that runs the containers
- Schedule containers by using a built-in scheduler or a third-party scheduler (for example, Apache Mesosor Blox)

### Amazon ECS orchestrates containers
- **Task Definition:** A blueprint (text file) that describes the containers (up to 10) that make up your application.
- Specifies parameters like:
    - Containers to use
    - Ports to open
    - Data volumes for containers
- **Task:** An instantiation of a task definition in a cluster. You can define how many tasks will run in the cluster.
- **Amazon ECS Task Scheduler:** Responsible for placing tasks in the cluster.
- **Cluster:** A collection of EC2 instances running an ECS container agent (when using EC2 launch type)
- Amazon ECS provides multiple scheduling strategies that will place containers across your clusters based on your resource needs (for example, CPU or RAM) and availability requir


**EC2 Launch Type:**
- Choose between On-Demand Instances or Spot Instances for the EC2 instances in the cluster.
- You must specify the same details as when launching a standalone EC2 instance.
- Provides more control over infrastructure since you manage the EC2 instances in the cluster.
- Amazon ECS tracks CPU, memory, and other resources in the cluster and places containers on the best server based on resource needs.

**AWS Fargate Launch Type (Networking-only):**

- AWS manages the cluster for you.
- You only need to package your application in containers and define CPU, memory, networking, and IAM policies.
- No need to provision, configure, or scale the cluster.
- Simplifies management by removing the need to choose server types or scale the cluster, allowing you to focus on building your application.

Do you want to manage the Amazon ECS cluster that runs the containers?

- If yes, create an Amazon ECS cluster backed by Amazon EC2 (provides more granular control over infrastructure)
- If no, create an Amazon ECS cluster backed by **AWS Fargate** (easier to maintain, focus on your applications)


### **Amazon Elastic Kubernetes Service (EKS)**

What is Kubernetes?

- Kubernetes is open source software for container orchestration
  - Deploy and manage containerized applicationsat scale
  - The same toolset can be used on premises and in the cloud
- Complements Docker
  - Docker enables you to run multiple containers on a single OS host
  - Kubernetes orchestrates multiple Docker hosts **(nodes)**.
  - Containersare run in logical groupings called **pods**
- Automates container provisioning, networking, load distribution and scaling

Amazon Elastic Kubernetes Service (Amazon EKS)

- Enables you to run Kubernetes on AWS
- Certified Kubernetes conformant (supports easy migration)
- Supports Linux and Windows containers
- Compatible with Kubernetes community tools and supports popular Kubernetes add-ons
- Use Amazon EKS to manage clusters of Amazon EC2 compute instances and run containers that are orchestrated by Kubernetes on those instances

### Amazon Elastic Container Registry (ECR):
- Fully managed Docker container registry for storing, managing, and deploying Docker container images.
- Integrated with Amazon ECS, allowing you to store and manage container images for ECS applications.
- Specify the ECR repository in your ECS task definition for image retrieval.

**Compatibility:**

- Supports Docker Registry HTTP API version 2 which Allows interaction with Amazon ECR using Docker CLI commands or preferred Docker tools.
- Works with any Docker environment (cloud, on-premises, or local machine).

**Security:**
- Container images are encrypted at rest using Amazon S3 server-side encryption.
- Images can be transferred to and from Amazon ECS via HTTPS.

- Amazon ECR images can also be used with Amazon EKS.
- Amazon ECS integrationDocker support Team collaborationAccess controlThird-party integrations


<br/>

## Section 5: Introduction to AWS Lambda

- Event-drive, Serverless computing enables you to build and run applications and services without provisioning or managing servers.
- **Lambda function**, which is the AWS resource that contains the code that you upload.
- Supports multiple programming languages.
- Provides built-in fault tolerance and automatic scaling.
- It supports the orchestration of multiple functions.  define workflows **Step Functions**.
- An event source is an AWS service or developer-created application that triggers a Lambda function to run.
- Pay-per-use pricing

### AWS Lambda event sources
- Event Sources: AWS services or developer apps that produce events to trigger Lambda functions.
- Asynchronous Invocation: Services like Amazon S3, SNS, and CloudWatch Events invoke Lambda functions asynchronously.
- Polling: Lambda can pull records from services like SQS and DynamoDB to trigger functions.
- Direct Invocation: Lambda functions can be invoked directly via the Lambda console, API, SDK, CLI, or toolkits.

### AWS Lambda function configuration
- **Lambda Function**:
  - Custom code written to process events. AWS Lambda runs the function on your behalf.
- **Creating a Lambda Function**:
  - **Step 1**: Give the function a name.
  - **Step 2**: Specify:
    - **Runtime environment** (e.g., Python or Node.js).
    - **Execution role** (IAM permission for interacting with other AWS services).
  
- **Configuring the Function**:
  - **Add a trigger**: Choose an event source.
  - **Add function code**: Use the code editor or upload a file.
  - **Specify memory**: Between 128 MB to 10,240 MB.
  - **Optional settings**:
    - Environment variables, description, timeout.
    - Virtual Private Cloud (VPC) configuration.
    - Tags and other configurations.

All of the above settings end up in a Lambda deployment package which is a ZIP archive


Soft limits per Region:
- Concurrent executions = 1,000
- Function and layer storage = 75 GB
Hard limits for individual functions:
- Maximum function memory allocation = 10,240 MB
- Function timeout = 15 minutes•Deployment package size = 250 MB unzipped, including layers
- Container image code package size = 10 GB



<br/>

## Section 6: Introduction to Elastic Beanstalk

- An easy way to get web applications up and running
- A managed service that automatically handles
  - Infrastructure provisioning and configuration
  - Deployment
  - Load balancing
  - Automatic scaling
  - Health monitoring
  - Analysis and debugging
  - Logging
- No additional charge for Elastic Beanstalk, pay only for the underlying resources that are used
- It supports web applications written for common platforms
- You upload your code and Elastic Beanstalk automatically handles the deployment
- At the same time, you retain full control over the AWS resources that power your application, and you can access the underlying resources at any time.

### AWS Elastic Beanstalk deployments
1. **Deployment Options**: Elastic Beanstalk allows code deployment via the AWS Management Console, AWS CLI, Visual Studio, and Eclipse.
2. **Supported Platforms**: It supports a wide range of platforms, including Docker, Java, .NET, Node.js, PHP, Python, Ruby, and Go.
3. **Automatic Deployment**: Elastic Beanstalk automatically handles deployment on various servers like Apache, NGINX, IIS, and more, while you manage the code.
Fast and simple to start using, Developer productivity, Difficult to outgrowComplete resource control, AWS Training and Certification.


<br/>

