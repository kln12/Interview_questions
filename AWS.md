**Diff b/w EFS and EBS  
Answer:** Both of these are AWS Storage services, Amazon EBS is the block storage offered on AWS. An Amazon EBS volume is a persistent storage device that can be used as a file system for databases, application hosting and storage, and plug and play devices. Volumes get automatically replicated within Availability Zones for high availability and durability.   
Amazon EFS is an NFS file system service offered by AWS. EFS is the best choice for running any application that has a high workload, requires scalable storage, and must produce output quickly. It scales automatically, even to meet the most abrupt workload spikes. After the period of high-volume storage, demand has passed, EFS will automatically scale back down. File storage is a storage like shared folder which we can access through IP and save our files and folders. It is of two type NFS and CIFS. NFS is in Unix machine where as CIFS is in Windows.   
Block storage is just like a hard disk. It get mapped to a physical server (ESXi, Cisco, Dell, Lenevo etc). It can be through FC, iSCSI or FCOE.
File storage is a storage like shared folder which we can access through IP and save our files and folders. It is of two type NFS and CIFS. NFS is in Unix machine where as CIFS is in Windows      
**Diff B/W application Load balencer and elastic load balencer   
Answer:** Application Load Balancers support content-based routing and support applications that run in containers. They support a pair of industry-standard protocols (WebSocket and HTTP/2), and also provide additional visibility into the health of the target instances and containers. Websites and mobile apps, running in containers or on EC2 instances, can benefit from the use of Application Load Balancers.   
An Elastic Load Balancer (ELB) is one of the key architecture components for many applications inside the AWS cloud. In addition to autoscaling, it enables and simplifies one of the most important tasks of our application’s architecture: scaling up and down with high availability.Elastic Load Balancing automatically distributes incoming application traffic across multiple applications, microservices, and containers hosted on Amazon EC2 instances.One of the many advantages of using ELB is the fact that it is elastic (i.e. changeable), which means that it will automatically scale to meet your incoming traffic.   https://cloudacademy.com/blog/application-load-balancer-vs-classic-load-balancer/   
**how to replicate S3 bucket   
Answer:**   Replication enables automatic, asynchronous copying of objects across Amazon S3 buckets. Buckets that are configured for object replication can be owned by the same AWS account or by different accounts.To automatically replicate new objects as they are written to the bucket, use live replication, such as Cross-Region Replication (CRR). To replicate existing objects to a different bucket on demand, use S3 Batch Replication   
###Choose if both S3 buckets belong to same account or different accounts ###   
Create 2nd replicated bucket (if not present)
Check if Bucket Versioning is enabled or not. On Both buckets, it needs to be enabled
to check, Go to AWS S3 console -> Open S3 Bucket -> Properties -> Bucket Versioning
Make sure you have access to both S3 buckets, to copy content and make changes in S3 bucket configurations   
**4 explain Disastor Recovery(DR) AND types    
Answer:**   https://aws.amazon.com/blogs/architecture/disaster-recovery-dr-architecture-on-aws-part-i-strategies-for-recovery-in-the-cloud/   
**how income allow but does not go outbound      
Answer:**   
**how to increase a the volume size of instance  
Answer:**     Consider you have stopped the instance from running, simply navigate to Elastic Block Store -> Volumes.   
Check the box on the volume you want to increase and click the Actions button. Click the Modify Volume option and enter the number of GB you want in the Size field. Click the Modify button once you’re done.   
Now Reboot your instance. (See the image above for the reboot option).   
**what is MX record & Cname in route53**    
**Answer** A CNAME record maps DNS queries for the name of the current record, such as acme.example.com, to another domain (example.com or example.net) or subdomain (acme.example.com or zenith.example.org).   
An MX record specifies the names of your mail servers and, if you have two or more mail servers, the priority order. Each value for an MX record contains two values, priority and domain name.   
**S3:** S3 An object store (not a file system).You can store files and "folders" but can't have locks, permissions etc like you would with a traditional file system.This means, by default you can't just mount S3 and use it as your webserverBut it's perfect for storing your images and videos for your website.Great for short term archiving (e.g. a few weeks). It's good for long term archiving too, but Glacier is more cost efficient.Great for storing logs. You can access the data from every region (extra costs may apply) Highly Available, Redundant. Basically data loss is not possible (99.999999999% durability, 99.9 uptime SLA) Much cheaper than EBS. You can serve the content directly to the internet, you can even have a full (static) website working direct from S3, without an EC2 instance    
**2.Define serverless LAMBA function and cloud formation   
Answer:** CloudFormation is a tool for specifying groups of resources in a declarative way. Each resource is actually a small block of JSON that CloudFormation uses to create a real version that is up to the specification provided.      
AWS Lambda is a compute service that lets you run code without provisioning or managing servers.Lambda runs your code on a high-availability compute infrastructure and performs all of the administration of the compute resources, including server and operating system maintenance, capacity provisioning and automatic scaling, and logging. With Lambda, all you need to do is supply your code in one of the language runtimes that Lambda supports.   
**3.cloud application and network load  
Answer:**   
**4.if a pem key has lost doesn't have any backup.how to login ec2 server?   
Answer:**  Accessing the EC2 instance even if you loose the pem file is rather easy.   
First, create a new instance by creating new access file, call it 'helper' instance with same region and VPC as of the lost pem file instance.   
Now stop the lost pem file instance. Remember not to terminate instance but to stop it.   
Go to EBS volumes, select the root volume of the lost pem file instance and detach.   
Now again select the detached volume and this time you have to attach this volume to helper instance which we created before. Since helper instance already has a root volume by default as /dev/sda1, the newly attached volume will be secondary(eg: /dev/sdf).   
Login to your helper instance with its pem file.   
Execute below commands:   
** mount /dev/xvdf1 /mnt   ##
** cp /root/.ssh/authorized_keys /mnt/root/.ssh/   
** umount /mnt   
Detach the secondary volume from helper instance.      
Again attach the volume back to our recovery instance. Start the instance. Terminate the helper instance.   
Use helper instance pem file to log into recovery instance.   
**5.Define ARN :    
Answer**Amazon Resource Names (ARNs) uniquely identify AWS resources. We require an ARN when you need to specify a resource unambiguously across all of AWS, such as in IAM policies, Amazon Relational Database Service (Amazon RDS) tags, and API calls.   
***arn:partition:service:region:account-id:resource-id   
**6.Different types of EC2 instances   
Answer:** Amazon EC2 provides a wide selection of instance types optimized to fit different use cases. Instance types comprise varying combinations of CPU, memory, storage, and networking capacity and give you the flexibility to choose the appropriate mix of resources for your applications. Each instance type includes one or more instance sizes, allowing you to scale your resources to the requirements of your target workload.  
1.General Purpose  2.Compute Optimized 3.Memory Optimized 4.Accelerated Computing 5.Storage Optimized   
**7.What is the difference b/w the DNS and Gated       
Answer:**   DNS server - Domain Name System. As the name itself indicates it translates domain name to IP address.   
Gateway - In simple way of saying it’s a network device to be more specific it’s a router( or firewall, server, any network device which allows to and from traffic). This router acts as a gateway between two networks ( internal and external network).   
**8.difference b/w the Terminate and stop in AWS    
Answer:** When you stop an AWS EC2 instance, you do not get charged for that instance and can restart the instance with all the data and software on the EC2 instance being intact. However, you are charged for the EBS volumes attached with the instance.   
When you terminate an AWS EC2 instance, you cannot restart the instance and all the data is permenantely lost. You cannot use that same instance ever again. Once the state of the instance is changed to shutting-down or terminated you are no longer charged for that instance.   
It is always a good practice to take backup of your EC2 instance as AMI and of your EBS volumes as snapshot before terminating the instance. A new EC2 instance with an EBS volume can be spawned from the AMI and the snapshot   
**9.Cloud watch and SNS     
Answer**
**10.private and public subnet     
Answer**  https://www.learnaws.org/2022/06/22/public-private-subnets/     
11.Types of s3     
**12.Define Security group and NACL   
Answer**  ![image](https://github.com/kln12/Interview_questions/assets/58560303/9480d5cc-b10a-4e11-a9d3-8fa6de113272)

13.Explain User data    Answer   
14.Storage types    Answer   
15.Disastor Recovery    Answer   
**Difference between Internet Gateway and NAT Gateway    Answer**
Internet Gateway (IGW) is a horizontally scaled, redundant, and highly available VPC component that allows communication between your VPC and the internet.
Internet Gateway enables resources (like EC2 instances) in public subnets to connect to the internet. Similarly, resources on the internet can initiate a connection to resources in your subnet using the public.If a VPC does not have an Internet Gateway, then the resources in the VPC cannot be accessed from the Internet (unless the traffic flows via a Corporate Network and VPN/Direct Connect).Internet Gateway supports IPv4 and IPv6 traffic.Internet Gateway does not cause availability risks or bandwidth constraints on your network traffic.In order to make subnet public, add a route to your subnet’s route table that directs internet-bound traffic to the internet gateway.You can associate exactly one Internet Gateway with a VPC.Internet Gateway is not Availability Zone specific.There’s no additional charge for having an internet gateway in your account.   
NAT Gateway (NGW) is a managed Network Address Translation (NAT) service. NAT Gateway does something similar to Internet Gateway (IGW), but it only works one way: Instances in a private subnet can connect to services outside your VPC but external services cannot initiate a connection with those instances.NAT gateways are supported for IPv4 or IPv6 traffic.NAT gateway supports the following protocols: TCP, UDP, and ICMP.Each NAT gateway is created in a specific Availability Zone and implemented with redundancy in that zone.   
**18.VPC Peering    
Answer**     
19.EKS and ECS Answer:    Answer   
20.Application Load Balancer vs Network Load Balancer    Answer   
21.subnet mask and calculate rhe 10.2.1.0/16    Answer   
**22.if pem key is deleted alternatively how can authenticate agent   
Answer**   https://towardsdev.com/accessing-aws-instances-if-pem-key-file-is-lost-2a7f4dca4f89   

23.describe eni    Answer   
24.ebs volume types    Answer   
**What is VPC endpoints     
Answer** A VPC endpoint enables customers to privately connect to supported AWS services and VPC endpoint services powered by AWS PrivateLink. Amazon VPC instances do not require public IP addresses to communicate with resources of the service. Traffic between an Amazon VPC and a service does not leave the Amazon network   

**27. FTP    Answer**     
FTP stands for "File Transfer Protocol," and it is a standard network protocol used for the transfer of files from one host to another over a TCP-based network, typically the internet. Here's a brief overview of FTP:  SFTP and FTPS are two secure file transfer protocols that address the security shortcomings of the traditional FTP (File Transfer Protocol). They are designed to encrypt data during transmission and provide authentication methods for secure file transfers. Here's an overview of both protocols:  
SFTP (SSH File Transfer Protocol):Security Layer: SFTP is an extension of the SSH (Secure Shell) protocol. It secures data transmission by encrypting both the control (command) and data channels, making it resistant to eavesdropping and data tampering.   
FTPS (FTP Secure):Security Layer: FTPS is an extension of FTP, and it adds a security layer through Transport Layer Security (TLS) or Secure Sockets Layer (SSL) encryption. It can operate in two modes: Explicit FTPS and Implicit FTPS.   

**28.cloud trail       
Answer** CloudTrail is a service provided by Amazon Web Services (AWS) that helps you monitor and log actions taken in your AWS account. It records information about every API call made on your AWS account, capturing details about who made the call, what action was taken, and when it occurred  
To use CloudTrail, you need to create a trail, which specifies the settings for logging and storing the recorded events. You can then monitor, analyze, and respond to events based on the data captured in CloudTrail logs   

**nat gatway    
Answer**A NAT gateway is a Network Address Translation (NAT) service. You can use a NAT gateway so that instances in a private subnet can connect to services outside your VPC but external services cannot initiate a connection with those instances.   
**30.code pipeline, multi tenancy, aptcontainer, elasticbean stack and how to access to access other application using iam**     
**31.Services used AWS and tasks performed in AWS         
Answer**  Familiarize Yourself with AWS Services:
AWS offers a wide range of services. You should be comfortable discussing the following, at a minimum:
**Compute Services**: EC2 (Elastic Compute Cloud), Lambda, ECS.   
**Storage Services**: S3 (Simple Storage Service), EBS (Elastic Block Store).   
**Database Services**: RDS (Relational Database Service), DynamoDB.   
**Networking Services**: VPC, Route 53, CloudFront.   
**Serverless Services**: AWS Lambda.   
**Container Services**: Amazon ECS, EKS.   
**Security and Identity Services**: IAM (Identity and Access Management), Security Groups, NACLs, and Web Application Firewall (WAF).   
**Monitoring and Logging Services**: CloudWatch and CloudTrail.   
**Deployment and Orchestration**: Elastic Beanstalk, CloudFormation.   
**32.I have 3 tier application, configure it with private and public subnet?      
Answer**   Sign in to AWS Console:   
Sign in to your AWS account to create and configure your infrastructure.   
Create VPC:   
Start by creating a Virtual Private Cloud (VPC), which will serve as your network environment.
Create Subnets:
You'll need at least two types of subnets: public and private.
Public Subnets: These are usually associated with the web tier and allow inbound and outbound internet traffic. To create a public subnet, choose the "Create subnet" option within your VPC, and ensure that you disable the option to disable auto-assign public IPv4 addresses.
Private Subnets: These are generally associated with your application and database tiers, which shouldn't have direct internet access. To create a private subnet, disable the option to auto-assign public IPv4 addresses.
Route Tables:   
Create two route tables - one for the public subnets and another for the private subnets. The public route table should have a route to the internet gateway for 0.0.0.0/0, while the private route table doesn't require an internet gateway route.
Internet Gateway:
Create an Internet Gateway and attach it to your VPC. This allows resources in the public subnets to access the internet.
Security Groups:
Define security groups for each tier to control inbound and outbound traffic.
Launch Instances:   
Launch your instances in the appropriate subnets.
Web Tier: Instances in the public subnet. These could be your web servers.
Application Tier: Instances in the private subnet, allowing traffic only from the web tier.
Database Tier: Instances in a different private subnet, only allowing traffic from the application tier.
Load Balancer (Optional):
If you have a multi-instance setup in the web tier, you can set up a load balancer to distribute traffic among them.
Database Setup:
Install and configure your database server(s) in the database tier subnet. Make sure the security group only allows traffic from the application tier.
Configuration:
Configure your application servers to connect to the database servers using private IPs. Update any security groups to allow necessary communication.
Testing:
Test your setup to ensure that it's working as expected. Try accessing the application from the internet to confirm that the web tier is correctly configured.
Monitoring and Scaling:
Set up monitoring and scaling policies as per your requirements to ensure your application can handle varying loads.   
**33.How to replicate or create same machine with same configuration?    
Answer**
Create an AMI from the Source Machine:
First, create an Amazon Machine Image (AMI) from your source machine. An AMI is a snapshot of your machine's root volume, and it includes the configuration and data.
Sign in to your AWS Management Console.   
Navigate to the EC2 Dashboard.
In the navigation pane, choose "Instances."   
Select the instance you want to replicate.   
Right-click on the instance, choose "Image," and then "Create Image."   
Provide a name and description for your AMI, and click "Create Image." This will initiate the AMI creation process.   
Launch a New Instance from the AMI:   
Once your AMI is created, you can launch new instances with the same configuration.
In the EC2 Dashboard, click "AMIs" in the navigation pane to find your newly created AMI.
Select the AMI and click "Launch."   
Follow the instance creation wizard, specifying the instance type, networking, and other settings.
When configuring the security groups and key pairs, make sure to choose the appropriate options for your new instance.
Review and Launch:
Review your settings and configurations, and click "Launch."
Access the New Instance:
Once the new instance is running, you can access it using the same methods as your source machine. This includes SSH for Linux instances or Remote Desktop for Windows instances.     

**how to manage the S3 Bucket from EC2 instance to write and read by private   
Answer** 

