---
title: "Getting Your Feet Wet With Jenkins"
datePublished: Sat Sep 16 2023 05:19:00 GMT+0000 (Coordinated Universal Time)
cuid: clmlkw5yz000509id9bo76trl
slug: getting-your-feet-wet-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694836186791/255e07ae-5a25-4417-a0c0-bfe62fd24aeb.png
tags: jenkins, 90daysofdevops, day22, trainwithshubham, 90daysofdevopschallenge

---

# **Introduction**

Welcome to my Jenkins blog series! Here, we'll dive into a tool that DevOps Engineers love for automating tasks. In this beginner-friendly blog, we'll discover what Jenkins is, learn about CI/CD, set it up, explore the Jenkins Web Interface, and create our very first Jenkins job.

---

## What is CI/CD❓

**CI/CD** stands for **Continous Integration** and **Continous Delivery/Deployment**.

When you look at the DevOps symbol

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692323807701/fd777628-6cbb-4e20-ab08-c0bd7844aee2.png?auto=compress,format&format=webp align="left")

You can see there is an Infinite Cycle of the SDLC process from Planning to Deploy, Operate and Monitor. This Cycle that helps us for a faster release of the product should be continuous, automated, and robust. This Cycle is known as Continuous Integration and Deployment.

This is a crucial part of the DevOps practice where the whole process is automated, right when the code was committed to Git till it is deployed.

## ✔Continuous Integration (CI)

Continuous Integration (CI) is a development practice centered around the seamless merging and verification of code changes. When a developer commits or adds new code, CI involves assessing its functionality by confirming that it builds successfully, passes predefined test cases without issues, and operates without errors. If these criteria are met, the code is deemed successfully integrated.

In essence, CI consists of three key steps:

1. **Code Verification:** After a developer contributes new code, CI initiates automated checks to ensure it functions as intended.
    
2. **Merging and Assessment:** The code changes are merged with the existing codebase, creating a unified version. This merged code is then assessed as a whole to confirm it fulfils quality standards.
    
3. **Test and Build:** The integrated code undergoes rigorous testing to ascertain its reliability and compatibility with the larger system. Additionally, the code is built to produce a functional executable.
    

CI serves as an early warning system, detecting potential issues promptly and allowing developers to rectify problems before they escalate. By automating the integration, testing, and assessment of code changes, CI enhances collaboration among developers, minimizes errors, and accelerates the development process.

## **✔Continuous Delivery (CD)**

Continuous Delivery is a software development practice where code changes are automatically prepared, tested, and made ready for deployment to a production environment. In CD, every code change that passes automated tests is potentially deployable to production, but the actual deployment to the production environment is typically triggered manually by a team member or through an approval process. It includes:

1. **Automation and Testing:** Continuous Delivery emphasizes the automation of building, testing, and packaging code changes. This ensures that changes are thoroughly verified before they are considered for deployment.
    
2. **Staging and Pre-Production:** In Continuous Delivery, changes are first deployed to staging or pre-production environments, allowing further testing and validation. If the changes pass these tests, they are ready for deployment to the production environment.
    
3. **Manual Deployment:** While the process leading up to deployment is automated, the decision to deploy to the production environment is made by a human. This human intervention adds an extra layer of control and allows for final checks before releasing changes to end users.
    

## **✔Continuous Deployment**

Continuous Deployment takes the concept of Continuous Delivery a step further by automating the entire process of deploying code changes to production without manual intervention. In this approach, any code change that passes automated tests is automatically deployed to the production environment. It includes:

1. **Automated Deployment:** In Continuous Deployment, the deployment process is fully automated. As soon as code changes pass automated tests, they are immediately deployed to the production environment.
    
2. **Minimal Human Intervention:** Unlike Continuous Delivery, where a human decision is required to trigger deployment, Continuous Deployment eliminates this step. This reduces the time between code changes being ready and them being available to users.
    
3. **Rapid Feedback Loop:** Continuous Deployment allows teams to receive rapid feedback from real-world usage of code changes, enabling faster iteration and response to user needs.
    

---

# **Jenkins**

Jenkins is a powerful CI/CD tool that automates the software development process. By seamlessly integrating development and operations practices, it accelerates the creation, testing, and deployment of software. With Jenkins, code changes are automatically integrated, tested, and deployed, making the entire development lifecycle faster and more efficient. This automation streamlines tasks, reduces errors, and fosters collaboration between teams.

