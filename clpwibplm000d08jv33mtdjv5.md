---
title: "Automating EBS Snapshot Creation with CloudWatch Events and SNS"
datePublished: Fri Dec 08 2023 10:51:41 GMT+0000 (Coordinated Universal Time)
cuid: clpwibplm000d08jv33mtdjv5
slug: automating-ebs-snapshot-creation-with-cloudwatch-events-and-sns
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702031481294/538009ac-0855-46e1-aec0-380cd571d5b3.webp
tags: aws, cloud-computing, devops, aws-community-builder, ebs-snapshot

---

* We will create a new SNS topic and SNS email subscription that we will use with our CloudWatch Events rule.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702031559790/133e27fe-92b0-45ea-b7be-190234d25ad0.png align="center")

* Create the CloudWatch Events rule that will once-daily snapshot the specified EBS volume and initiates an email via SNS.
    
    1. Go to Cloudwatch
        
    2. Click on "Rules" below "Events" (It will auto redirect you to Amazon EventBridge)
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702031734305/c36e554f-f8c8-49c7-bed9-2f38617fb3af.png align="center")
        
    3. Click on Create Rule and select Schedule (To run on a schedule)
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702032042284/65e4f2e0-122b-4aae-a98a-00086bf5495e.png align="center")
        
    4. Select the time to run the schedule every 15 mins
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702032183683/5a0ea122-9d3f-44ef-a2db-6cb9e2c63137.png align="center")
        
    5. Now add 2 Targets - one for creating EBS Snapshot and another for sending an email through SNS.
        
        Target 1: Use EBS Create Snapshot and insert the volume ID of which you want to take a snapshot
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702032338675/e3d34d71-4485-43d8-951d-e74f1055b82b.png align="center")
        
        Target 2: Select the SNS topic to send the email.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702032378030/2ea67f22-7d9a-4cda-a6bf-758844f1060a.png align="center")
        

1. Finally, Review all the configurations and create a rule.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702032436141/d61b5b02-ea13-4283-b041-091791a713dd.png align="center")
    
2. Now, wait for the Snapshot to be created automatically.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702032491501/117516cc-9b6b-4e94-83cb-56f54d18613a.png align="center")