---
title: "Basic Git & GitHub for DevOps Engineers"
datePublished: Thu Aug 03 2023 04:44:29 GMT+0000 (Coordinated Universal Time)
cuid: clkuoab3j000l09mje9bzcspq
slug: basic-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690828066671/c624ac04-2db0-4d19-93a1-40444d468c02.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691037454635/fc14aacd-18b0-48ed-8c40-1a657a493d37.jpeg
tags: github, git, day8, trainwithshubham, 90daysofdevopschallenge

---

### What is Git?

Git is a distributed version control system (DVCS) that allows multiple developers to work together on the same project without stepping on each other. It gives you to track changes in your code and collaborate seamlessly with your team.

In simple language, Image you are working on your project, and every time you make a significant change, you take a snapshot of your work. Git does the same thing for your code. It takes snapshots of your code whenever you want, and you can give each snapshot a description to remember what you did.

This way, you can experiment with new features or fix bugs without worrying about messing up the entire project. If something doesn't work back you can go back to the previous snapshot and try again.

Git also allows you to work with other people. It keeps everyone's changes separate, so multiple people can work on the same project simultaneously without stepping on each other's toes. When you're ready to share your work or collaborate with others, you can send your snapshots to them or receive their changes and merge them into your own work.

### What is GitHub?

GitHub is a code-hosting platform for version control and collaboration. It's a website that helps developers work together on software projects.

Imagine it as a place where you can store your code, just like you would save your files on a computer. But instead of keeping it to yourself, you can share your code with other people around the world.

When you have a project on GitHub, others can see what you've done, and they can also suggest changes or improvements to your code. These suggestions are done through something called "pull requests," where others propose their changes, and you can review them before deciding to add them to your project.

GitHub is not only for sharing code; it also keeps track of all the changes made to your project over time, making it easy to see who did what and when. So, if something goes wrong, you can look back at previous versions of your code to find out what happened.

### What is Version Control? How many types of version controls do we have?

Version control is a system that helps developers track and manage changes to their code or files over time. It allows multiple developers to collaborate on a project without overwriting each other's work and provides a history of changes made to the project. Version control is crucial for software development, as it enables developers to keep track of the development process, revert to previous states if needed, and work more efficiently in teams.

There are primarily two types of version control:

1. **Centralized Version Control System (CVS):**
    
    In a centralized version control system, there is a central server that stores the entire history of the project and the files themselves. Developers work with a local copy of the files, and when they want to make changes, they first check out files from the central server. After making changes, they commit their modifications back to the central server, and other developers can update their local copies by pulling the changes from the server.
    
    Examples of CVCS include Subversion (SVN) and Perforce.
    
    ![What Is Git | Explore A Distributed Version Control Tool | Edureka](https://www.edureka.co/blog/wp-content/uploads/2016/11/Centralized-Version-Control-System-Workflow-What-Is-Git-Edureka.png align="left")
    
2. **Distributed Version Control System (DVCS):**
    
    In a distributed version control system, every developer has their own complete copy of the repository, including the entire history. This allows developers to work independently and collaborate more effectively. They can commit changes locally, and when ready, they can push their changes to a shared remote repository, where other developers can pull the changes.
    
    Examples of DVCS include Git, Mercurial, and Bazaar.
    
    ![What Is Git | Explore A Distributed Version Control Tool | Edureka](https://www.edureka.co/blog/wp-content/uploads/2016/11/Distributed-Version-Control-System-Workflow-What-Is-Git-Edureka.png align="left")
    

### Why we use distributed version control over centralized version control?

We use distributed version control over centralized version control because it offers several advantages that make collaboration and development easier for individuals and teams. Here are the reasons why Distributed Version Control, like Git, is preferred:

  
We use distributed version control over centralized version control because it offers several advantages that make collaboration and development easier for individuals and teams. In simple language, here are the reasons why distributed version control, like Git, is preferred:

1. **Offline Work**: With distributed version control, each developer has their own complete copy of the entire project, including its history. This means developers can work on their code even when they are offline or disconnected from the central server. They can make commits and switch branches without needing constant access to the internet.
    
2. **Faster Operations**: Since everything is stored locally in distributed version control, common operations like committing changes and switching between branches are generally faster because they don't rely on a central server. Developers can perform these actions without waiting for a remote server's response.
    
3. **Branching and Merging**: Distributed version control systems excel at handling branches. Developers can create branches to work on separate features or bug fixes without affecting the main codebase. Merging changes from one branch to another is generally more flexible and easier to manage in a distributed environment.
    
4. **Better Collaboration**: In distributed version control, developers can share their changes with others through pull requests. This allows for a more streamlined and controlled way of collaborating on code. Contributors can propose changes, have them reviewed, and then merge them into the main project.
    
5. **Redundancy and Backup**: Since every developer has a full copy of the repository, the risk of losing code due to a server failure is minimized. Each copy serves as a backup, and the loss of one developer's copy doesn't affect others.
    
6. **Support for Open Source**: Distributed version control is particularly well-suited for open-source projects, where contributors may be geographically dispersed. It enables collaboration between developers worldwide without relying on a central authority.
    
7. **Scalability**: Distributed version control can handle large and complex projects efficiently. As the project grows, developers can continue working locally without putting excessive strain on the central server.
    

Overall, distributed version control systems, like Git, provide more flexibility, resilience, and efficiency for developers working on software projects. They empower teams to work together more effectively and offer greater control over the development process, making them the preferred choice for modern software development.

## Task 1: Installation of Git

Below are the steps to install Git on Windows, macOS, and Linux:

**For Windows:**

1. Go to the official Git website at [**git-scm.com/downloads**](http://git-scm.com/downloads)**.**
    
2. Download the latest version of Git for Windows.
    
3. Run the installer and follow the on-screen instructions.
    
4. During the installation, you can choose the components you want to install. The default settings are generally sufficient for most users.
    
5. After the installation is complete, open the command prompt or Git Bash to verify that Git is installed. Type `git --version`, and it should display the installed Git version.
    

**For macOS:**

1. macOS comes with a built-in version of Git. To check if Git is installed, open the Terminal application and type `git --version`. If Git is not installed, it will prompt you to install the Xcode Command Line Tools, which include Git. Confirm the installation, and Git will be installed.
    

**Linux**:

1. For Debian/Ubuntu-based systems, open the terminal and use the package manager to install Git. Type `sudo apt update` to update the package list, then `sudo apt install git` to install Git.
    
2. For Red Hat/Fedora-based systems, open the terminal and use the package manager to install Git. Type `sudo dnf install git` or `sudo yum install git` to install Git.
    
3. Verify the Git is installed and the version of it:
    
    ```bash
    ubuntu@ip-172-31-92-36:~$ git --version
    git version 2.34.1
    ```
    

## Task 2: Create a free account on GitHub

Below are the steps to create a free GitHub account:

1. Visit [**github.com**](http://github.com) and click "Sign Up."
    
2. Choose the "Free" plan and create an account with email or Google.
    
3. Verify your email to activate your account.
    
4. Complete your profile settings and personalize your GitHub experience.
    
5. Optional: Set up an SSH key for enhanced security and convenience.
    

## **Excercise** 1: Create a new repository on GitHub.

1. Sign in to your GitHub Account using your Username and Password.
    
2. On the top right corner, Click on the "+" icon and "New repository"
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690996868163/3f865608-9806-4dbb-9367-fd4b6558e48c.png align="center")
    
3. Add the repository name and other details like whether you want to keep it public or private report.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690997159240/cd3413c6-a26e-4516-8e56-6f09779f5cae.png align="center")
    
    Click on "Create repository" to successfully create a repo.
    

## **Excercise** 2: **Clone the Repository to Your Local Machine**

1. **Find the Repository**: Go to the GitHub website and navigate to the repository you want to clone.
    
2. **Get the Clone URL and copy it:** Click on the green "Code" button located on the right side of the repository page. This will reveal the clone URL. Make sure to select the "HTTPS" option if you haven't set up an SSH key. Click on the clipboard icon next to the clone URL to copy it to your clipboard.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690997877991/d0694a66-0b82-4c2c-b35f-3294da3d34f3.png align="center")
    
3. **Open the terminal** and execute the below command to clone the remote repository to the local machine.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690998046811/954e897e-3240-4ab3-aca7-91e161dda524.png align="center")
    
    <details data-node-type="hn-details-summary"><summary></summary><div data-type="detailsContent">NOTE: If the repository is private, you may be prompted to enter your GitHub credentials to authenticate.</div></details>

## **Excercise** 3: Make some changes to a file in the repository and commit them to the repository using Git

1. **Open the Terminal or Command Prompt:** Navigate to the local repository directory on your computer using the terminal (Linux or macOS) or command prompt (Windows).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690998533523/573b4f3a-4078-496a-a025-8ec3fcb59edf.png align="center")
    
