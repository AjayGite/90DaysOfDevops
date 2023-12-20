---
title: "Day01-TerraWeek Challenge:Introduction to Terraform & Basics"
datePublished: Wed Dec 20 2023 13:54:27 GMT+0000 (Coordinated Universal Time)
cuid: clqdu4z22000708jl6z8h1ouj
slug: day01-terraweek-challengeintroduction-to-terraform-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703080400569/6d82c170-72c1-42cb-a876-76280ce8cb41.png
tags: terraform, 90daysofdevops, trainwithshubham, terraweekchallenge

---

# **Introduction**

In the ever-evolving landscape of IT infrastructure management, ***Infrastructure as Code (IaC)*** has emerged as a game-changing approach.

It allows organizations to manage and provision infrastructure resources using machine-readable configuration files or scripts, eliminating the need for manual processes and configurations.

This blog will delve into the core concepts of IaC, and more specifically, we will explore why **Terraform** is the preferred choice for infrastructure management.

Follow along, and you'll learn not only the 'what' and 'why' but also the 'how' of setting up *Terraform* and creating your first configuration.

# 📚Comprehending Infrastructure as Code (IaC)

**Infrastructure as Code (IaC)** represents a profound transformation in our approach to infrastructure management.

Instead of the conventional manual setup of servers, networks, and related infrastructure components, IaC empowers us to articulate our desired infrastructure state using code.

This code can subsequently be executed to automate the provisioning and management of our infrastructure.

IaC serves as a fundamental cornerstone within the realms of both DevOps and cloud computing, with a primary focus on efficiency, reliability, and scalability.

**The Merits of Infrastructure as Code**

Let's delve further into the benefits of embracing IaC:

1. **Automation**: IaC streamlines the deployment of infrastructure, substantially reducing the need for manual interventions and the associated risks of human errors. This bolsters the dependability and efficiency of your infrastructure.
    
2. **Uniformity**: By expressing infrastructure configurations through code, you ensure a consistent setup across diverse environments. The issue of configuration deviations, where environments stray from the intended state, becomes a thing of the past.
    
3. **Scalability**: IaC simplifies the process of adjusting resource capacities. Through code adjustments, you can effortlessly expand or shrink your infrastructure to accommodate evolving demands, ensuring optimal resource allocation.
    
4. **Reproducibility**: Your infrastructure can be systematically deployed across various environments, such as development, staging, and production. This consistency streamlines testing and deployment procedures.
    
5. **Collaboration**: IaC encourages collaboration among team members. Infrastructure configurations can be version-controlled, shared, and developed collaboratively, fostering the sharing of knowledge and teamwork.
    
6. **Documentation**: Infrastructure code serves as executable documentation, simplifying the comprehension and long-term maintenance of your infrastructure.
    
7. **Agility**: Infrastructure modifications can be swiftly and efficiently executed, facilitating rapid iterations and deployments. This agility proves indispensable in dynamic and fast-paced development environments.
    

# **🤔Why Terraform?**

Among the many Infrastructure as Code tools available, Terraform shines for several reasons:

1. **Multi-Cloud and Multi-Provider Support**: Terraform supports a wide range of cloud providers, including AWS, Azure, GCP, and more. Additionally, it extends its support to various infrastructure platforms like VMware, Docker, and Kubernetes. This versatility means you can manage resources across different providers and platforms using a single tool.
    
2. **Declarative Syntax**: Terraform employs HashiCorp Configuration Language (HCL) or JSON, offering a human-readable format to define your infrastructure. You describe the desired state of your resources, and Terraform handles the provisioning and management details.
    
3. **Community and Ecosystem**: Terraform boasts a thriving community that provides a wealth of modules, plugins, and best practices. This community support accelerates development, assists in issue resolution, and encourages knowledge sharing.
    
4. **Collaboration and Version Control**: Infrastructure code written in Terraform integrates seamlessly with version control systems. This facilitates collaboration, enables robust code reviews, and provides the ability to roll back changes if necessary.
    

