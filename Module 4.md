# AWS Cloud Seccurity

- Is a shared responsibility

### **This module will address the following topics:**
- AWS shared responsibility model
- AWS Identity and Access Management (IAM)
- Securing a new AWS account
- Securing accounts
- Securing data on AWS
- Working to ensure compliance
- Additional security services and resources

### Module Objective
- Recognize the shared responsibility model
- Identify the responsibility of the customer and AWS
- Recognize IAM users, groups, and roles
- Describe different types of security credentials in IAM
- Identify the steps to securing a new AWS account
- Explore IAM users and groups
- Recognize how to secure AWS data
- Recognize AWS compliance programsAWS Training and Certification Module

### Section 1: AWS shared responsibility model

#### Customer Responsibility
- **Responsible for Security in the cloud**
- Customer Data
- Plateform, Aplication Access and Identity managment.
- OS, Network and Firewall Management.
- Client side data(Encrytion and Data integrity Authentication)
- Server Side encryption
- Networking Traffic Protection encryption.

- Amazon Elastic Compute Cloud (Amazon EC2) instance operating system - Including patching, maintenance
- Applications - Passwords, role-based access, etc.
- Security group configuration
- OS or host-based firewalls - Including intrusion detection or prevention systems
- Network configurations
- Account management - Login and permission settings for each user
- Security in the cloud.
- IaaS- More manage by customer, less AWS.
- PaaS- Customer less More AWS.
- SaaS- More AWS less Customer.

#### AWS Responsibility
**Software-**
- Compute, Storage, Database, Networking
**Hardare-**
- Regions, Available Zones, Edge Location

- Physical security of data centers - Controlled, need-based access
- Hardware and software infrastructure - Storage decommissioning, host operating system (OS) access logging, and auditing
- Network infrastructure - Intrusion detection
- Virtualization infrastructure - Instance isolation
    - AWS ensure that virtualization infrastructure provide isolation between customer workload. For Eg- EC2 instances of one customer is isloated from compute invironment of other customer.




### **Service Characteristics and Security**

**Iaas Example** of services Manage by Customer- EC2, EBS, Amazon VPC.
**PaaS Examples** of Services manage by AWS- AWS lambda, Amazon RDS, AWS BeansTalk.
**SaaS Examples** of services manage by AWS mostly- AWS Trusted adviser, AWS Shield, Amaozon Chime.

**AWS Trusted Advisor** is an online tool that analyzes your AWS environment and provides real-time guidance and recommendations to help you provision your resources by following AWS best practices. The Trusted Advisor service is offered as part of your AWS Support plan. Some of the Trusted Advisor features are free to all accounts, but Business Support and Enterprise Support customers have access to the full set of Trusted Advisor checks and recommendations.
**AWS Shield** is a managed distributed denial of service (DDoS) protection service that safeguards applications running on AWS. It provides always-on detection and automatic inline mitigations that minimize application downtime and latency, so there is no need to engage AWS Support to benefit from DDoS protection. AWS Shield Advanced is available to all customers.However, to contact the DDoS Response Team, customers must have either Enterprise Support or Business Support from AWS Support.
**Amazon Chime** is a communications service that enables you to meet, chat, and place business calls inside and outside your organization, all using a single application.It is a pay-as-you-go communications service with no upfront fees, commitments, or long-term contracts

Infrastructure as a service (IaaS)

- Customer has more flexibility over configuring networking and storage settings
- Customer is responsible for managing more aspects of the security
- Customer configures the access controls
- AWS services—such as Amazon EC2—can be categorized as IaaS and thus require the customer to perform all necessary security configuration and management tasks

Platform as a service (PaaS)

- Customer does not need to manage the underlying infrastructure
- AWS handles the operating system, database patching, firewall configuration, and disaster recovery
- Customer can focus on managing code or data

Software as a service (SaaS)

- Software is centrally hosted
- Licensed on a subscription model or pay-as-you-go basis.
- Services are typically accessed via web browser, mobile app, or application programming interface (API)
- Customers do not need to manage the infrastructure that supports the service

<br/>

## Section 2: Identity and Access Management (IAM)
- First service in AWS also free to use.
- Its a Global service. available across all region.

AWS Identity and Access Management (IAM) is a web service that enables Amazon Web Services (AWS) customers to manage users and user permissions in AWS. With IAM, you can centrally manage users, security credentials such as access keys, and permissions that control which AWS resources users can access.

