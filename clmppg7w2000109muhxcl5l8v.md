---
title: "Jenkins Freestyle Project for DevOps Engineers"
datePublished: Tue Sep 19 2023 02:37:38 GMT+0000 (Coordinated Universal Time)
cuid: clmppg7w2000109muhxcl5l8v
slug: jenkins-freestyle-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694934065936/3b665f51-2181-47f2-b0aa-98952301b956.png
tags: jenkins, 90daysofdevops, day23, trainwithshubham, jenkinsproject

---

### **What is CI/CD?**

CI/CD stands for Continuous Integration and Continuous Delivery (or Deployment). Continuous Integration is the practice of frequently merging code changes into a shared repository. It involves automating the build, unit testing, and code quality checks to detect issues early. Continuous Delivery focuses on automating the deployment process to make software releases ready for production at any time.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694934129350/8c1ff249-34b9-4bb3-b268-7f49dbced3b0.jpeg align="center")

### **What Is a Build Job?**

A Jenkins build job contains the configuration for automating a specific task or step in the application building process. These tasks include gathering dependencies, compiling, archiving, or transforming code, and testing and deploying code in different environments.

Jenkins offers a diverse array of build job types to cater to different needs:

1. **Freestyle Projects:** These projects provide flexibility in configuring build steps and are suitable for simpler tasks or projects.
    
2. **Pipelines:** Pipelines offer more advanced capabilities, enabling the definition of complex workflows using script-based approaches.
    
3. **Multi-Configuration Projects:** These projects are designed for testing on multiple configurations, such as different operating systems.
    
4. **Folders:** Folders help organize jobs into logical groups, enhancing the management of larger projects.
    
5. **Multibranch Pipelines:** This type is used when managing multiple branches in a source code repository, automating builds for each branch.
    
6. **Organization Folders:** Ideal for overseeing numerous projects across diverse repositories within an organization.
    

In essence, Jenkins build jobs serve as the backbone of automation in software development. They empower developers and teams to automate repetitive tasks, streamline code building and testing, and ensure consistent and reliable outcomes. By leveraging various build job types based on project complexity and requirements, development teams can optimize workflows, enhance efficiency, and maintain high software quality throughout the development lifecycle.

### **What is Freestyle Projects ?? 🤔**

A Freestyle Project in Jenkins allows you to create a job without adhering to a strict pipeline structure. It provides a graphical user interface (GUI) where you can configure various build steps, triggers, post-build actions, and more. This approach is especially useful for projects that don't follow a standard build and deployment process or for teams that prefer a more manual and ad-hoc approach to setting up their automation tasks.

### **Task 01: Creating a Jenkins Freestyle Project with Docker Integration**

1. Launched two instances - One as a Jenkins Master Node and another as an agent.
    
2. Install Jenkins on the Master EC2 instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695039873070/9a05f8f1-6671-414e-b27c-bc9c763c9575.png align="center")
    
3. Create private and public keys via `ssh-keygen` to connect Jenkins Master and Agent server via SSH.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695039990124/9f016785-9857-4166-86af-7205bb0ad028.png align="center")
    
4. Copy the Public key from the Master Server to the Agent Server in the below file.
    
    `cd .ssh/authorized_keys`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695040130703/223983d1-3ded-4148-ab74-0ceeecb0470c.png align="center")
    
5. Log in to your Jenkins dashboard.
    
6. Navigate to "Set up an agent".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695089787147/206f100f-0aa8-41ee-9f93-719c6863a85f.png align="center")
    
7. Click on "New Node" or "New Agent."
    
8. Assign a name to the agent, such as "Todo-App-Dev" or "Docker-Agent".
    
9. Opt for the "Permanent Agent" option.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695089822465/ec3b58d2-dc76-441a-9921-ba422343f487.png align="center")
    
10. Choose "Launch agents via SSH" under "Launch method."
    
11. Copy the Master Private key.
    
12. Define the agent's root directory for storing files.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090047209/af2aef21-fae0-4ed9-a6e0-de187a0043ad.png align="center")
    
