---
title: "Docker Interview Questions"
datePublished: Tue Sep 12 2023 13:53:57 GMT+0000 (Coordinated Universal Time)
cuid: clmgdj064000109ij7jzj2z7o
slug: docker-interview-questions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694448179468/7ef7ffab-5864-480b-99cd-9c09d3865887.png
tags: day21, trainwithshubham, docker-interview-questions

---

1. **What is the Difference between an Image, Container, and Engine?**
    
    Ans:
    
    **Docker Image**: A blueprint that contains all the necessary libraries, dependencies, and code to run a service or an app. Docker Image is built from a configuration file called Dockerfile. Docker images are also stored in a Registry called DockerHub where predefined images of services are kept in a repository with various tags. These tags indicate the version of that service.
    
    **Docker Container**: It is a running instance of a Docker Image. Docker Image is a blueprint containing instructions on how to run the app. Container is an isolated environment that runs the service and is deployed on the server.
    
    **Docker Engine**: It is a software or a program that sits on top of the Host Operating system that allows us to run multiple containers on the host machine. Docker Engine consists of two parts:
    
    1. **Docker Daemon**: It is a background process that manages the containers, networking, and storage for containers, and uses a low-level service called container d (daemon) that creates, removes, and schedules the container.
        
    2. **Docker CLI**: It is a command Line Interface that helps us run Docker commands to perform various docker-related tasks.
        
2. **What is the Difference between the Docker command COPY vs ADD?**
    
    **COPY**: The `COPY` command is straightforward and is primarily used to copy local files and directories from the host machine into the image. It takes two arguments: the source path on the host and the destination path in the image. It doesn't perform any extraction or manipulation of the files being copied. It's a safer choice when you want a simple copy operation without any extra processing.
    
    Example:
    
    ```bash
    COPY app.py /data
    ```
    
    **ADD**: The `ADD` command is more versatile and can do everything that `COPY` does and more. In addition to copying files, it can also extract compressed files (tar, gzip, bzip2) and retrieve remote files from URLs. It also supports automatically extracting compressed files and copying over URL resources into the destination directory. Because of this added functionality, it's important to be cautious with `ADD` to avoid unexpected behavior.
    
    Example of copying and extracting:
    
    ```bash
      ADD app.tar.gz /usr/src/
    ```
    
    Example of copying remote URL:
    
    ```bash
      ADD https://example.com/myfile.txt /usr/src/
    ```
    
    **ADD**: It can be used to directly download and extract an archive from a URL or pulling code from a version control repository.
    
3. **What is the Difference between the Docker command CMD vs RUN?**
    
    **RUN**: It is used to run the commands while building the Docker image. These commands generally include downloading libraries, dependencies, runtime environment, and running some test cases that are necessary to ensure the app is running when deployed in a container. The commands mentioned using each RUN keyword act as a different layer while building the Docker image, therefore it is a good practice to put all the required commands that can be grouped in a single RUN keyword that helps in reducing the layers while building a Docker Image.
    
    ```bash
      RUN apt-get update && apt-get install -y python3
    ```
    
    **CMD**: In this keyword, we mention the commands that we want to run while the container is being deployed. These can include commands for post-build actions that can include sending a message, giving a prompt, etc.
    
    ```bash
      CMD ["python", "app.py"]
    ```
    
    While `RUN` is typically used for setup tasks that affect the image inside the container, `CMD` is used to define what the container should do when it's run when it starts/ready.
    
4. How will you reduce the size of the Docker image?
    
    Reducing the size of a Docker image is essential to optimize performance, minimize storage usage, and enhance the efficiency of image distribution. Here are some techniques to achieve this:
    
    1. **Use a Smaller Base Image**: Choose a minimal and lightweight base image for your application. Alpine Linux is a popular choice as it's small and efficient.
        
    2. **Multi-Stage Builds**: Utilize multi-stage builds to separate the build environment from the runtime environment. This allows you to copy only the necessary artifacts from the build stage to the final image.
        
    3. **Minimize Layers**: Reduce the number of layers in your image by chaining multiple commands together using the `&&` operator. Each layer adds to the image size, so combining commands can reduce the number of layers.
        
        ```bash
         RUN apt-get update && apt-get install -y package1 package2 && apt-get clean
        ```
        
    4. **Use Specific Package Versions**: Specify exact package versions to ensure consistency and avoid installing unnecessary dependencies.
        
    5. **Cleanup**: Remove temporary files and package caches after installation to reduce the image size. Use the `RUN` command with `apt-get clean`, `yum clean all`, or similar commands.
        
    6. **Avoid Unnecessary Files**: Be selective about which files and directories are included in the image. Exclude unnecessary logs, documentation, and other artifacts that aren't required at runtime.
        
    7. **Compress Files**: Compress files that are copied into the image. For example, use `gzip` to compress log files before copying them.
        
    8. **Use .dockerignore**: Create a `.dockerignore` file to exclude files and directories that shouldn't be included in the image, such as build artifacts or cached files.
        
    9. **Remove Unneeded Users**: Remove any unused or unnecessary users from the image to reduce its size.
        
    10. **Use Minimal Base Images**: Instead of full-featured base images, opt for minimal ones that only contain the necessary components for your application.
        
    11. **Avoid Unnecessary Tools**: Remove any tools or binaries that aren't needed for the application to run.
        
    12. **Optimize Dockerfile Instructions**: Carefully order the instructions in your Dockerfile to take advantage of caching mechanisms and minimize layer changes.
        
        By implementing these techniques, you can significantly reduce the size of your Docker images while ensuring your application's functionality remains intact.
        
