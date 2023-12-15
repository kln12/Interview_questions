**1.i have 4 clusters A,B,C,D and i'm in Ath cluster and i want to switch to B cluster  
Answer:**   Switching to a different cluster in Kubernetes involves changing your kubectl context to the context associated with the desired cluster,check the available contexts and their associated clusters "kubectl config get-contexts" To switch to cluster B, use the" kubectl config use-context cluster-b"command and specify the context associated with cluster B.   
**2. In kubernetes, Role based authentication    
Answer:** Role-based access control (RBAC) is a method of regulating access to computer or network resources based on the roles of individual users within your organization.  The RBAC API declares four kinds of Kubernetes object: Role, ClusterRole, RoleBinding and ClusterRoleBinding.   
**3. How to troubleshoot the pod, if issue occur after 6 month    
Answer:**   
**4.how to stop pods on particular node    
Answer:**   
**5.if one node is down and how to pods are shedule to other nodes    
Answer:**   
In a Kubernetes cluster, if a node goes down, the Pods running on that node need to be rescheduled to other available nodes to maintain the desired state of the application. Kubernetes has a mechanism called "Pod rescheduling" or "Node failure handling" to address this  Eviction of Pods:
Once a node is detected as unhealthy or goes down, Kubernetes initiates the eviction of Pods running on that node.
The scheduler identifies the affected Pods and decides where to reschedule them based on resource requirements, node affinity/anti-affinity rules, and other policies.  
**6.Can we have multiple conatiners in a pod? Can we have similar conatiners in a pod? Lets say i have 4 conatiners, one of them has failed how would you check which container has failed?   
Answer**
**7.What is liveness and readiness probe? Why we need them?   
Answer** https://cloud.google.com/blog/products/containers-kubernetes/kubernetes-best-practices-setting-up-health-checks-with-readiness-and-liveness-probes   
**8.Can we deploy a pod on particular node?   
Answer** https://blog.house-of-code.com/how-to-restrict-pods-to-run-on-only-on-specific-nodes-in-kubernetes/   

**9.what is init container and side-car container?can you give simple scenario where we use these conatiners?   
Answer**Init-containers are used to initialize something inside your Pod. The init-containers will run and exit. After every init container which exits with a code 0, your main containers will start. 
Kubernetes itself does not know anything about sidecars. Sidecar-Containers are a pattern to solve some use-cases. Usually, Kubernetes distinguishes between Init-Containers and Containers running inside your Pod.   
Typically, we call Sidecars all containers, that do not provide a user-focused service. For example, this could be a proxy or something for easier database access. If you're running a Java-App you could use a sidecar to export JVM metrics in Prometheus format.   
The difference here is, that your sidecar-containers must run all the time. If one of your not-init-containers exits, kubernetes will restart the whole pod.
And that's the difference.   
Init containers run and exit before your main application starts   
Sidecars run side-by-side with your main container(s) and provide some kind of service for them.      

**10.command to check the container logs in pod?   
Answer**$ kubectl logs <pod-name> -c <container-name>   
 we can use the –tail option to fetch only the latest logs.   
 $ kubectl logs <pod-name> -c <container-name> --tail=<number-of-lines>   
 
**11.what are the types of services present in kubernetes?   
Answer** https://www.vmware.com/topics/glossary/content/kubernetes-services.html   
**12.List objects you know in kubernetes?Give a brief about each object?   
Answer**
**13.Command to list pods and deployments   
Answer**
**14.Components in kubernetes architecture?   
Answer** https://komodor.com/learn/kubernetes-architecture/  
**15.What are stateful sets in kuberentes?   
Answer**StatefulSet is the workload API object used to manage stateful applications. Manages the deployment and scaling of a set of Pods, and provides guarantees about the ordering and uniqueness of these Pods. 
Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a sticky identity for each of its Pods. These pods are created from the same spec, but are not interchangeable: each has a persistent identifier that it maintains across any rescheduling. 