# **📃Important Terminology in Terraform**

## **📌Providers**

A provider serves as a plugin that enables Terraform to manage an external API. When executing `terraform init`, the required plugins for the provider are automatically fetched and stored locally within a `.terraform` directory. Terraform boasts support for multiple providers, and depending on the desired infrastructure type, you must choose and configure the appropriate provider accordingly.

```bash
# Initialize Terraform and download provider plugins
terraform init
```

## **📌Resource**

Resources constitute the fundamental building blocks in the Terraform language. Each resource block defines one or more infrastructure components, such as virtual networks, compute instances, or higher-level elements like DNS records.

```bash
resource "aws_instance" "web" {
  ami           = "ami-a1b2c3d4"
  instance_type = "t2.micro"
}
```

## **📌Variables**

In Terraform, variables can be assigned values through various methods, including:

i) Environment variables ii) Command Line Flags iii) From a File iv) Variable Defaults

**i) Environment Variables:**

You can set Terraform variables using environment variables. Here's an example:

```bash
variable "region" {
  description = "AWS region"
}
```

To set the `region` variable using an environment variable:

```bash
export TF_VAR_region=us-west-1
```

Now, the `region` variable is set to "us-west-1" in your Terraform configuration.

**ii) Command Line Flags:**

You can also set Terraform variables using command-line flags when running `terraform apply` or `terraform plan`. Here's how:

```bash
terraform apply -var="region=us-west-1"
```

This command sets the `region` variable to "us-west-1" for the duration of the `apply` operation.

**iii) From a File:**

You can store variable values in a separate file and reference that file in your configuration. Create a file (e.g., `terraform. tfvars`) with the variable values:

**COPY**

**COPY**

```bash
region = "us-west-1"
```

Then, when running `terraform apply`, Terraform will automatically read values from this file

```bash
terraform apply
```

Terraform will recognize and use the values specified in `terraform. tfvars`.

**iv) Variable Defaults:**

In your variable declarations, you can also provide default values:

```bash
variable "region" {
  description = "AWS region"
  default     = "us-east-1"
}
```

If no other method sets the `region` variable, it will default to "us-east-1."

By using these methods, you can manage and set Terraform variables according to your specific needs, whether through environment variables, command-line flags, external files, or default values in your configuration.

## **📌Module**

Think of a module as a readily usable blueprint for a specific collection of infrastructure resources. It resembles a pre-built package that can be reused across different projects, promoting code organization and ensuring consistency in infrastructure.

```bash
# Use a Terraform module
terraform apply -target=module.module_name
```

## **📌State**

The state acts as a memory repository for your infrastructure. It maintains a record of the current state of your resources and their configurations. Terraform relies on the state to determine what resources have already been created, simplifying the management and updating of your infrastructure.

```bash
# Show Terraform state
terraform show
```

# **♻Terraform Lifecycle**

The Terraform lifecycle encompasses four crucial phases: *initialization, planning, application, and destruction.*

1. **Initialization (Terraform init):** This phase initializes the local Terraform environment. Typically, it's executed just once per session to set up the necessary configurations.
    
2. **Planning (Terraform plan):** During this step, Terraform compares the current Terraform state with the existing state in the cloud infrastructure. It constructs and presents an execution plan, which serves as a read-only blueprint for potential changes to the deployment. Importantly, it doesn't alter the actual deployment.
    
3. **Application (Terraform apply):** In this phase, Terraform executes the previously generated plan. This operation has the potential to modify the deployment, bringing it in line with the defined configuration.
    
4. **Destruction (Terraform destroy):** The destruction phase is responsible for removing all resources managed by the specific Terraform environment. It effectively cleans up and deletes the infrastructure components according to the Terraform configuration.
    

# **⚓Set Up of Terraform on AWS**

