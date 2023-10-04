---
title: "Jenkins Agents"
datePublished: Wed Oct 04 2023 11:14:42 GMT+0000 (Coordinated Universal Time)
cuid: clnbnixq7000209l9ge2kgyv5
slug: jenkins-agents
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696415599635/b9aee00e-23fd-44a7-901c-2a543d3018e5.png
tags: devops, jenkins, 90daysofdevops, trainwithshubham, jenkins-docker

---

### **Jenkins Master**

The Jenkins master server is the core component that manages configurations, scheduling jobs, and monitoring tasks.

It acts as a control server that coordinates workflows defined in pipelines. The master node handles interactions with agents, scheduling jobs to be executed on them, and collecting results afterwards.

### **Jenkins Agent**

A Jenkins agent is a machine or container that connects to the Jenkins master server. Agents are responsible for executing the steps outlined in a Jenkins job. When creating a Jenkins job, it's necessary to assign an agent to it. Each agent is labeled to provide a unique identifier.

When a Jenkins job is triggered from the master, the execution takes place on the agent node specified in the job configuration. This distribution of work ensures that the master node doesn't get overwhelmed and can focus on controlling the overall process.

For teams with growing needs, Jenkins offers the ability to scale using a **"master-to-agent connection**." This approach allows agents to handle job execution, while the master concentrates on serving the Jenkins UI and managing the workflow.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692898099572/a2f4c1dc-4833-4f1d-a54c-53470ffe1b35.png?auto=compress,format&format=webp align="center")

### **Task 01: Create a Jenkins Agent Node**

1. Launched two instances - One as a Jenkins Master Node and another as an agent.
    
2. Install Jenkins on the Master EC2 instance.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695039873070/9a05f8f1-6671-414e-b27c-bc9c763c9575.png?auto=compress,format&format=webp align="left")
    
3. Create private and public keys via `ssh-keygen` to connect Jenkins Master and Agent server via SSH.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695039990124/9f016785-9857-4166-86af-7205bb0ad028.png?auto=compress,format&format=webp align="left")
    
4. Copy the Public key from the Master Server to the Agent Server in the below file.
    
    `cd .ssh/authorized_keys`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695040130703/223983d1-3ded-4148-ab74-0ceeecb0470c.png?auto=compress,format&format=webp align="left")
    
5. Log in to your Jenkins dashboard.
    
6. Navigate to "Set up an agent".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695089787147/206f100f-0aa8-41ee-9f93-719c6863a85f.png?auto=compress,format&format=webp align="left")
    
7. Click on "New Node" or "New Agent."
    
8. Assign a name to the agent, such as "Todo-App-Dev" or "Docker-Agent".
    
9. Opt for the "Permanent Agent" option.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695089822465/ec3b58d2-dc76-441a-9921-ba422343f487.png?auto=compress,format&format=webp align="left")
    
10. Choose "Launch agents via SSH" under "Launch method."
    
11. Copy the Master Private key.
    
12. Define the agent's root directory for storing files.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090047209/af2aef21-fae0-4ed9-a6e0-de187a0043ad.png?auto=compress,format&format=webp align="left")
    
13. Save the agent configuration. Here is the successful console output.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090103349/995cea4e-b5d7-41a7-ba92-2728acc8456f.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090134868/40cb0272-6bc3-4ef8-a618-ca247033559a.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695090052777/ef10935c-548d-456a-9dd5-ea73f090b5bc.png?auto=compress,format&format=webp align="left")
    
14. Install Jenkins on the master.
    
    ```bash
     sudo apt update
     sudo apt install openjdk-11-jre
     #Install Jenkins
     curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
       /usr/share/keyrings/jenkins-keyring.asc > /dev/null
     echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
       https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
       /etc/apt/sources.list.d/jenkins.list > /dev/null
     sudo apt-get update
     sudo apt-get install jenkins
     #Start jenkins
     sudo systemctl enable jenkins
     sudo systemctl start jenkins
     sudo systemctl status jenkins
    ```
    
15. Install Docker, docker-compose and Java on Jenkins-Slave.
    
    ```bash
     sudo apt install docker.io
     sudo apt install docker-compose -y
     sudo apt install openjdk-11-jre
     sudo usermod -aG docker $USER
     sudo reboot
    ```
    