**16.Why config maps are used   
Answer**A configMap is an API object used to store non-confidential data in key-value pairs. Pods can consume ConfigMaps as env variables, command-line arguments, or as configuration files in a volume.A configMap allows you to decouple env specific configuration from our containers images, so that our
applications are easily portable.   
Note: It doesn't provide secrecy or encryption.   

**17.what are operators and give one example where we can use operator?   
Answer**https://www.cncf.io/blog/2022/06/15/kubernetes-operators-what-are-they-some-examples/  

**20.write an ingress file**  
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  namespace: your-namespace
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
    - host: your-domain.com
      http:
        paths:
          - path: /app
            pathType: Prefix
            backend:
              service:
                name: your-app-service
                port:
                  number: 80

**21. Decribe about K8's Services**  
https://komodor.com/learn/kubernetes-service-examples-basic-usage-and-troubleshooting/   
**22. Describe DaemonSet.    
 Answer**A DaemonSet is a Kubernetes resource that ensures that a copy of a Pod is running on all (or some) nodes in a cluster. It is useful for running background services or daemons that need to be present on all nodes, such as log collectors, monitoring agents, or network plugins.

 **6. How have you handled failed deployments?
AnswerIdentify** the Issue:Quickly determine the nature of the problem. Is it a code issue, configuration problem, infrastructure issue, or a combination of factors
Rollback:If possible, roll back to the previous version to minimize the impact on users and the system.
Communication:Communicate with relevant stakeholders, including users, management, and the development team. Provide clear and accurate information about the issue, its impact, and the steps being taken to address it.
Isolate the Problem:Narrow down the scope of the problem to identify the root cause. This may involve analyzing logs, monitoring data, and conducting further testing.
Fix the Issue:Develop a solution for the identified problem and test it thoroughly in a controlled environment before attempting another deployment.  
**24. How to create a node  
Answer** https://kubernetes.io/docs/concepts/architecture/nodes/  
**23.Describe TSL    
Answer**
**24.what is the importance of kubeconfig file? Also lets say when you login to kuberenets by default it will pointed to default namespace, if i want list any objects which are other namespace need concate -n option for all the kubectl commands, is there a way we can set the namaspace to aviod -n option in all the commands
Answer**The kubeconfig file is a crucial configuration file used by kubectl to interact with Kubernetes clusters. It contains information about cluster authentication, the location of the cluster, the default namespace, and other settings.
**24.Tools to maintain kubernetes log files
Answer**
**25.List objects you know in kubernetes?Give a brief about each object?
Answer** 
Kubernetes has a variety of objects that allow you to deploy, manage, and scale applications.some commonly used Kubernetes objects   
Pod:  
Description: The smallest deployable unit in Kubernetes. A Pod represents a single instance of a running process in a cluster and encapsulates one or more containers.Use Case: Running a single container or multiple tightly-coupled containers within the same network namespace.  
ReplicationController (Deprecated) / ReplicaSet:  
Description: Ensures a specified number of replica Pods are running at all times. It is used for maintaining the desired number of replicas of a Pod.
Use Case: Ensuring high availability and scalability by managing identical Pods.  
Deployment:  
Description: Provides declarative updates to applications. It allows you to describe the desired state of the application and automatically manages the deployment and scaling of Pods.Use Case: Rolling updates, rollbacks, and scaling applications.  
Service:  
Description: Exposes a set of Pods as a network service. It provides a stable IP address and DNS name for accessing the Pods, enabling load balancing across them.Use Case: Exposing applications within the cluster or making them accessible externally.  
ConfigMap:  
Description: Stores configuration data in key-value pairs. ConfigMaps can be mounted into Pods as volumes or used to set environment variables.Use Case: Separating configuration from application code and managing configuration data.  
Secret:  
Description: Stores sensitive information, such as passwords, OAuth tokens, and SSH keys. Secrets are base64 encoded and can be used by Pods.Use Case: Securing sensitive data used by applications.  
Namespace:  
Description: Provides a way to divide cluster resources into virtual clusters. It helps in organizing and isolating resources within a cluster.Use Case: Multi-tenancy and resource isolation.  
ServiceAccount:  
Description: Provides an identity for processes running in a Pod. Service accounts are used to control access to the Kubernetes API.Use Case: Controlling permissions and access for Pods.  
PersistentVolume (PV) and PersistentVolumeClaim (PVC):  
Description: PV represents physical storage resources, and PVC is a request for those resources by a user. PVCs consume PVs.Use Case: Persistent storage for stateful applications.  
StatefulSet:  
Description: Manages the deployment and scaling of a set of Pods with stable network identities. It is used for stateful applications.Use Case: Deploying and scaling stateful applications with unique network identities.  
DaemonSet:  
Description: Ensures that all (or some) Nodes run a copy of a Pod. It is used for deploying system daemons or agents on every Node.Use Case: Running a monitoring agent or logging agent on every Node.  
Job and CronJob:  
Description: A Job creates one or more Pods and ensures they successfully terminate. CronJob is a time-based Job scheduler.Use Case: Running batch processes and scheduled tasks.    
**26.List resource you know in kubernetes?
Answer**In Kubernetes, resources refer to the computational units (CPU and memory) that are allocated to containers running in Pods. The allocation of resources helps in defining the capacity and constraints of a Kubernetes cluster. Here are some key resources in Kubernetes:
CPU (Central Processing Unit):  
Description: The processing power allocated to a container or Pod.Resource Definition: Specified in terms of CPU units (e.g., "500m" represents 500 milliCPU or half a core).  
Memory:  
Description: The amount of RAM allocated to a container or Pod.Resource Definition: Specified in terms of bytes (e.g., "256Mi" represents 256 megabytes).
Storage:  
Description: Represents the amount of storage allocated to a container or Pod.  Resource Definition: Configured using Persistent Volumes (PVs) and Persistent Volume Claims (PVCs) for persistent storage needs.  
GPU (Graphics Processing Unit):  
Description: Specialized hardware resource for offloading graphic and parallel computation tasks.Resource Definition: Allocated to containers requiring GPU acceleration.  
Ephemeral Storage:  
Description: Represents temporary storage that is associated with a node but not persisted across restarts.Resource Definition: Configured based on the node's available ephemeral storage.  
Network Bandwidth:  
Description: Represents the rate of data transfer over the network.Resource Definition: Configured based on network policies and bandwidth requirements.
Number of Pods:  
Description: Represents the count of Pods running within a specific namespace or cluster.Resource Definition: Used for managing the overall load on the cluster.  
Number of Nodes:  
Description: Represents the count of worker nodes in the Kubernetes cluster.
Resource Definition: Used for managing the overall cluster capacity.
Number of CPU Cores:  
Description: Represents the total number of CPU cores available in the cluster.
Resource Definition: Used for capacity planning and resource allocation.
Number of GPUs:  
Description: Represents the total number of GPUs available in the cluster.
Resource Definition: Used for scheduling containers that require GPU acceleration.
Node Selector:  
Description: Allows Pods to be scheduled onto nodes based on node labels.
Resource Definition: Configured in Pod specifications to define node affinity.
Resource Quotas:  
Description: Limits the aggregate resource consumption in a namespace.
Resource Definition: Set quotas for CPU, memory, storage, and other resources within a namespace.
LimitRange:  
Description: Sets default resource requests and limits for containers within a namespace.
Resource Definition: Helps in preventing resource exhaustion and ensuring fair resource allocation.
These resources are critical for managing and optimizing the performance, scalability, and reliability of applications running in a Kubernetes cluster. Kubernetes allows users to define and manage these resources to ensure efficient resource utilization and maintain the health of the cluster.
