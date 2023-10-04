---
title: "Deep Dive In Git & Github For Devops Engineer"
datePublished: Sun Aug 06 2023 10:13:11 GMT+0000 (Coordinated Universal Time)
cuid: clkzackh600040amrcy7u5h7k
slug: deep-dive-in-git-github-for-devops-engineer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691242744801/32b13faf-c3dc-48ad-945c-896793067324.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691316766508/cbe2f7af-c883-4284-93f6-932b3e42bcd2.png
tags: github, 90daysofdevops, trainwithshubham

---

### What is Git and why is it important?

Git is a distributed version control system (DVCS) that allows multiple developers to work together on the same project without stepping on each other toes. It gives you to track changes in your code and collaborate seamlessly with your team.

**Importance of Git with Examples**:

1. **Version Control**: Git allows developers to track changes to files and directories over time. This ensures that a comprehensive history of the project's development is maintained. For example, if you're working on a software project and you encounter a bug, you can use Git to trace back to the specific commit that introduced the bug and fix it.
    
2. **Collaboration**: Git enables multiple developers to work on the same project simultaneously. Each developer can work on their own local copy of the code, make changes, and then merge their changes back into the main codebase. For instance, if you and your colleague are both developing different features of an application, Git helps you merge your changes without conflicts.
    
3. **Branching and Merging**: Git allows you to create branches, which are independent lines of development. This is useful for experimenting with new features or isolating bug fixes. You can then merge these branches back into the main codebase when they are ready. For example, you can create a branch to work on a new feature, test it thoroughly, and then merge it into the main branch.
    
4. **Code Reviews**: Git facilitates code reviews by allowing developers to share their changes with others before merging them into the main codebase. This ensures that code quality is maintained and potential issues are caught early. For instance, you can create a pull request in Git to review and discuss the changes you've made with your team before merging them.
    
5. **Rollbacks and Reverts**: If a problem arises after a code change, Git makes it easy to roll back to a previous version of the code. This is helpful in case a new feature introduces unexpected issues. For instance, you can quickly revert to a stable state of the project if a critical bug is discovered after a release.
    
6. **Open Source Collaboration**: Git plays a crucial role in open-source software development. It allows developers from around the world to contribute to projects without needing direct access to the main repository. Contributors can fork the repository, make changes, and submit pull requests to have their changes considered for merging.
    

**Example Scenario**: Imagine you're part of a team developing a mobile app. You use Git to manage the project. Each team member creates a local copy of the repository. As you work on your assigned tasks, you make commits to your local repository to track your changes. When a feature is complete, you push your changes to a shared remote repository on a platform like GitHub. Your team members review the changes, and after approval, the changes are merged into the main branch. If a critical bug is discovered in the main branch, you can create a hotfix branch, fix the bug, and merge it back quickly, while the rest of the team continues their work in parallel.

### What is the difference Between Main Branch and Master Branch?

Here's a table comparing the "main" branch and the "master" branch in Git repositories, along with corresponding examples:

| **Aspect** | **"master" Branch** | **"main" Branch** |
| --- | --- | --- |
| Default Name | "master" is the traditional default branch name | "main" is an alternative recommended by Git and many communities |
| Purpose | Serves as the primary development branch | Serves as the primary development branch |
| Historical Connotation | Some critics argue that "master" has negative historical connotations | Aims to avoid potentially insensitive language |
| Feature Branch Creation | Create and work on feature branches based on "master" | Create and work on feature branches based on "main" |
| Merging Changes | Merge feature branches back into "master" | Merge feature branches back into "main" |
| Example - Creating a Branch | `$ git checkout -b feature-login`&lt;br&gt; (create a new feature branch) | `$ git checkout -b feature-login`&lt;br&gt; (create a new feature branch) |
| Example - Making Changes | `$ git add .`&lt;br&gt; `$ git commit -m "Added login feature"` | `$ git add .`&lt;br&gt; `$ git commit -m "Added login feature"` |
| Example - Merging Changes | `$ git checkout master`&lt;br&gt; `$ git merge feature-login` | `$ git checkout main`&lt;br&gt; `$ git merge feature-login` |

### Can you explain the difference between Git and GitHub?

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Aspects</strong></p></td><td colspan="1" rowspan="1"><p><strong>Git</strong></p></td><td colspan="1" rowspan="1"><p><strong>GitHub</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>Owned by</p></td><td colspan="1" rowspan="1"><p>Git is maintained by Linux</p></td><td colspan="1" rowspan="1"><p>Is maintained by Microsoft.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Location</p></td><td colspan="1" rowspan="1"><p>Git lives on the Developer's personal computer.</p></td><td colspan="1" rowspan="1"><p>GitHub is a Cloud-based platform accessible through a web browser.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Application</p></td><td colspan="1" rowspan="1"><p>Git is a Command-Line tool.</p></td><td colspan="1" rowspan="1"><p>GitHub is a Graphical User Interface.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Storage</p></td><td colspan="1" rowspan="1"><p>Is installed locally in the system for use and does not require the internet.</p></td><td colspan="1" rowspan="1"><p>Can be accessed through the web browser. It needs an internet connection.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Usage</p></td><td colspan="1" rowspan="1"><p>Developers use Git to work on their code locally and track changes efficiently.</p></td><td colspan="1" rowspan="1"><p>Developers use GitHub to save their Git repositories in the cloud and collaborate with others.</p></td></tr><tr><td colspan="1" rowspan="1"><p>User Preferences</p></td><td colspan="1" rowspan="1"><p>Lacks user management features - It provides core version control functions like creating branches, committing changes and maintaining history.</p></td><td colspan="1" rowspan="1"><p>GitHub has features like issue tracking, project management, code reviews and collaboration tools. It also provides Organisational and Enterprise level accounts with unlimited public repositories and collaborators.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Security</p></td><td colspan="1" rowspan="1"><p>The privacy in Git is too strong</p></td><td colspan="1" rowspan="1"><p>Privacy depends on the settings of the repositories.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Platform</p></td><td colspan="1" rowspan="1"><p>It is compatible with Windows, macOS, Linux, Solaris, AIX</p></td><td colspan="1" rowspan="1"><p>It is compatible with Windows, macOS, Linux, and all other web browsers.</p></td></tr><tr><td colspan="1" rowspan="1"><p>Collaboration</p></td><td colspan="1" rowspan="1"><p>Git is more suitable for individual developers working on their own projects or small teams working together locally.</p></td><td colspan="1" rowspan="1"><p>GitHub brings developers together on a global scale, facilitating among multiple developers, teams, and open-source communities.</p></td></tr></tbody></table>

