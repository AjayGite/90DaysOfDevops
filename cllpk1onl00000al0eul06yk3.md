---
title: "Docker for DevOps Engineers"
datePublished: Thu Aug 24 2023 19:26:40 GMT+0000 (Coordinated Universal Time)
cuid: cllpk1onl00000al0eul06yk3
slug: docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692904776030/7be57e79-879e-4b72-9a18-8905214ac870.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692905186341/06dc0fd9-4771-436c-812a-a3f4f58089c6.png
tags: docker, day16, trainwithshubham

---

### **What is Docker?**

* Docker is a platform-as-a-service product that uses OS-level virtualization to deliver software in packages called containers.
    
* Containers are isolated from one another and are bundled in their own software, and they can communicate with each other through well-defined channels.
    

### **Docker VS Virtual Machine:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692786011330/8d788112-1ceb-47fc-a951-2b6ee2de4ffd.png align="center")

### **Docker Lifecycle:**

1. Develop your application and its supporting components using containers.
    
2. The container becomes the unit for distributing and testing your application.
    
3. When you’re ready, deploy your application into your product environment, as a container or an orchestrated service. This works the same whether your production environment is a local data centre, a cloud provider, or a hybrid of the two.
    

### **Docker Engine:**

Docker Engine is a service that allows you to run any container be it Linux, MacOS or Windows on any kind of host OS which uses two main components - dockerd and docker cli.

### **Docker Daemon (dockerd):**

The Docker daemon (dockerd) is the core background service that runs on the host machine. It is responsible for managing containers, images, volumes, and networks using a low level service called (containerd). The daemon handles all the requests from the Docker client, manages the container's lifecycle, and ensures the isolation and resource allocation of containers.

### **Docker Client:**

The Docker client is the command-line tool or API that allows users to interact with the Docker daemon. It sends commands to the Docker daemon, which, in turn, executes them. The client can run on the same machine as the daemon or connect to a remote Docker daemon running on another host.

# **Tasks**

* Installation of Docker on Ubuntu - Run the below commands to install docker:
    
    ```bash
    sudo apt update
    sudo apt install docker.io -y
    ```
    

1. **Docker Run** - Starting a Container: The `docker run` a command is your gateway to launching containers. It allows you to create and run a container from an image. Let's start with the famous "Hello World" example:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692892958888/f721fb3d-e816-4644-a6de-373da8d1bdc4.png align="center")
    
    While running the command to create a container, you will face this issue. Then you need to add the current user to the docker group.
    
    ```bash
    sudo usermod -aG docker $USER
    sudo cat /etc/group | grep docker
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692893150104/89824d0a-d423-4e60-91de-d764c4eb5196.png align="center")
    
    **Docker Run** - Starting a Container: The `docker run` a command is your gateway to launching containers. It allows you to create and run a container from an image. Let's start with the famous "nginx" example:
    
    ```bash
    docker run -it -d -p 80:80 nginx:latest
    docker ps
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692903945946/e6da55fb-f765-4cfe-b2c8-22912e625e7f.png align="center")
    
    This command fetches the "nginx" image from Docker Hub and runs it, confirming that your Docker installation is working correctly.
    
    \-it -&gt; To make it interactive
    
    \-d -&gt; detached and to keep running in the background even after not accessing the container.
    
    **Docker Inspect** - Detailed Container Information: For a deep dive into container or image details, use `docker inspect`. You can inspect a specific container or image by providing its name or ID:
    
    ```bash
    docker inspect <container_name_or_id> 
    docker inspect <image_name_or_id>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692904363030/41ca2dec-e59e-4e99-b569-00a4183bb63c.png align="center")
    
    **Docker Port** - Listing Port Mappings: When dealing with containers, you often need to know which ports are mapped. The `docker port` command helps you list the port mappings for a specific container
    
    ```bash
    docker port <container_name_or_id>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692904475405/fc4a159b-5221-43bc-9451-dfb39b5838c6.png align="center")
    
    **Docker Stats** - Resource Usage Statistics: To monitor the resource usage of one or more containers in real-time, use the `docker stats` command:
    
    ```bash
    docker stats <container_name_or_id>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692904601027/6ab62906-ab6e-4dac-bbeb-945f5d34053a.png align="center")
    
    This command displays CPU, memory, network I/O, and block I/O statistics, helping you optimize resource allocation.
    
    **Docker Top** - Viewing Container Processes: Sometimes, you need to check the processes running inside a container. The `docker top` command allows you to do just that:
    
    ```bash
    docker top <container_name_or_id>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692904662605/9de24f32-d60e-4108-a8b8-df7d85bc50fb.png align="center")
    
    This gives you insights into the processes within the container, aiding in debugging and performance tuning.
    
    **Docker Save** - Saving an Image to a Tar Archive: With `docker save`, you can export Docker images to a tar archive for sharing or backup purposes:
    
    ```bash
    docker save -o <output_file_name>.tar <image_name>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692904927392/3d3aadb3-96e1-4310-b3f6-b74455352596.png align="center")
    
    This command saves the specified image to a tar file.
    
    **Docker Load** - Loading an Image from a Tar Archive: To load an image from a previously saved tar archive, use the `docker load` command:
    
    ```bash
    docker load -i <input_file_name>.tar
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692905108353/92b661a8-9e25-431b-8051-51ac37a68a5d.png align="center")
    
    # **Conclusion ✨**
    
    There you go! You've just scratched the surface of Docker. Mastering Docker commands is essential for DevOps enthusiasts. These commands, though seemingly complex, are the building blocks of container orchestration and management.
    
    Keep experimenting, and remember, every DevOps journey begins with a single step. Stay curious, and soon you'll be orchestrating containers like a pro.
    
    Stay tuned for more DevOps demystification on my 90 Days of DevOps Challenge!
    
    Happy DevOps learning!✍