### **Task 02: Run a Jenkins Job on Agent Node**

1. From the Jenkins dashboard, click on "New Item" to create a new project.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696407974297/95337b0b-849f-4d8d-a213-0989c8c594d8.png?auto=compress,format&format=webp align="left")
    
2. Enter a project name and select "Pipeline" Click "OK" to create the project.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408018466/610538a3-6450-4af4-8e7f-4683a7b24ad5.png?auto=compress,format&format=webp align="left")
    
3. Under the Configuration, Select the GitHub Project checkbox -&gt; Enter the URL and Enabled the GitHub hook trigger for GITScm polling.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408079727/ffabcbbc-df61-4cdf-b26c-af8118c91271.png?auto=compress,format&format=webp align="left")
    

**GitHub WebHooks Setup:**

1. Accessed my repository on GitHub and go to Settings -&gt; Webhooks
    
2. Added a new webhook with my Jenkins job's URL Selected events to trigger (e.g., push, pull request).
    
3. Saved the webhook.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408204201/deeb903d-0b79-4fe9-bbff-143eb3047c49.png?auto=compress,format&format=webp align="left")
    

**Create Environment variable credential for docker hub:**

1. Click on <mark>"manage jenkins"</mark> &gt; <mark>Credentials</mark>.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408250279/3de9a0e8-8885-448a-82da-6c0691eaf76a.png?auto=compress,format&format=webp align="left")
    
2. Click on <mark>"Systum"</mark> &gt; <mark>"</mark>**<mark>Global Credentials(unrestricted)</mark>**<mark>"</mark> &gt; <mark>"Add Credentials"</mark>.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408270799/51c3f79a-65b3-4efb-92a1-21bec20b3167.png?auto=compress,format&format=webp align="left")
    
3. Add the docker hub credentials and click on create
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408305766/ce5669dc-825e-41fb-a282-c819ab67834f.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408312146/d2e22061-3da7-478b-b034-37e35f25a29a.png?auto=compress,format&format=webp align="left")
    

**Running the Application:**

1. Install docker and docker-compose on the server. Add the current user to the `docker` group:
    
    ```bash
     sudo usermod -aG docker $USER 
     sudo reboot
    ```
    
2. Add the Jenkins user to the `docker` group:
    
    ```bash
      sudo usermod -aG docker jenkins
      sudo systemctl restart jenkins
    ```
    
3. Inside the Dashboard <mark>"Node-app"</mark> job &gt; Within the Jenkins job's **<mark>Pipeline</mark>** build step.
    
    ```bash
      pipeline {
          agent {label 'todo-dev'}
    
          stages{
              stage('Clone Code'){
                  steps {
                      echo "Cloning the code"
                      git url:"https://github.com/ajaygite/node-todo-app.git", branch:"master"
                  }
              }
              stage('Build'){
                  steps {
                      echo "Building the Image"
                      sh "docker build -t todo-app ."
                  }
              }
              stage('push to dockerhub'){
                  steps {
                      echo "Pushing the code to dockerhub"
                      withCredentials([usernamePassword(credentialsId:"dockerhub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                      sh "docker tag todo-app ${env.dockerHubUser}/node-app:latest"
                      sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                      sh "docker push ${env.dockerHubUser}/node-app:latest"
                      }
                  }
              }
              stage('Deploy'){
                  steps {
                      echo "Deploying the application"
                      sh "docker-compose down"
                      sh "docker-compose up -d --build"
    
                  }
              }
          }
      }
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408448589/a064cd22-5bce-4865-a695-97ed8b2fe41f.png?auto=compress,format&format=webp align="left")
    
4. Save and click on Build Now.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408535958/d3773859-a588-48a0-a0d0-dce8c8b3e238.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408548013/80f767a3-5903-41f8-bd14-7e44e4ba298e.png?auto=compress,format&format=webp align="left")
    
5. Once done hit the URL [**ipaddress:8000**](http://ipaddress:8000/) to check if it is running.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408599050/44594a32-7a11-4b65-939b-123d4122e8ee.png?auto=compress,format&format=webp align="left")