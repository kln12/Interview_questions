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
**how inconme allow but does not go outbound      
Answer:**   
**how to increase a the volume size of instance  
Answer:**     Consider you have stopped the instance from running, simply navigate to Elastic Block Store -> Volumes.   
Check the box on the volume you want to increase and click the Actions button. Click the Modify Volume option and enter the number of GB you want in the Size field. Click the Modify button once you’re done.   
Now Reboot your instance. (See the image above for the reboot option).   
**what is ms record & Cname in route53**   
**S3:** S3 An object store (not a file system).You can store files and "folders" but can't have locks, permissions etc like you would with a traditional file system.This means, by default you can't just mount S3 and use it as your webserverBut it's perfect for storing your images and videos for your website.Great for short term archiving (e.g. a few weeks). It's good for long term archiving too, but Glacier is more cost efficient.Great for storing logs. You can access the data from every region (extra costs may apply) Highly Available, Redundant. Basically data loss is not possible (99.999999999% durability, 99.9 uptime SLA) Much cheaper than EBS. You can serve the content directly to the internet, you can even have a full (static) website working direct from S3, without an EC2 instance 2.LAMBA and cloud formation Answer:
**3.cloud application and network load  
Answer:**
4.if a pem key has lost doesn't have any backup.how to login ec2 server? Answer:
5.Iam ARN Answer:  
6.different types of EC2 instances Answer:
7.DNS vs Gated Answer:
8.Terminate vs stop in aws Answer:
9.Cloud watch and SNS
10.private and public subnet
11.Types of s3     
12.Define Security group and NACL   
13.User data   
14.Storage types   
15.Disastor Recovery   
16.Internet vs NAT Gatway   
17.Faragate 18.VPC Peering   
19.EKS and ECS Answer:   
20.Application Load Balancer vs Network Load Balancer   
21.subnet mask and calculate rhe 10.2.1.0/16   
22.if pem key is deleted alternatively how can authenticate agent   
23.describe eni   
24.ebs volume types   
25.explain endpoints   
26.Versionind in s3   
27.FTP Commands   
28.cloud trail   
29.nat gatway     
**30.code pipeline, multi tenancy, aptcontainer, elasticbean stack and how to access to access other application using iam**
