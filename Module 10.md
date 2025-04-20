# Module 10 - Automatic Scaling and Monitoring

## Objective/Topics

- Elastic Load Balancing
- Amazon CloudWatch
- Amazon EC2 Auto Scaling

<br/>

## 1. Elastic Load Balancing

- Distributes incoming application or network traffic across multiple targets in a single Availability Zone or across multiple Availability Zones.
- Scales your load balancer as traffic to your application changes over time.

### Types of Elastic Load Balancing

- Application Load Balancer
    - Operates at layer 7 of OSI model.
    - HTTP and HTTPS traffic

- Networking load Balancer
    - Operates at layer 4 of OSI model.
    - TCP, UDP and TLS traffic where extreme performance is required.

- Classical load Balancer(Previous generation)
    - Load balancing of HTTP, HTTPS, TCP and SSL traffic.
    - Load balacing accross multiple EC2 instances.
    - Work for both traditionally.

### How Elastic Load Balancing works

- With Application Load Balancers and Network Load Balancers, you register targets in target groups, and route traffic to the target groups.
- With Classic Load Balancers, you register instances with the load balancer.

**A listener** is a process that checks for connection requests. It is configured with a protocol and port number for connections from clients to the load balancer. 
 - It is configured with a protocol and port number for connections from clients to the load balancer. 
 - Similarly, it is configured with a protocol and port number for connections from the load balancer to the targets. 

### Elastic load Balacing use cases

- High availbility and fault tolerant application
- Containerized applications
- Elasticity and Scalibility
- Virtual Private Cloud(VPC)
- Hybrid Environmnent
- Invoke Lambda funtion over HTTP(S)

### Load balancer monitoring

- Amazon CloudWatch metrics–Used to verify that the system is performing as expected and creates an alarm to initiate an action if a metric goes outside an acceptable range.
- Access logs–Capture detailed information about requests sent to your load balancer.
- AWS CloudTrail logs–Capture the who, what, when, and where of API interactions in AWS services.

<br/>

## 2. Amazon CloudWatch

### Monioring AWS Resources

- To use AWS efficiently, you need insight into your AWS resources:
- How do you know when you should launch moreAmazon EC2 instances?
- Is your application's performance or availabilitybeing affected by a lack of sufficient capacity?
- How much of your infrastructure is actually being used?

### Amazon CloudWatch

- Monitors–
    - AWS resources
    - Applicationsthat run on AWS
- Collects and tracks–
    - Standard metrics
    - Custom metrics
- Alarms-
    - Send notificationsto an Amazon SNS topic
    - Perform Amazon EC2 Auto Scaling or Amazon EC2 actions
- Events–
    - Define rules to match changes in AWS environment and route these events to one or more target functions or streams for processing

### CloudWatch Alarm
Create alarms based on 

- Static threshold
    - Anomaly detection
    - Metric math expression
- Specify 
    - Namespace•Metric
    - Statistic
    - Period
    - Conditions
    - Additional configuration
    - Actions


### Some keytakeaways from this section of the module include:
- Amazon CloudWatch helps you monitor your AWS resources—and the applications that you run on AWS—in real time.
- CloudWatch enables youto –
- Collect and track standard and custom metrics.
- Set alarms to automatically send notifications to SNS topics or perform Amazon EC2 Auto Scaling or Amazon EC2 actions based on the value of the metric or expression relative to a threshold over a number of time periods.
- Define rules that match changes in your AWS environment and route these events to targets for processing.


<br/>

## 3. Amazon EC2 Auto Scaling

- Helps you maintain application availability
- Enables you to automatically add or remove EC2 instances according to conditions that you define
- Detects impaired EC2 instances and unhealthy applications, and replaces the instances without your intervention
- Provides several scaling options –Manual, scheduled, dynamic or on-demand, and predictive

**Auto Scaling group** is a collection of EC2 instances that are treated as a logical grouping for the purposes of automatic scaling and management.

<img width="667" alt="image" src="https://github.com/user-attachments/assets/892e7eef-b165-401b-9599-af290a8b06c2" />


Auto Scalling group size can me categorized as
- Minimum Size
- Desired Capacity
- Maximum Size

### How Amazon EC2 Auto Scaling works
1- What
    - Launch Configuration
    - AMI
    - Instance Type
    - IAM Roles
    - Security Groups
    - EBS Volumes

2- Where
    - Auto Scaling Groups
    - VPC and Subnet
    - Load Balancer

3- When
    - Maintain current number
        - Helath Check
    - Manual Scaling
        - Min,Max and desird Capacity
    - Scheduled Scalling
    - Dynamic Scalling
    - Predictive auto Scaling
        - AWS auto Scaling

### AWS Auto Scaling

- Monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost.
- Provides a simple, powerful user interface that enables you to build scaling plans for resources, including.
- Amazon EC2 instances and Spot Fleets•Amazon Elastic Container Service (Amazon ECS) Tasks.
- Amazon DynamoDB tables and indexes•Amazon Aurora Replicas.

<br/>

