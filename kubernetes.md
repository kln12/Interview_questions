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
