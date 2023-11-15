**1.how can we reduce docker image**   
**Answer:**    https://devopscube.com/reduce-docker-image-size/   
**2.Define docker Engine**   
**Answer:**  Docker Engine is an open source containerization technology for building and containerizing your applications. Docker Engine acts as a client-server application with:    
A server with a long-running daemon process dockerd.   
APIs which specify interfaces that programs can use to talk to and instruct the Docker daemon.   
A command line interface (CLI) client docker.   
**4. CMD vs RUN**  
**Answer:**  RUN is an image build step, the state of the container after a RUN command will be committed to the container image. A Dockerfile can have many RUN steps that layer on top of one another to build the image.   
CMD is the command the container executes by default when you launch the built image. A Dockerfile will only use the final CMD defined. The CMD can be overridden when starting a container with docker run $image $other_command.   
ENTRYPOINT is also closely related to CMD and can modify the way a CMD is interpreted when a container is started from an image.   
**5.Entrypoint vs    
5.where docker container are stored**  
**Answer:**  Docker containers are stored in a location on your host machine's filesystem. The default location can vary depending on the operating system, but typically, Docker containers are stored in the /var/lib/docker     
**6.in docker (. dot ) in docker build and what can if we remove  
Answer:** In Docker, the dot (.) in the docker build command represents the build context, which is the directory on your host machine where the Dockerfile and any additional files required for the build are located."docker build -t <image-name> <build-context>"   
 if your Dockerfile and other build-related files are located in the current directory (the directory you are in when you run the command), you can specify the build context as .:docker build -t my-image .   
 If you remove the dot (.) and do not specify a build context, Docker will assume the current directory as the default build context. So, if you're already in the directory containing the Dockerfile and other necessary files, "docker build -t my-image"   
**7.Difference between docker stop and docker kill? 8.What version of docker you have used? Speciic reason to use that particular version?  
Answer**
**9.Can we have multiple CMD in Dockerfile?  
Answer** we can have multiple CMD instructions, but only the last CMD instruction will take effect. 
FROM ubuntu:latest

CMD ["echo", "This is the first CMD instruction"]
CMD ["echo", "This is the second CMD instruction"]

**10.What is the difference between ADD and COPY docker instructions in Dockerfile?  
Answer** the major difference is that ADD can do more than COPY 
ADD allows <src> to be a URL 
If is a local tar archive in a recognized compression format (identity, gzip, bzip2 or xz) then it is unpacked as a directory. Resources from remote URLs are not decompressed. 
COPY where the magic of ADD is not required. Otherwise, you (since you had to look up this answer) are likely to get surprised someday when you mean to copy keep_this_archive_intact.tar.gz into your container, but instead, you spray the contents onto your filesystem. 
![image](https://github.com/kln12/Interview_questions/assets/58560303/6e6f5a1e-a7e7-4516-b1c2-17643f5d800a)

**11.Types of network in docker? if you dont specify network to deploy on which network the conatiner will be created?  
Answer** Docker provides several types of networks that containers can be connected to. The default behavior when you don't specify a network for a container to be deployed on is to use the default bridge network.   
Here are some of the common network types in Docker:   
Bridge Network: The default network created on every Docker host. Containers attached to this network can communicate with each other and with the host. It's isolated from the host's external network.   
Host Network: When a container is connected to the host network, it shares the network namespace with the host, giving it full access to the host's network interfaces. This can be useful for high-performance scenarios but sacrifices network isolation.   
Overlay Network: Used in Docker Swarm mode for container communication across multiple hosts. Overlay networks facilitate communication between containers in a multi-host setup.   
Macvlan Network: Allows containers to be directly attached to a physical network interface, essentially giving containers their own MAC and IP addresses. 
None Network: Containers attached to this network have no network connectivity. It's useful in scenarios where you want to run a container without any network access.   
Custom User-Defined Networks: You can create your own user-defined networks to isolate groups of containers or for specific use cases. These networks can be configured with specific IP ranges and other settings.   
By default, if you don't specify a network when starting a container, it will be connected to the default bridge network. You can specify a network using the --network option when running a container, and you can also create custom user-defined networks to better control and isolate container communication in your applications. 

**12.Explain a sample dockerfile that you have used in your project?  
Answer**  
**13.How Docker containers troubleshoot the issue?**
