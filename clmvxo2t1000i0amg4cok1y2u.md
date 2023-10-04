---
title: "Jenkins CI/CD Mastery: Building, Deploying, and Automating with Web Hooks"
datePublished: Sat Sep 23 2023 11:14:19 GMT+0000 (Coordinated Universal Time)
cuid: clmvxo2t1000i0amg4cok1y2u
slug: jenkins-cicd-mastery-building-deploying-and-automating-with-web-hooks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695454352605/0448c152-bdba-4881-b306-a77a2471b48c.png
tags: docker, jenkins, 90daysofdevops, trainwithshubham, 90daysofdevopschallenge

---

### **Task-01: Setting Up Jenkins with GitHub for CI/CD using GiHub webhooks**

**Step 1:** Created 2 EC2 instances, Master and Agent.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695465354931/16c8e9ce-8625-4abf-b582-42ed395f1896.png align="center")

**Step 2:** Connected both instances via SSH keys.

**Step 3**: Fork the repository: [**https://github.com/LondheShubham153/node-todo-cicd**](https://github.com/LondheShubham153/node-todo-cicd)

**Step 4:** Login into the Jenkins dashboard and Create a **freestyle Project**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695465445504/d8b35d9c-ffc7-4f21-b103-e0dd2e5a2295.png align="center")

**Step 5:** Enter the **GitHub** repo URL of your forked repository here

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695465470453/da909efc-42d1-472a-95f7-4918236e7c13.png align="center")

**Step 6:** Select the Source Code Management as **Git** and paste the URL from the forked repository and select the branch in which the code is there.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467028443/2bf97f04-af78-44fb-83ee-af91aeb9bdc1.png align="center")

**Step 7:** Build a link between your Jenkins task and your GitHub Repository through GitHub Integration by utilizing a **Git Webhook**. Input the git URL of your project.

**Step 8:** Open the forked GitHub repository, Go to the repository's "**Settings**" tab.

**Step 9:** Select "Webhooks" from the left-hand menu & Click on the "**Add webhook**" button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467177407/95886385-a9af-42a9-b1b6-1bb4b624afa7.png align="center")

**Step 10:** In the "Payload URL" field, enter the Jenkins URL & Select the events that you want to trigger the webhook.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467145753/cdac1ad1-d5f3-4621-bced-b0f0859b3f18.png align="center")

**Step 11:** Click "Add webhook" to save the webhook configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467227023/164f9450-3748-4368-ab77-5f862249e832.png align="center")

**Step 12:** Again come to the Jenkins dashboard, click on **Build steps** &gt; **Execute Shell** &gt; Enter the command that will be executed after the job is built & save.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467242517/3654b87f-8d37-41e4-bc08-6a43bc855091.png align="center")

**Step 13:** Now, refresh the page unless the webhook URL is ticked as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467254803/ceafde0c-9cf8-49a9-a98d-9724fb6b1918.png align="center")

**Step 14:** Now, to test the webhook, make a small code change in your GitHub repository and commit it

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467275814/9b91bf0b-e4cc-4886-99bd-2e3400f39c73.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467282076/ad9d5843-4c64-4f0d-91b5-d152af9e233f.png align="center")

**Step 14:** Now, whenever you push code to your GitHub repository, the webhook will send a request to the Jenkins job's URL. This will trigger the Jenkins job automatically, running your specified build and deployment steps.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467326470/d51c3a11-a95f-4449-a929-286c9aac8e6b.png align="center")

Build Logs:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467309880/2c5a0a0f-c779-4b96-bc1a-ed2a064ecd22.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467317950/09c21b4f-6e78-4c60-8a31-ee7b702e6c73.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467376633/966cbbbd-bbea-4757-bf47-5781c27d1f48.png align="center")

### **Task 2: Effortless Application Deployment using Webhooks and Docker Compose**

**Step 1:** Follow the same steps from TASK1 till adding WebHook

**Step 2:** Now, change the execute shell command as below and save the Jenkins Job.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467513511/f7022a2f-5fef-44be-a37b-ea644e5730c0.png align="center")

**Step 3:** Now, to test the webhook, make a small code change in your GitHub repository and commit it

Step 4: Now, whenever you push code to your GitHub repository, the webhook will send a request to the Jenkins job's URL. This will trigger the Jenkins job automatically, running your specified build and deployment steps.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467539758/47857e46-0a84-4e76-98c3-0785c3394fdb.png align="center")

FYI - Agent server image and container information

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695467561663/8692f367-289e-458f-8713-c9f1b7d167f8.png align="center")

Thank you for taking the time to read this blog. I hope you found the information helpful and insightful.