AWS Identity and Access Management (IAM) can be used to:

- **Manage IAM Users and their access:** You can create Users and assign them individual security credentials (access keys, passwords, and multi-factor authentication devices). You can manage permissions to control which operations a User can perform.
- **Manage IAM Roles and their permissions:** An IAM Role is similar to a User, in that it is an AWS identity with permission policies that determine what the identity can and cannot do in AWS. However, instead of being uniquely associated with one person, a Role is intended to be assumableby anyone who needs it.
- **Manage federated users and their permissions:** You can enable identity federation to allow existing users in your enterprise to access the AWS Management Console, to call AWS APIs and to access resources, without the need to create an IAM User for each identity.

### **Essential Components**

**IAM User:** A person or application that can authenticate with an AWS account. When you define an IAM user, you select what types of access the user is permitted to use.


**Authentication as a IAM user** 
Note- When you define an IAM user you define the the way an user can authenciate itself.
- Programmatic Access
    - Access Key ID
    - Secret Access Key
Provide AWS CLI and AWS SDK access.
- AWS Management console Access
    - 12 digit Id
    - Username & Password
    - MFA(if anabled)

**IAM Group:** A collection of IAM users that are granted identical authorization.

- A user can belong to multiple groups
- There is no default group
- Groups cannot be nested

**IAM Policy:** The document that defines which resources can be accessed and the level of access to each resource.
- Policies are created independtly and then can be attached to groups or user.

- Permissions determine which resources and operations are allowed.
  - All permissions are implicitly denied by default.
  - If something is explicitly denied, it is never allowed.
- Two Types of Policies:
  1. Identity Based
     - Attach a policy to any IAM entity - user, group, or role
     - Policies specify actions that may or may not be performed by the entity
     - Policies and entities have a many-to-many relationship
     - When the policy is updated, the changes to the policy are immediately apply against all Users and Groups that are attached to the policy.
  2. Resource Based
     - Attached to a resource (such as an S3 bucket)
     - Specifies who has access to the resource and what actions they can perform on it
     - The policies are inline only, not managed. An inline policy is assigned to just one User or Group. Inline Policies are typically used to apply permissions for one-off situations.
     - Resource-based policies are supported only by some AWS services

**IAM Role:** Useful mechanism to grant a set of permissions for making AWS service requests.

- Similar to an IAM user: Attach permissions policies to it
- Different from an IAM user: Not uniquely associated with one person, intended to be assumable by a person, application, or service
- Role provides temporary security credentials

    #### Examples of how IAM roles are used to delegateaccess 
        - Used by an IAM user in the same AWS account as the role 
        - Used by an AWS service—such as Amazon EC2—in the same account as the role
        - Used by an IAM user in a different AWS account than the role


**IAM Authorization** - 
- Assign Permission by creating an IAM policy.
- Permission determine which resource and services 
    - All permisssion are denied by default.
    - If something explicitly denied it cant be enbale.




- AWS Management Console Access



**Principle of Least Privilege:** The practice of limiting access rights for users to the bare minimum permissions they need to perform their work. Under POLP, users are granted permission to read, write or execute only the files or resources they need to do their jobs

<br/>

## Section 3: Securing a New AWS Account

Best practice: Do not use the AWS account root user except when necessary. Access to the account root user requires logging in with the email address and password that you used to create the account.
**4 Steps**
1. Stop using the account root user as soon as possible
   1. While you are logged in as the account root user, create an IAM user for yourself. Save the access keys if needed.
   2. Create an IAM group, give it full administrator permissions, and add the IAM user to the group.
   3. Disable and remove your account root user access keys, if they exist.
   4. Enable a password policy for users.
   5. Sign in with your new IAM user credentials.
2. Enable multi-factor authentication (MFA)
3. Use AWS CloudTrail
   - CloudTrail tracks user activity on your account. It logs all API requests to resources in all supported services your account.
   - Basic AWS CloudTrail event history is enabled by defaultand is free. It contains all management event data for the last 90 days of account activity (this can be extended beyond 90 days)
   - Add S3 bucket for extra storage.
4. Enable a billing report, such as the *AWS Cost and Usage Report*
    - It store data in the S3 that you assigned to it.