### How do you create a new repository on GitHub?

Creating a new repository on GitHub is as easy as pie! Just follow these simple steps:

1. **Sign in or Sign up:** If you already have a GitHub account, sign in. If not, create a new account—it's quick and free on [**https://github.com/**](https://github.com/)
    
2. **Find the "+" sign:** Once you're logged in, look for the "+" sign in the top-right corner of the page.
    
3. **Click "New repository":** Click on that "+" sign, and a menu will pop up. Choose "New repository" from the menu.
    
4. **Name your repository:** Give your new repository a cool name that describes what it's all about. You can be creative!
    
5. **Add a description (optional):** If you want to let others know what your repository is for, you can add a brief description.
    
6. **Public or Private:** Decide whether you want your repository to be visible to everyone (public) or just you and some friends (private).
    
7. **Optional extras:** You can also choose to add a README file (a cool way to introduce your project), a .gitignore file (to ignore certain files), and even a license to let others know how they can use your code.
    
8. **Click "Create repository":** Finally, when you're all set, click that button, and voilà! Your new repository is ready to go.
    

### **Difference between local & remote repository? How to connect local to remote?**

Here's a comparison between local and remote repositories, presented in a table format:

| **Aspect** | **Local Repository** | **Remote Repository** |
| --- | --- | --- |
| Location | Exists on your local computer | Hosted on a remote server (e.g., GitHub) |
| Accessibility | Only accessible on your machine | Accessible to multiple contributors |
| History | Contains the entire version history | Contains the same version history as local |
| Collaboration | Primarily for individual development | Facilitates collaborative development |
| Privacy | Private, not directly accessible by others | Shared among collaborators and team members |
| Backup | Not automatically backed up | Acts as a remote backup of your work |
| Connection | No network connection needed to work | Requires network connection for collaboration |
| Branches and Commits | All branches and commits are local | Reflects branches and commits from local |

## **How to connect local to remote?**

To connect your local repository to a remote repository, we need to perform the below steps using Git, which is a widely used version control system.

Let's assume we already have a local repository set up on your computer and have created a remote repository on a platform like GitHub, GitLab, or Bitbucket.

Here's a step-by-step guide to connecting your local repository to a remote repository:

1. **Obtain the Remote Repository URL:**
    
    * Go to your remote code hosting platform (e.g., GitHub) and navigate to the repository you want to connect to.
        
    * Look for the "Clone" or "Code" button and copy the remote repository's URL. It should look something like: [**https://github.com/username/repo-name.git**](https://github.com/username/repo-name.git)[**.**](https://github.com/username/repo-name.git.%EF%BF%BC)
        
2. **Open Terminal (or Command Prompt) on Your Local Machine:**
    
    * Navigate to the directory where your local repository is located using the cd command (e.g., cd path/to/your/repo).
        
3. **Set Up Git Configuration:**
    
    * If you haven't already configured Git on your local machine, you may need to set up your name and email address. Use the following commands, replacing the placeholders with your actual name and email:
        

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

1. **Add Remote Origin:**
    
    * Run the following command to add the remote repository's URL as the **"origin"** for your local repository. This step connects from local repository to the remote one:
        

```bash
git remote add origin <remote_repository_url>
```

* Replace &lt;remote\_repository\_url&gt; with the URL we have copied in **step 1**
    

1. **Push to Remote Repository:**
    
    * Now that the connection is established, you can push your local repository's code to the remote repository using the following command:
        
        ```bash
          git push -u origin main
        ```
        
    * The **\-u** option is used to **set the upstream** branch, so you can use git push without additional arguments in the future.
        
2. **Verify Connection:**
    
    * After pushing the code, refresh the remote repository's web page (e.g., on GitHub). You should see your code and files from the local repository now available in the remote repository.
        

Your local repository is now connected to the remote repository, and you can start collaborating with others, push and pull changes, and manage version control across both local and remote environments.

## Task 1: Set your user name and email address, which will be associated with your commits.

To set your user name and email address for commits using the following Git commands:

1. **Set User Name:** Use the following command to set your Git user name:
    

```bash
git config --global user.name "Your Name"
```

1. **Set Email Address:** Use the following command to set your Git email address:
    

```bash
git config --global user.email "your@email.com"
```

We have completed the blog on Git and GitHub.