1. To install Terraform and set up the environment for AWS, you can follow these steps:
    
    * Download the Terraform binary suitable for your operating system from the official Terraform website: [**https://developer.hashicorp.com/terraform/downloads**](https://vishaltoyou.hashnode.dev/day01-terraweek-challengeintroduction-to-terraform-basics#heading-comprehending-infrastructure-as-code-iac)
        

Here, we will be setting up Terraform in an AWS EC2 instance(Ubuntu AMI)

```bash
    # Download HashiCorp GPG key and store it as /usr/share/keyrings/hashicorp-archive-keyring.gpg
    wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

    # Add HashiCorp repository to the sources list
    echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

    # Update package list and install Terraform
    sudo apt update && sudo apt install terraform

    #Verify the installation using 
    terraform -- version
```

These commands will download HashiCorp's GPG key, add their repository to your system's package sources, update the package list, and finally install Terraform. Make sure you have appropriate permissions (e.g., sudo) to execute these commands on your system.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694335253582/7c37c246-de37-46dc-9ff4-a4e68784d1e5.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694335278617/00d3784c-6766-47b0-b634-e3b99261ab7c.png?auto=compress,format&format=webp align="left")

# **📑Create Day 01 Simple Project**

So on Day 01 , let's start with a simple project

1. To start your Terraform project, create a new directory
    
2. To store your Terraform configuration files, create a new directory.
    
3. Enter this directory's path at the command prompt or terminal.
    
4. Create a Terraform configuration file: In your project directory, create a new file called [**main.tf**](https://vishaltoyou.hashnode.dev/day01-terraweek-challengeintroduction-to-terraform-basics#heading-comprehending-infrastructure-as-code-iac)**. This file will contain your Terraform configuration.**
    
5. In [**main.tf**](https://vishaltoyou.hashnode.dev/day01-terraweek-challengeintroduction-to-terraform-basics#heading-comprehending-infrastructure-as-code-iac) **file add the below HCL commands to create a file with automation.**
    
    ```bash
     resource "local_file" "devops_terraform" {
             filename = "/home/ubuntu/first_terraform_project/config"
             content = "It's Day-1 TerraWeek challenge"
     }
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694336615698/b6237a28-f9d2-4eb3-bee9-02c5c22cad57.png?auto=compress,format&format=webp align="left")
    
6. The code snippet creates a resource of type "local\_file" with the name "devops\_terraform". Here's the breakdown of the code:
    
    * `resource`: This keyword is used to define a resource in Terraform.
        
    * `"local_file"`: It specifies the resource type, which in this case is a local file resource.
        
    * `"devops_terraform"`: It provides a name or identifier for the resource instance, allowing it to be referenced elsewhere in the configuration.
        
    * `filename`: It specifies the path and name of the file to be created. In this case, it is set to "/root/terraform/terraform-local/automate-file.txt".
        
    * `content`: It defines the content that will be written to the file. Here, it is set to "It's Day-1 Terraweek challenge".
        
7. **Initialization**: Start your Terraform project with `terraform init`. This command sets up your environment by fetching necessary provider plugins and configuring the backend for state storage. It ensures your Terraform environment is ready for infrastructure management
    
    ```bash
     terraform init
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694336437771/2d4a05d7-8ec1-410f-84b5-dab5ea4fe23e.png?auto=compress,format&format=webp align="left")
    
8. **Deployment**: Deploy your infrastructure using `terraform apply`. Terraform will ask for confirmation; type "yes" and hit Enter to proceed with deployment.
    
    ```bash
     terraform apply
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694336680161/10ba7406-2742-466e-a410-3f01554204d7.png?auto=compress,format&format=webp align="left")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694336707491/a851603c-7330-4be2-8921-5fe5d98bb009.png?auto=compress,format&format=webp align="left")
    
9. **Verification**: After Terraform finishes applying your configuration, verify the successful deployment in your cloud provider's console.
    
10. To Check for your newly provisioned infrastructure components to confirm everything is as expected, check whether the file has created or not
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694336862738/5a405a59-826c-4f2d-a77c-852d3e051d20.png?auto=compress,format&format=webp align="left")
    
    **So, we have completed our day 01 of the terraWeek Challenge by creating simple project**
    

#