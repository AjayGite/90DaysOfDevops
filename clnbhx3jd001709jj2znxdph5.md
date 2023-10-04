---
title: "Jenkins Declarative Pipeline with Docker"
datePublished: Wed Oct 04 2023 08:37:45 GMT+0000 (Coordinated Universal Time)
cuid: clnbhx3jd001709jj2znxdph5
slug: jenkins-declarative-pipeline-with-docker
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696357759586/5c5f11b2-3adf-43a1-924c-de6f351de955.png
tags: 90daysofdevops, trainwithshubham, jenkins-pipeline, day27, jenkins-docker

---

## **Use your Docker Build and Run Knowledge**

**docker build -** you can use `sh 'docker build . -t <tag>'` in your pipeline stage block to run the docker build command. (Make sure you have docker installed with correct permissions.

**docker run:** you can use `sh 'docker run -d <image>'` in your pipeline stage block to build the container.

**How will the stages look:**

```yaml
stages {
        stage('Build') {
            steps {
                sh 'docker build -t trainwithshubham/django-app:latest'
            }
        }
    }
```

# **Task-01**

### **🔹Create Declarative Pipeline with Docker**

1. Install the required plugins to inject the docker hub credentials to set an environment for the builds.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696397310478/a6e800b0-4880-476e-91c1-ca388ced2116.png align="center")
    
2. From the Jenkins dashboard, click on "New Item" to create a new project.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696407974297/95337b0b-849f-4d8d-a213-0989c8c594d8.png align="center")
    
3. Enter a project name and select "Pipeline" Click "OK" to create the project.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408018466/610538a3-6450-4af4-8e7f-4683a7b24ad5.png align="center")
    
4. Under the Configuration, Select the GitHub Project checkbox -&gt; Enter the URL and Enabled the GitHub hook trigger for GITScm polling.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408079727/ffabcbbc-df61-4cdf-b26c-af8118c91271.png align="center")
    

**GitHub WebHooks Setup:**

1. Accessed my repository on GitHub and go to Settings -&gt; Webhooks
    
2. Added a new webhook with my Jenkins job's URL Selected events to trigger (e.g., push, pull request).
    
3. Saved the webhook.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408204201/deeb903d-0b79-4fe9-bbff-143eb3047c49.png align="center")
    

**Create Environment variable credential for docker hub:**

1. Click on <mark>"manage jenkins"</mark> &gt; <mark>Credentials</mark>.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408250279/3de9a0e8-8885-448a-82da-6c0691eaf76a.png align="center")
    
2. Click on <mark>"Systum"</mark> &gt; <mark>"</mark>**<mark>Global Credentials(unrestricted)</mark>**<mark>"</mark> &gt; <mark>"Add Credentials"</mark>.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408270799/51c3f79a-65b3-4efb-92a1-21bec20b3167.png align="center")
    
3. Add the docker hub credentials and click on create
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408305766/ce5669dc-825e-41fb-a282-c819ab67834f.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408312146/d2e22061-3da7-478b-b034-37e35f25a29a.png align="center")
    

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
         agent any
    
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
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408448589/a064cd22-5bce-4865-a695-97ed8b2fe41f.png align="center")
    
4. Save and click on Build Now.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408535958/d3773859-a588-48a0-a0d0-dce8c8b3e238.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408548013/80f767a3-5903-41f8-bd14-7e44e4ba298e.png align="center")
    
5. Once done hit the URL http://ipaddress:8000 to check if it is running.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696408599050/44594a32-7a11-4b65-939b-123d4122e8ee.png align="center")