2. **Make Changes to the File:** Use a text editor or code editor to make the desired changes to the file you want to update.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690998520702/98300760-f20a-4006-a73c-aac9fe892d4b.png align="center")
    
    Basically, we have created 2 files and added some contents in the each file. We will now have to add those file to Staging area and then will have to commit them.
    
    ![Git Gud: The Working Tree, Staging Area, and Local Repo | by Lucas Maurer |  Medium](https://miro.medium.com/v2/resize:fit:686/1*diRLm1S5hkVoh5qeArND0Q.png align="left")
    
3. **Check Repository Status:** Use the command `git add <filename>` to add the modified file to the staging area. This prepares the changes for the upcoming commit. You can also use `git add .` to add all modified files in the repository to the staging area.Use the command `git status` to check the status of the repository. It will show you which files have been modified or created.
    
4. **Commit the Changes:** Use the command `git commit -m "Your commit message here"` to commit the changes to the repository. The commit message should be descriptive and explain the changes you made in the commit.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690998916992/1d8b94e3-1370-4ace-8da5-49fce0994281.png align="center")
    
    One thing to note here, We have only committed in local repo not to the remote repo(GitHub).
    

## **Excercise** 4: Push the changes back to the repository on GitHub

![Git concepts for newcomers — Part 2: Git repository, working tree and  staging area | by Sébastien Dubois. | ITNEXT](https://miro.medium.com/v2/resize:fit:1204/1*zpvd5fjZAFGsVAEsvMGKxA.png align="left")

1. Push the code: We need to push this code in order to commit the code to the remote repository.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691001841819/c21ea063-d1a5-4717-b62d-46910f2ccac1.png align="center")
    
    In order to resolve this issue, From 2021-08-13, GitHub is no longer accepting account passwords when authenticating Git operations. You need to add a **PAT (Personal Access Token)** instead, and you can follow the below method to add a PAT on your system.
    
    ## Create Personal Access Token on GitHub
    
    From your GitHub account, go to **Settings** → **Developer Settings** → **Personal Access Token** → **Generate New Token** (Give your password) → **Fillup the form** → click **Generate token** → **Copy the generated Token**, it will be something like `ghp_sFhFsSHhTzMDreGRLjmks4Tzuzgthdvfsrta`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691035485316/7097c42a-fe42-4a46-9773-5bfb83760a7b.png align="center")
    
    ```bash
    git push origin <branch-name>
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691035501368/cf804cb9-e5d6-4cee-841e-daf1e30a07c9.png align="center")
    
    Congratulations, we have completed the first Excersice for Basics Git and GitHub.