[Lab: Introduction to IAM](https://labs.vocareum.com/main/main.php) --- [Lab Instructions](https://labs.vocareum.com/main/main.php)

<br/>

## Section 4: Securing Accounts

### **AWS Organizations**

Organizations enable you to consolidate multiple AWS accounts so that you centrally manage them.

Security Features of AWS Organizations:

- Group AWS accounts into organizational units (OUs) and attach different access policies to each OU.
- Integration and support for IAM. Permissions to a user are the intersection of what is allowed by AWS Organizations and what is granted by IAM in that account.
- Use service control policies to establish control over the AWS services and API actions that each AWS account can access

#### Service Control Policies

- Service control policies (SCPs) offer centralized control over accounts. Limit permissions that are available in an account that is part of an organization.
- Ensures that accounts comply with access control guidelines.
- SCPs are similar to IAM permissions policies – They use similar syntax, but an SCP never grants permissions. Instead, SCPs specify the maximum permissions for an organization.

#### Key Management Service

- Enables you to create and manage encryption keys
- Enables you to control the use of encryption across AWS services and in your applications.
- Integrates with AWS CloudTrail to log all key usage.
- Uses hardware security modules (HSMs) that are validated by Federal Information Processing Standards (FIPS) 140-2 to protect keys

#### Cognito

- Adds user sign-up, sign-in, and access control to your web and mobile applications. Scales to millions of users.
- Supports sign-in with social identity providers, such as Facebook, Google, and Amazon; and enterprise identity providers, such as Microsoft Active Directory via Security Assertion Markup Language (SAML) 2.0.

#### Shield

- Is a managed distributed denial of service (DDoS) protection service
- Provides always-on detection and automatic inline mitigations
- AWS Shield Standard enabled for at no additional cost. AWS Shield Advanced is an optional paid service.
- Use it to minimize application downtime and latency

## Section 5: Securing Data

### **Data at Rest**

- Data at rest = Data stored physically (on disk or on tape)
- Encryption encodes data with a secret key, which makes it unreadable. Only those who have the secret key can decode the data. 
- You can encrypt data stored in any service that is supported by AWS KMS which manages the keys.
- AES 256 Encription algo is used.

### **Data in Transit**

- Data in transit = Data moving across a network
- Transport Layer Security (TLS) — formerly SSL, is an open standard protocol. AWS Certificate Manager provides a way to manage, deploy, and renew TLS or SSL certificates
- Secure HTTP (HTTPS) creates a secure tunnel.
- Use AES 256 cipher

### **Securing Amazon S3 buckets and objects**
- All S3 buckets are private and protected by default.

Tools and options for controlling access to S3 data include 
- Amazon S3 Block Public Access feature: Simple to use.
- IAM policies: A good option when the user can authenticate using IAM.
- Bucket policies
- Access control lists(ACLs): A legacy access control mechanism.•AWS Trusted Advisorbucket permission check: A free feature.

## Section 6: Working to Ensure Compliance

Customers are subject to many different security and compliance regulations and requirements. AWS engages with certifying bodies and independent auditors to provide customers with detailed information about the policies, processes, and controls that are established and operated by AWS.

- Infomation security management defines how AWS manage security in holistic and comprehensive manner.
- AWS also provides security features and legal agreements that are designed to help support customers with common regulations and laws. One example is the Health Insurance Portability and Accountability Act (HIPAA) regulation. Anotherexample, the European Union(EU) General Data Protection Regulation (GDPR)  

Compliance programs can be broadly categorized:

- Certifications and attestations
- Laws, regulations, and privacy
- Alignments and frameworks - Industry or function-specific security or compliance requirements

### **AWS Config**

- Assess, audit, and evaluate the configurations of AWS resources.
- Automatically evaluate recorded configurations versus desired configurations.
- Review configuration changes and view detailed configuration histories.
- As you can see in the AWS Config Dashboard screen capture shown here, AWS Config keeps an inventory listing of all resources that exist in the account,and it then checks for configuration rule compliance and resource compliance. Resources that are found to be noncompliant are flagged, which alerts you to the configuration issues that should be addressed within the account.
- AWS Config is a Regional service.To track resources across Regions, enable it in every Region.
- You can also use AWS Artifact to review, accept, and track the status of AWS agreements such as the Business Associate Agreement (BAA). A BAA typically is required for companies that are subject to HIPAA to ensure that protected health information (PHI) is appropriately safeguarded.
- With AWS Artifact, you can accept agreements with AWS and designate AWS accounts that can legally process restricted information.

### AWS Artifact

- A resource for compliance-related information
- Provide access to security and compliance reports, and select online agreements
- Access AWS Artifact directly from the AWS Management Console

<br/>

---

<br/>