5. **Why and when to use Docker?**
    
    Docker is ideal for scenarios where a microservice architecture is implemented. Since it provides isolation, and virtualization and also is a better alternative than virtual machines. Since docker is lightweight, it uses a Host kernel for performing tasks rather than downloading the whole OS.
    
    Docker is a powerful tool for containerization, offering numerous advantages for various scenarios:
    
    1. **Microservices Architecture:** Docker is well-suited for microservices-based applications. It allows you to package each component of your application as a separate container, enabling easy deployment, scaling, and management of individual services.
        
    2. **Isolation and Consistency:** Docker containers provide process-level isolation, ensuring that applications run in their own isolated environments. This isolation improves security and prevents conflicts between applications that share the same host.
        
    3. **Portability:** Docker containers encapsulate the application and its dependencies, including libraries and configurations. This "containerized" format makes applications highly portable across different environments, from development to production.
        
    4. **Efficiency and Resource Utilization:** Compared to traditional virtual machines, Docker containers share the host system's OS kernel, resulting in less overhead. Containers are lightweight and start up quickly, enabling efficient use of resources.
        
    5. **Development and Testing:** Docker simplifies development and testing by providing consistent environments across various stages of the development lifecycle. Developers can build containers locally that closely resemble the production environment.
        
    6. **Continuous Integration/Continuous Deployment (CI/CD):** Docker plays a vital role in CI/CD pipelines. You can define the application's environment in a Dockerfile, ensuring that the same environment is used for testing and deployment, reducing "it works on my machine" issues.
        
    7. **Scalability and Load Balancing:** Docker containers can be easily scaled up or down to handle varying loads. Container orchestration tools like Kubernetes and Docker Swarm make managing and scaling containerized applications seamless.
        
    8. **Version Control and Rollbacks:** Docker images are versioned, enabling you to track changes and roll back to previous versions if needed. This simplifies version control and makes application updates more manageable.
        
6. Explain the Docker components and how they interact with each other.
    
    Docker has several components that work together to provide a platform for packaging, deploying, and running applications in containers. These components include:
    
    **Docker Engine:** The Docker Engine is the underlying technology that runs and manages the containers. It is responsible for creating, starting, stopping, and deleting containers, as well as managing their networking and storage.
    
    **Docker Daemon**: The Docker Daemon is the background service that communicates with the Docker Engine. It receives commands from the Docker CLI and performs the corresponding actions on the Docker Engine.
    
    **Docker CLI:** The Docker Command Line Interface (CLI) is a command-line tool that allows users to interact with the Docker Daemon to create, start, stop, and delete containers, as well as manage images, networks, and volumes.
    
    **Docker Registries**: A Docker Registry is a place where images are stored and can be accessed by the Docker Daemon. Docker Hub is the default public registry, but you can also use private registries like those provided by Google or AWS.
    
    **Docker Images**: A Docker Image is a lightweight, stand-alone, executable package that includes everything needed to run a piece of software, including the code, a runtime, libraries, environment variables, and config files.
    
    **Docker Containers:** A Docker Container is a running instance of an image. It is a lightweight, standalone, and executable software package that includes everything needed to run the software in an isolated environment.
    
    Users interact with the Docker Client, which communicates with the Docker Daemon. The Docker Daemon, in turn, manages images, containers, and other resources, using the Docker Engine.
    
    **Interaction:**
    
    * The Docker Client communicates with the Docker Daemon using the Docker API.
        
    * Docker Images are built using the Docker Client, and they can be stored in Docker Registries.
        
    * Docker Containers are created from Docker Images using the Docker Client and run on the Docker Daemon.
        
    * Containers can communicate with each other using Docker Networks, and they can store and retrieve data using Docker Volumes.
        
    * Docker Compose uses the Docker Client to manage multi-container applications based on a Compose file.
        