13. Save the agent configuration. Here is the successful console output.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090103349/995cea4e-b5d7-41a7-ba92-2728acc8456f.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090134868/40cb0272-6bc3-4ef8-a618-ca247033559a.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090052777/ef10935c-548d-456a-9dd5-ea73f090b5bc.png align="center")
    

**Step 2: Creating a Jenkins Freestyle Project**

1. Access your Jenkins dashboard.
    
2. Click "New Item" to initiate a new project.
    
3. Give the project a name.
    
4. Select "Freestyle project" as the project type.
    
5. Confirm by clicking "OK."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090144726/59bda29a-57c0-430d-bf34-38baf1669786.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090192981/db7118eb-6cd2-494e-b382-3aa0e20254bd.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090199472/56504cf0-65ac-499a-a2c8-6ccc142d6cb1.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090222637/b1419aed-7397-413f-bced-5ee012652f7f.png align="center")
    
    **Step 3: Configuring Build Steps**
    
    1. On the project's configuration page, proceed to the "Build" section.
        
    2. Add a new build step by selecting "Add build step."
        
    3. Opt for "Execute shell" to add a shell script build step.
        
    
    **Step 4: Implementing the "docker build" Command**
    
    Within the shell script build step, include the following commands:
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090433950/dc4b86f1-5beb-4deb-b7c5-030633e9f748.png align="center")
    
    **Step 6: Saving and Triggering the Project**
    
    1. Scroll down and click "Save" to store the project configuration.
        
    2. Click "Build Now" to initiate the project's build process.
        
    
    Jenkins will execute the configured build steps. It will first create the Docker image using the "docker build" command and then initiate a Docker container via the "docker run" command. The container will expose port 8000 from the app to port 8080 on the host.
    
    Ensure 8000 is open on Agent server.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090560809/5d6c61bc-4f74-4515-93b0-6a3368682f71.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090463039/87658bf1-e939-43a2-8ed7-2953509f216e.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090617642/a49d4f18-18b5-4e7d-893e-4b3e2fbd5d88.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090472891/fc21af35-fc62-4d7a-8181-87f666115ab2.png align="center")
    
    ### **Task-02: Jenkins Project for Docker Compose Management**
    
    In this task, your objective is to set up a Jenkins project that effectively utilizes Docker Compose to manage the deployment and cleanup of multiple containers as defined in a compose file.
    
    **Step 1: Preparing Your Jenkins Environment**
    
    Ensure that Docker and Docker Compose are properly installed on your Jenkins server before proceeding.
    
    **Step 2: Creating a Jenkins Freestyle Task**
    
    1. Log in to the Jenkins dashboard.
        
    2. Initiate the creation of a new project by selecting "New Item."
        
    3. Assign a name to your project
        
    4. Opt for "Freestyle project" as the chosen project type.
        
    5. Confirm your selection by clicking "OK."
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090714838/c54eb831-83c7-4970-a51b-4ae1ec8fc61f.png align="center")
        
        **Step 3: Configuring the Build Stages**
        
        1. Within the project's configuration page, navigate to the "Build" section.
            
        2. Choose "Add build step."
            
        3. Opt for "Execute shell" to incorporate a shell script build stage.
            
        
        **Step 4: Executing the "docker-compose up -d" Command**
        
        Inside the shell script build stage, integrate the following commands:
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692070240149/82e32b0c-e0be-4a16-b3ec-1ca9001d9e71.png?auto=compress,format&format=webp align="left")
        
        **Step 6: Saving and Initiating the Project**
        
        1. Scroll down to "Save" and store the project configuration.
            
        2. Initiate the build process by clicking "Build Now."
            
        
        Jenkins will proceed to execute the configured build stages. It will employ the **"docker-compose up -d"** command to activate containers as specified in the **docker-compose.yml** file. Subsequently, it will perform cleanup by discontinuing and removing those containers, all facilitated through the "docker-compose down" command.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090472891/fc21af35-fc62-4d7a-8181-87f666115ab2.png align="left")
        
        Done with both the Tasks.