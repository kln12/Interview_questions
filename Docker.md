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
Answer**
**10.What is the difference between ADD and COPY docker instructions in Dockerfile?  
Answer**
**11.Types of network in docker? if you dont specify network to deploy on which network the conatiner will be created?  
Answer**
**12.Explain a sample dockerfile that you have used in your project?  
Answer**