7. **Explain the terminology: Docker Compose, Docker File, Docker Image, Docker Container?**
    
    **1\. Docker Compose:** Docker Compose is a tool that allows you to define and run multi-container applications. It uses a YAML file to specify the services, networks, and volumes required for your application. With Docker Compose, you can define the entire application stack in a single file and manage its deployment and orchestration. It simplifies the process of setting up and running complex applications that consist of multiple interconnected services.
    
    **2\. Docker File:** A Dockerfile is a text file that contains a set of instructions for building a Docker image. It provides a recipe for creating an image by specifying the base image, adding application code, setting up configurations, installing dependencies, and defining runtime settings. Dockerfiles are used as input to the `docker build` command to create a Docker image. They allow you to automate and reproduce the process of creating consistent and reproducible images for your applications.
    
    **3\. Docker Image:** A Docker image is a lightweight, portable, and self-sufficient snapshot of an application and its environment. It contains all the necessary code, runtime, libraries, dependencies, and configurations needed to run the application. Images are built from Dockerfiles and can be stored in Docker registries. Images are read-only, making them reusable across different environments. They serve as the basis for creating Docker containers.
    
    **4\. Docker Container:** A Docker container is a runnable instance of a Docker image. It represents an isolated environment that encapsulates the application and its dependencies. Containers share the host operating system's kernel but run in separate process spaces, ensuring isolation and consistency. Containers are ephemeral, meaning they can be easily created, started, stopped, and destroyed. They provide a consistent runtime environment across different systems and make applications portable and reproducible.
    
8. In what real scenarios have you used Docker?
    
    **Microservices Architecture:** Docker is often used to containerize individual microservices within a larger application. This approach enables better isolation, scalability, and maintainability of each component. I have used Docker-compose while containerizing a 2-tier flask web application.
    
    **Continuous Integration/Continuous Deployment (CI/CD):** Docker is integrated into CI/CD pipelines to build, test, and deploy applications automatically. Containers provide a consistent environment for testing and deploying code changes. I have integrated Docker with Jenkins while building a CI/CD pipeline for a 2-tier flask application.
    
9. Docker vs Hypervisor?
    
    **Docker VS Virtual Machine:**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694523374203/cdd88f80-0b44-4391-84c2-eb1dd65c4497.png align="center")
    
    Docker and Hypervisor are both technologies used for virtualization, but they have key differences:
    
    * Docker: Uses containerization to run applications with shared OS resources, making it lightweight and efficient. Containers share the host OS kernel, reducing overhead and improving performance.
        
    * Hypervisor: Virtualizes the entire operating system, allowing multiple virtual machines to run on a single physical host. Each VM requires its own OS kernel, resulting in higher resource consumption compared to Docker containers.
        
    
    Docker's lightweight and portable approach is excellent for microservices and containerized applications, while hypervisors are more appropriate for scenarios requiring strong isolation between applications or support for multiple operating systems on a single machine.
    
10. What are the advantages and disadvantages of using docker?
    
    <table><tbody><tr><td colspan="1" rowspan="1"><p><strong><mark>Advantage</mark></strong></p></td><td colspan="1" rowspan="1"><p><strong><mark>Disadvantage</mark></strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>Consistency and isolation,</p></td><td colspan="1" rowspan="1"><p>Limited OS compatibility,</p></td></tr><tr><td colspan="1" rowspan="1"><p>Resource efficiency,</p></td><td colspan="1" rowspan="1"><p>Security concerns,</p></td></tr><tr><td colspan="1" rowspan="1"><p>Rapid deployment,</p></td><td colspan="1" rowspan="1"><p>No automatic backup and Complexity of orchestration.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Version control and Environment reproducibility</p></td><td colspan="1" rowspan="1"><p></p></td></tr></tbody></table>
    
11. What are the advantages and disadvantages of using docker?
    
    Advantages:
    
    * Isolation: Containers provide a secure and isolated environment for running applications.
        
    * Portability: Docker images can run on any system with Docker installed, providing consistency across environments.
        
    * Scalability: Containers can be easily scaled up or down based on demand.
        
    * Rapid Deployment: Docker allows quick and automated application deployment.
        
    * Simplified Management: Docker provides tools for easy container management.
        
    
    Disadvantages:
    
    * Learning Curve: Understanding Docker and its components might require time and effort.
        
    * Limited GUI Support: Docker primarily focuses on command-line interfaces.
        
    * Security Concerns: Misconfigured containers can pose security risks.
        
    * Container Sprawl: Poor management may lead to an excessive number of containers.
        
