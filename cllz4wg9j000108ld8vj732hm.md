---
title: "Docker Project  for Devops Engineer"
datePublished: Thu Aug 31 2023 12:20:23 GMT+0000 (Coordinated Universal Time)
cuid: cllz4wg9j000108ld8vj732hm
slug: docker-project-for-devops-engineer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693420298113/b235e709-68be-48d8-8bfc-0cca5d9decdc.png
tags: docker, docker-images, trainwithshubham, 90daysofdevops-chanllenge, dockerprojects

---

# **Dockerfile**

A Dockerfile is like a recipe that provides instructions to create a consistent and isolated environment for running your application within a Docker container. It's a text file containing a series of commands that define how to assemble an image, which is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, libraries, and settings.

## Detailed breakdown of attributes in Dockerfile:

**FROM base\_image:tag** -&gt; The `FROM` instruction specifies the base image that your image will be built upon

**WORKDIR /app** -&gt; Set the working directory inside the container

**COPY source destination** -&gt; Copy files or directories from host to container

**RUN command** -&gt; Run a command inside the container

**ENV key=value** -&gt; Set Environment Variables

**EXPOSE port\_number** -&gt; Expose a port on the container

**CMD \["executable", "arg1", "arg2"\]** -&gt; Define a command to run when the container starts/ready

**LABEL key=value** -&gt; Optionally, specify metadata about the image (labels, author, etc)

**RUN package\_manager install package\_name** -&gt; Install dependencies (Specific to the base image package manager)

**USER username** -&gt; Specify the user that the container should run as

### **Task:**

* Create a Dockerfile for a simple web application (e.g. a Node.js or Python app)
    
* Build the image using the Dockerfile and run the container
    
* Verify that the application is working as expected by accessing it in a web browser
    
* Push the image to a public or private repository (e.g. Docker Hub )
    

1. **Create a Directory:** Create a directory for your Node.js app. For example, let's call it `python-app`.
    
2. **Navigate to the Directory:** Open a terminal and navigate to the `python-app` directory.
    
3. **Create the Python Code:** Inside the `python-app` directory, create a file named [`app.py`](http://app.py) and add the following content to create a basic Python web server:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693479476839/c9f61aa1-7d1c-46e6-a20e-4264f90fd466.png align="center")
    
4. **Create a Dockerfile:** In the same directory, create a file named `Dockerfile` and add the following content:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693479659754/10827129-81e6-419c-ae47-7fe33e721dc1.png align="center")
    
5. **Build and Run Docker Container:** In the terminal, navigate to the `python-app` directory and run the following commands:
    
    Build the image:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693479567424/17f518b1-3340-40cd-b3d8-913fe066bc39.png align="center")
    
    Create a container:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693479586557/0e7db59a-2b91-46f3-86fd-59b1d4e7d4a0.png align="center")
    
6. This example demonstrates a simple Python web server running inside a Docker container. The `-p 8080:8080` flag maps port 8080 on your host machine to port 8080 inside the Docker container. You can access the app by navigating to [`http://ec2-public-ip-address:8080`](http://localhost:8080) in your web browser.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693480585096/96a70ee0-80b0-4e1b-bff2-f6468f698738.png align="center")
    

# **Push the Docker image to a public or private repository (e.g., Docker Hub):**

1. **Push to Docker Hub**
    

To share your Docker image with others, you can push it to Docker Hub. Make sure you're logged in to Docker Hub, using `docker login` and then push the image:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693484233383/4cfd24c3-9ed7-4bf3-9141-0627af5c585b.png align="center")

Once you have logged in, tag the image with the repository’s name and push it using the following commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693484264011/36c05756-35ad-42ae-90d1-b50a66d92353.png align="center")

Now Verify the docker hub. docker image pushed your docker hub account.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693484273951/674b7b54-c95b-40e3-b011-c02e74a556ec.png align="center")