---

# Installation and Setup

Jenkins is a Java-based application that relies on the Java Virtual Machine (JVM) to execute its code. Therefore, a Java Development Kit (JDK) must be installed on the system before you can run it.

Documentation to install Jenkins: [**https://www.jenkins.io/doc/book/installing/**](https://www.jenkins.io/doc/book/installing/)

`Step 1`:

```bash
sudo apt-get update
sudo apt install openjdk-17-jre
java --version # Verify java installation
```

If the output for the `java --version` command is the following then it means the JDK had been successfully installed:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694836525920/c3f21471-e350-4195-94c4-ea1cff49f545.png align="center")

`Step 2`:

If you want to use a stable release then you can use Long Term Support Release/ go ahead with the Weekly release:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694836557378/3a061980-6ba3-4583-a54c-288e59d4de06.png align="center")

Check the status of Jenkins -

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694836731264/e15c7f2d-e1f7-4b5f-8be4-6de6d65f0ac6.png align="center")

Since Jenkins is a service a user named "jenkins" is created in the system.

`Step 3`:

Allowing port 8080 and restricting access to my IP only:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694838422207/92f57845-9b54-4e36-bf2d-0f421c749094.png align="center")

# **Creating Your First Jenkins Job**

The default port for the Jenkins web interface is **8080**. This means that when you access Jenkins through a web browser, you would typically use a URL like:

[`http://localhost:8080`](http://localhost:8080)

[`http://aws_ec2_ip_address:8080`](http://aws_ec2_ip_address:8080)

Type this URL in your browser you will get this -

Admin initial password is stored in a temporary file inside the `/var/lib/jenkins/secrets/initialAdminPassword` directory path:

Use this command for Linux:

`Step 1`: Copy the password, paste it, and then press Continue.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694838472848/ae536cf5-fe0e-4f75-95c9-b639b773bf47.png align="center")

`Step 2`: Click on Install suggested plugins.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694838543387/8f5a52ce-2e64-42fc-a3d2-6fd63bd716fa.png align="center")

Jenkins will automatically install all the necessary plugins usually useful for performing DevOps tasks

`Step 3`: Create Admin User

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694838572802/104178de-a01b-43a0-8a5f-2915407b8937.png align="center")

`Step 4`: Enter your details to create the first admin user and press Save and Continue.

This **First Admin User** has access to the Jenkins **global configuration**

* The admin user can create, modify, delete user accounts, and assign permissions and roles to other users within Jenkins.
    
* Admins can create, configure, and delete Jenkins jobs (build, test, deployment tasks) for different projects.
    
* And many more privileges like **View Management, Plugin Management, etc.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694838626795/79a82f39-bcd7-4f6e-aca3-9b05d3aa9490.png align="center")

Then you will get a Jenkins URL to access Jenkins, you can change this URL name as you like. You can also change the URL.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694838654187/cb3c9a25-132e-48d5-9734-4ac4ed25b4f6.png align="center")

Your Set-Up is now finished and you will get the **Jenkins Interface** home page.

---

# **Jenkins Plugins**

## **✔What Are Plugins❓**

Plugins in Jenkins are modular extensions that enhance and expand its capabilities. They can add functionalities such as integrating with version control systems, automating builds, sending notifications, and more. Plugins are crucial for adapting Jenkins to your specific requirements without modifying its core code.

**Installing Plugins:** Jenkins provides a Plugin Manager that simplifies the process of finding, installing, and managing plugins:

* **Plugin Search:** You can search for plugins by name or functionality using the Plugin Manager's search bar. You see this search bar by clicking on "**Manage Jenkins**" at the left.
    
    From the dropdown menu that appears when you click "**Manage Jenkins**", select "**Manage Plugins**."
    
* **Installation:** When you find a plugin you need, you can install it with a single click. Jenkins will download and install the plugin for you.
    
* **Updating Plugins:** The Plugin Manager also helps you keep your plugins up to date by notifying you when updates are available.
    

**Commonly Used Plugins:** Highlighting a few essential plugins can help readers grasp the breadth of functionality plugins provide:

* **Git Plugin:** Integrates Jenkins with Git repositories, enabling automatic builds triggered by code changes.
    
* **Docker Plugin:** Facilitates Docker integration, allowing Jenkins to build, test, and deploy Docker containers.
    