12. **What is a Docker namespace?**
    

Docker namespaces are a technology used to provide isolation for various resources within a container. Each container has its own unique namespace, meaning that the processes running inside a container cannot see processes in other containers or the host system. Namespaces isolate process IDs, network interfaces, mount points, users, and more, making containers secure and independent.

1. **What is a Docker registry?**
    

A Docker registry is a repository that stores Docker images. It serves as a central location where developers can push and pull images. Public Docker registries like Docker Hub are freely accessible by anyone, while private registries can be used for internal image sharing within organizations.

1. **What is an entry point?**
    

An entry point in Docker refers to the command that is executed when a container is launched from an image. It serves as the primary command or executable that runs within the container's environment. The entry point defines the initial process that starts when the container starts, and any arguments provided are passed to this command.

Using an entry point in a Docker image allows you to specify a default behavior for the container when it's launched. This is particularly useful when you want to ensure that a specific application or script runs automatically when the container starts.

In a Dockerfile, you can define the entry point using the `ENTRYPOINT` instruction. For example:

```bash
  FROM ubuntu:latest
  ENTRYPOINT ["python3", "app.py"]
```

In this case, when a container is created from the image, it will automatically execute the [`app.py`](http://app.py) script using the Python 3 interpreter as the entry point. Any additional arguments provided when running the container will be passed as arguments to the [`app.py`](http://app.py) script.

1. **How to implement CI/CD in Docker?**
    

To implement CI/CD in Docker, you can use a combination of tools like Jenkins, GitLab CI/CD, or Travis CI along with Docker. Here's a basic outline:

1. Set up a CI/CD pipeline using your preferred CI/CD tool.
    
2. Configure the pipeline to build a Docker image during the build phase.
    
3. Push the built image to a Docker registry as an artifact.
    
4. Use Docker Compose or Kubernetes to deploy the image to the target environment during the deployment phase.
    

1. **Will data on the container be lost when the Docker container exits?**
    

By default, data on a Docker container will be lost when the container exits. Containers are designed to be ephemeral and disposable. However, you can use Docker volumes or bind mounts to persist data outside the container, ensuring that it is retained even after the container is stopped or removed.

1. **What is a Docker swarm?**
    

Docker Swarm is a native clustering and orchestration solution for Docker. It allows you to create and manage a swarm of Docker nodes (hosts) as a single virtual system. Docker Swarm enables high availability, load balancing, and easy scaling of services across multiple nodes, making it suitable for deploying and managing containerized applications in a distributed environment.

1. **What are the docker commands for the following:**
    
    * view running containers
        
        ```bash
          docker ps
        ```
        
    * command to run the container under a specific name
        
        ```bash
          docker run --name container_name image_name
        ```
        
    * command to export a docker
        
        ```bash
          docker export container_id > container.tar
        ```
        
    * command to import an already existing docker image
        
        ```bash
          docker import container.tar image_name:tag
        ```
        
    * commands to delete a container
        
        ```bash
          docker rm container_id
        ```
        
    * command to remove all stopped containers, unused networks, build caches, and dangling images?
        
        ```bash
          docker system prune -a
        ```
        
2. **What are the common docker practices to reduce the size of Docker Image?**
    
    \-Use a Minimal Base Image: `Start with a minimal base image, such as Alpine Linux, to reduce the initial image size`
    
    \-Multi-Stage Builds: `This helps discard unnecessary build dependencies, resulting in a smaller final image.`
    
    \-Minimize Layers: `Reduce the number of layers in your Dockerfile. Combine multiple RUN commands into a single command.`
    
    \-Minimize Image Layers: `Avoid installing software, copying files, and running commands in separate layers if they can be combined.`  
    \-Remove Unnecessary Dependencies:`Avoid installing packages or dependencies that your application doesn't need.`
    
    \-Clean Up after installation: `Remove temporary files, caches, and unnecessary artifacts after each build step to minimize the size of the final image.`
    
    \-Use .dockerignore:`Use a .dockerignore file to exclude unnecessary files and directories from being copied into the image during the build process.`  
    \-Use COPY Instead of ADD: `Use the COPY command instead of ADD to copy files into the image. COPY only handles local files, which is safer and more predictable.`  
    \-Avoid running unnecessary services:`Minimize services and processes running in the container, only including what's essential for the application to function.`