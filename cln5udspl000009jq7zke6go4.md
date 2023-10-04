---
title: "Jenkins Declarative Pipeline - An Overview with example"
datePublished: Sat Sep 30 2023 09:40:02 GMT+0000 (Coordinated Universal Time)
cuid: cln5udspl000009jq7zke6go4
slug: jenkins-declarative-pipeline-an-overview-with-example
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695797489643/0178bd29-ee92-42db-a5ae-285f27424068.png
tags: 90daysofdevops, jenkins-pipeline, day26

---

### **🔹What is Pipeline?**

In the context of Jenkins, a "pipeline" refers to a series of automated steps or jobs that are organized in a sequence to achieve a specific task or workflow. Pipelines are a fundamental concept in Jenkins, used for defining and automating the steps required to build, test, and deploy software applications.

There are two main ways to define and create pipelines in Jenkins: Declarative and Scripted.

<mark>Declarative Pipeline:</mark>

* Declarative is a more recent and user-friendly way to define pipelines in Jenkins.
    
* It is designed to provide a simpler and more structured syntax for defining pipelines.
    
* Declarative pipelines use a set of predefined, high-level directives and keywords to define stages and steps in a pipeline.
    
* These pipelines are easier to read, write, and maintain, making them a preferred choice for many Jenkins users, especially those who are new to pipeline scripting.
    
* Declarative pipelines encourage best practices and provide good defaults, making them a safer and more controlled way to define pipelines.
    
    **Declarative Pipeline Example:**
    
    ```yaml
      pipeline {
          agent any
    
          stages {
              stage('Build') {
                  steps {
                      sh 'echo "Building the application"'
                  }
              }
              stage('Test') {
                  steps {
                      sh 'echo "Running tests"'
                  }
              }
              stage('Deploy') {
                  steps {
                      sh 'echo "Deploying the application"'
                  }
              }
          }
            post { 
            // In this block you define expressions of build status or build status changes.
            always{
                // Actions to perform irrespective of build success or fail
    
            }
            success {
                // Actions to perform on successful build
                echo 'Build succeeded!'
            }
            failure {
                // Actions to perform on build failure
                echo 'Build failed!'
            }
        }
      }
    ```
    
    In this Declarative Pipeline example:
    
    * We specify that the pipeline can run on any available agent.
        
    * We define three stages: Build, Test, and Deploy.
        
    * Each stage contains a single step, which is a shell command (`sh`) that prints a message.
        
    * Declarative pipelines use a predefined structure with `pipeline`, `stages`, and `steps` directives to simplify pipeline definition.
        

<mark>Scripted Pipeline:</mark>

* Scripted pipelines were the original way to define pipelines in Jenkins and are built using Groovy, a powerful scripting language.
    
* Scripted pipelines offer more flexibility and control over the pipeline's logic, making them suitable for complex and custom workflows.
    
* In scripted pipelines, you write custom Groovy scripts to define the pipeline's stages and steps.
    
* This flexibility comes at the cost of increased complexity, as scripted pipelines can become harder to read and maintain, especially for users who are not familiar with Groovy.
    
* Scripted pipelines are still widely used when intricate customization or advanced logic is required for a pipeline.
    
    **Scripted Pipeline Example:**
    
    ```bash
      node {
          stage('Build') {
              echo 'Building the application'
              // Additional build steps can be added here
          }
          stage('Test') {
              echo 'Running tests'
              // Additional test steps can be added here
          }
          stage('Deploy') {
              echo 'Deploying the application'
              // Additional deployment steps can be added here
          }
      }
    ```
    
    In this Scripted Pipeline example:
    
    * We start with a `node` block, which specifies where the pipeline should run.
        
    * Within each `stage`, we use the `echo` command to print messages.
        
    * Scripted pipelines provide more flexibility to define custom logic and execute arbitrary code within each stage.
        

### **The Importance of Having a Pipeline**

By writing the pipeline's definition in a text file called a **Jenkinsfile**, and committing it to the project's source control repository, we're treating our CD pipeline just like any other part of the application's codebase.

This has some immediate advantages:

1. **Consistency**
    
    Every branch and pull request follows the same pipeline defined in the Jenkinsfile, ensuring consistency across the development process.
    
2. **Versioning**
    
    The pipeline becomes versioned alongside the application code, making it easier to track changes and roll back if needed.
    
3. **Code Review**
    
    Just like any other code, the pipeline can go through code review and iterations, ensuring it's efficient and error-free.
    

### **📖Task-01: Task: Create a New Job using Pipeline Hello World Example**

This example demonstrates the basic process of creating and executing a pipeline in Jenkins. Here's a more detailed breakdown of each step:

**Step 1: Navigate to the Jenkins Home Page and Create a New Job**

1. Open a web browser and navigate to the Jenkins home page.
    
2. Log in if required.
    
3. Click on "New Item" to create a new job.
    
4. Give a job a name and select "Pipeline" as the job type.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696066498371/4f2392a1-f039-416a-a2a8-b99cf37d9d3b.png align="center")
    
5. Click "OK" to create the job.
    

**Step 2: Configure the Project with a Valid Description**

1. In the job configuration page, scroll up to the top section where we can edit the job's details.
    
2. Add a valid description for the project.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696066648216/43187a4a-2c45-408d-8f5a-0fdafc8e4179.png align="center")
    
3. Save the changes.
    

**Step 3: Follow the Official Jenkins** [**Hello World Example**](https://www.jenkins.io/doc/pipeline/tour/hello-world/)

1. In the configuration page of the new job, scroll down to the "Pipeline" section.
    
2. Select the "Pipeline script" option.
    
3. Choose the "Pipeline script from SCM" option and provide the necessary repository details. (In this case, you're following the "Hello World" example, so you might choose to use a simple script or select Hello World or a Jenkinsfile in your repository.)
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696066673786/15bf3dd2-8e43-4d9b-8dc7-7cc78340bb8e.png align="center")
    
4. Save the changes.
    

**Step 4: Click on Save and Then Build Now**

1. After saving our pipeline configuration, we can manually trigger a build by clicking "Build Now." This will initiate the pipeline execution based on the code we've written.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696066704798/28900f01-1f67-4e31-921a-d0a79e96329f.png align="center")
    

**Step 5: Check the Full Stage View for Execution Time**

1. Once the pipeline execution starts, we can navigate to the "Full Stage View" to see the different stages of our pipeline and the time it takes for each stage to complete.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696066737875/a6aad816-d611-438b-8e9b-cf353288351f.png align="center")
    

**Step 6: Verify Hello World Using Console Output**

1. After the pipeline has been completed, we can check the "Console Output" to see the detailed logs of each step's execution.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696066745418/ee8536fa-30d8-42c3-99d1-ea7603d31574.png align="center")
    
2. If everything went as expected, we should see a "Success" status in the console output, indicating that the "Hello World" pipeline was executed successfully.