* **Pipeline Plugin:** Introduces Jenkins Pipeline, enabling you to define complex build and deployment workflows as code.
    

**Plugin Configuration:** After installing a plugin, you often need to configure it to suit your needs:

* **Global Settings:** Some plugins have global settings that affect the entire Jenkins instance.
    
* **Job-specific Configuration:** Plugins might introduce new configuration sections within job settings, allowing you to tailor their behavior per job.
    

**Customization:** Plugins empower you to customize Jenkins to align with your specific use cases:

* **Tailored Workflows:** You can combine various plugins to create workflows that meet your automation and deployment needs.
    
* **Visualizations and Reporting:** Plugins can introduce graphs, charts, and reports that help you analyze build trends and project health.
    

**Plugin Compatibility:** It's important to keep plugins up to date for several reasons:

* **Bug Fixes and Enhancements:** New versions might include bug fixes, performance improvements, and new features.
    
* **Security Updates:** Plugin updates might address security vulnerabilities, helping keep your Jenkins instance secure.
    

**Removing Plugins:** Removing unnecessary plugins can help maintain a clean Jenkins environment:

* **Backup:** Always make backups before removing plugins to ensure you can revert changes if needed.
    
* **Disruption Prevention:** Remove plugins carefully, as some jobs might rely on their functionality. Analyze potential impacts before deletion.
    

**Managing Dependencies:** Some plugins depend on others to function properly:

* **Plugin Interactions:** Some plugins might require specific core or other plugins to work correctly.
    
* **Dependency Handling:** Jenkins' Plugin Manager often handles plugin dependencies automatically, installing required plugins when you install one that depends on them.
    

---

# 📍Jenkins Job

A Jenkins job is a sequence of steps, commands, or actions that need to be executed as part of an automation workflow. Jenkins jobs automate repetitive tasks such as compiling code, running tests, packaging applications, and deploying software.

A Jenkins job is a way to automate a specific task or process in a software development workflow. Jobs encompass everything from source code management to build processes, testing, and deployment. The ability to define, configure, and automate jobs is a central feature of Jenkins, enabling teams to streamline their development and deployment processes.

**There are 3 types of Jobs:**

1. **Freestyle Jobs:** Traditional build jobs where you define a series of build steps, triggers, and actions.
    
2. **Pipeline Jobs:** Introduced by the Jenkins Pipeline plugin, they enable defining entire build and deployment workflows as code in a Jenkinsfile.
    
3. **Matrix Jobs:** Used for testing a combination of different parameters, such as various OS versions or browsers.
    

# **Creating Your First Jenkins Job**

`Step 1`: Click on "**Create a Job**" at the center or "**New Item**" at the left.

`Step 2`: Give a name to the Jenkins Job and select "**Freestyle project**" and Press "**OK**".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694839568044/40215ea3-e51a-4016-b1bf-c1f202ba0ba5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694840707924/2f455d1d-779b-469c-b52b-b6e5d15e300f.png align="center")

`Step 3`: Add some description of what this job is doing - Scroll down and in the Source Code Management Section select None.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694840718708/0d7f644a-bf59-4e1d-8b31-2252ab8b9526.png align="center")

`Step 4`: Scroll down a little and go to the Build Steps section. It is a dropdown menu to select a shell where you can execute your build and deploy commands or any other command you want to execute during the build process and Click "**Save**" and your Job has been created.

Select the "**Execute** **Shell**" option:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694840904531/e634dc16-6fd6-4a19-a1d9-9c65c2a870fc.png align="center")

Click "**Save**" and your Job has been created.

`Step 5`: Click on "**Build Now**" at the left to start the build of the Job.

You can see that your build has been executed successfully since we can see a green tick mark.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694841016651/4968c286-527e-4459-bfe5-d926616703fa.png align="center")

`Step 6`: Click on that build "**#1**" or "#2" You will see this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694841036978/682833bf-03a6-4171-a9f4-ac8814df9b17.png align="center")

`Step 7`: Click on "**Console Output**" To see all the steps it performed in the build process:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694841059739/00a89da3-c958-454a-933d-71015ec0f0d6.png align="center")

If the build fails, you can review the console output to pinpoint the exact point, step, or code where the failure occurred.

📝**Note**: All these Jenkins tasks are performed by the "jenkins" user in the system.