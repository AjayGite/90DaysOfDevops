---
title: "Integrating Jenkins Freestyle Project with GitHub Webhooks"
datePublished: Sat Sep 23 2023 12:24:12 GMT+0000 (Coordinated Universal Time)
cuid: clmw05xwg000d09md9pxp8lpw
slug: integrating-jenkins-freestyle-project-with-github-webhooks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695469088655/2431f8c8-efa6-49d1-8b35-ebcfcd4a32e5.png
tags: docker, jenkins, 90daysofdevops, trainwithshubham, 90daysofdevopschallenge

---

### **TASK-01:**

* Document the process from cloning the repository to adding webhooks, and Deployment, etc. as a README, go through [**this example**](https://github.com/LondheShubham153/fynd-my-movie/blob/master/README.md)
    
* A well-written readme file will help others to understand your project and you will understand how to use the project again without any problems.
    

### **Prerequisites:**

* You need a running Jenkins server with Java installed.
    
* Docker and Docker Compose should be installed on your system.
    
* You should have a GitHub repository hosting your project's source code.
    

### **Step 1: Create a Jenkins Freestyle Project:**

1. Log in to your Jenkins dashboard.
    
2. Click "New Item" to create a new project.
    
3. Name your project and select "Freestyle project."
    

### **Step 2: Configure Source Code Management:**

**For Private Repositories:** 4. In the project configuration, under "Source Code Management," select your version control system (e.g., Git).

1. Enter your GitHub repository's URL in the "Repository URL" field.
    
2. If it's a private repository, set up authentication in the "Credentials" section.
    

**For Public Repositories:** 7. In the project configuration, under "Source Code Management," select your version control system (e.g., Git).

1. Enter your GitHub repository's URL.
    

### **Step 3: Configure GitHub Webhooks:**

1. Go to your GitHub repository.
    
2. Click on "Settings" in the repository menu.
    
3. Select "Webhooks" from the left sidebar.
    
4. Click on "Add webhook."
    
5. In the "Payload URL" field, enter your Jenkins server's URL followed by `/github-webhook/`, e.g., [`https://your-jenkins-server/github-webhook/`](https://your-jenkins-server/github-webhook/).
    
6. Set the "Content-type" to "application/json."
    
7. Choose the events that should trigger the webhook, typically "Just the push event."
    
8. Click "Add webhook" to save.
    

### **Step 4: Add Current User to Docker Group:**

1. Open a terminal and run the following command (replace `<username>` with your username):
    

```bash
sudo usermod -aG docker <username>
```

### **Step 5: Configure Jenkins Build Triggers:**

1. In your Jenkins project configuration, under "Build Triggers," check "Build when a change is pushed to GitHub."
    

1. Save the project configuration.
    

### **Step 6: Test the Integration:**

1. Push a change to your GitHub repository (e.g., make a code commit).
    

1. Visit your Jenkins dashboard.
    
2. Your Jenkins project should be automatically triggered by the GitHub webhook.
    
3. Monitor the build progress and view build logs in the Jenkins dashboard.
    

### **Step 7: Updating Your Project:**

1. To update your project, execute the following commands in your Jenkins project's "Execute Shell" build step:
    
    ```bash
    docker-compose down
    docker-compose up -d --no-deps --build web
    ```
    

The command `docker-compose up --no-deps --build web` is used to start the `web` service defined in the Docker Compose configuration. The `--no-deps` flag ensures that dependent services are not started automatically. The `--build` flag indicates that the specified service (`web` in this case) should be rebuilt before starting.

Congratulations! You've successfully integrated your Jenkins Freestyle project with GitHub webhooks, allowing automatic builds and deployments whenever changes are pushed to your GitHub repository.