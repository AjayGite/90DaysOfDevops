---
title: "Advance Git & GitHub for Devops Engineers"
datePublished: Thu Aug 10 2023 10:09:41 GMT+0000 (Coordinated Universal Time)
cuid: cll4zzgra000309l72yjj468b
slug: advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691558160325/994c50de-4747-424b-b977-481cfd4f06c6.png
tags: github, trainwithshubham, 90daysofdevopschallenge

---

### Git Branching:

Git branching is a strategy where branches are created for specific features, bugs or experimental ideas by taking a clone from the main repository. Each repository typically has one default branch ("Master" or "Main") and can have multiple other branches created to work on specific features, bug fixes or experiments.

***NOTE****:* Master is basically created when you push from local to remote. Whenever we create a new repository on GitHub and clone from remote to local, Main is created.

Imagine you and your team are working on a popular messaging application called "ChatApp". Your team is responsible for adding new features and fixing bugs while ensuring a stable and reliable user experience. Here's how Git branching might work in this scenario:

➡️**Creating Branches:**  
You created two branches: "voice-message-feature" and "bug-fix-123"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691560840516/5fb15502-7cf2-41b9-8ab4-ae642beb53c8.png align="center")

These branches are like **separate environments** in Git where you'll **develop** new **features** and fix bugs.

➡️**Making Changes:**  
You switch to the "voice-message-feature" branch and start developing the voice message feature in this isolated environment.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691563643884/7bba1fde-9e28-4be9-a004-a19989455849.png align="center")

At the same time, another team member switches to the bug-fixes-123" branch and starts working on the bug-fix in its isolated environment.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691563726782/c7f771bb-ab98-4b84-8dd4-7b7c198675af.png align="center")

➡️**Merging:**  
Once both features are fully developed and tested on their respective branches, it's time to bring them together into the main application on the ChatApp (master branch).

First, you switch back to the "master" branch. Next, you merge the changes from the "voice-message-feature" and "bug-fix-123" branches into the "master" branch, ensuring that the new features and bug fixes are integrated smoothly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691563941688/2c17932e-3944-4baf-8cf3-ee6e070844fe.png align="center")

### **What is Git Revert and Reset:**

Git revert is a command in Git version control system that is used to revert the specified commit. It is a kind of **undo or reverse** command. It will create a new commit and also maintains the version history before the commit. We can revert the commit by simply `git revert <commit-id>`

Example:

You have a text file with the following content "Hello world" and You make a change to the file and commit it. Later, you realize that the change was a mistake, and you want to revert it to the original "Hello, world!" text.

You use "git revert &lt;commit-ID/hash&gt;" to create a new commit that undoes the changes made in the mistaken commit:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691574928469/87a7ba7a-ecac-44b0-959e-3b71dee83989.png align="center")

Git Reset is used to reset the changes but it deletes all the version history from where the commit has changed. There are three types of git reset - hard, soft and mixed.

* **Git reset --hard:** The --hard option changes the Commit History, and ref pointers are updated to the specified commit but any previously pending commits to the Staging area will be lost.
    
* **Git reset --mixed:** The --mixed option updates the ref pointers to the specified commit without losing any data from the Staging area.
    
* **Git reset --soft:** The --soft option is simply used to move the HEAD to the particular commit by giving the commit id along with the reset command.
    

Example:

## Git reset --hard example:

You have a project with a series of commits like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691575743951/7a9bff9a-3bd2-4136-bba7-8a1fcdc5e376.png align="center")

You're currently on commit D (the "HEAD" is pointing there).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691575805445/b42b3ff9-8ae5-4d1a-84c6-b0ab0547d06f.png align="center")

You realize that something went wrong in commit C, and you want to undo all the changes made in commits C and D.

You use "git reset" to move the "HEAD" and the branch pointer back to commit B. This doesn't erase commits C and D; it just makes them "disappear" from the current view.

After running this command, the state of your project goes back to the state of commit B:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691575961124/62db008b-eca0-4ebe-954a-d848432d9916.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691575994316/d780aaa6-97cb-43c2-9b48-7727cf76191f.png align="center")

## Git reset --soft example:

Here's how you might use `git reset --soft`:

Your commit history looks like this - `A`, `B`, and `C` represent three consecutive commits, with `C` being the latest commit (HEAD points to it).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691641043379/5a58f845-935c-4954-b09a-135b7ec72b78.png align="center")

You realize that the latest commit (`C`) contains an error, and you want to undo this commit while keeping its changes in your working directory.

**Using** `git reset --soft`: You use the `git reset --soft` command to reset the HEAD to the previous commit (`B`) while keeping the changes from commit `C` staged (ready to be committed again):

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691641074099/ef84f9e6-a1de-442c-8ab0-779f834efd9c.png align="center")

This moves the HEAD back to commit `B`, and the changes from commit `C` are now staged but not committed.

**Review and Commit**: You review the staged changes to make sure they are correct. If everything looks good, you can now create a new commit with the corrected changes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691641270841/63639138-0d7f-4304-a47a-7ababe4b32c7.png align="center")

Your commit history will now look like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691641307403/b042f1c4-6a6b-4521-a237-9728a2ce9de5.png align="center")

* `C'` represents the new commit that corrects the mistake in the commit `C`.
    

## **Git Rebase and Merge**

**Git rebase** is a linear process of merging. It combines a sequence of commits from distinct branches into a final commit. It merges the different commits one by one and the logs are modified once the action is complete. Git rebase was developed to overcome merging’s shortcomings, specifically regarding logs. Let's assume we have made three commits in the master branch and three in the test branch. If we rebase it, then it will be merged in a linear manner.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690956169951/e19031a4-3fc0-4d18-9b5d-7eca718afdb8.png?auto=compress,format&format=webp align="left")

**Git Merge** is always a forward changing record. The git merge command takes the data created by git branches and integrate them into a single branch while the logs of commits on branches remain intact. It combines a series of commits into one unified history. Let's assume we have made three commits in the master branch and three in the test. If we merge this, then it will merge all commits in a time.

Consider the below image:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690956375155/98da7bf3-ee84-45a1-a317-5207af28db5f.png?auto=compress,format&format=webp align="left")

### **👩‍💻Task 1: Branching, Committing, and Restoring:**

1\. Create a fresh branch called "dev" from the primary branch and confirm the alteration by executing the command "git checkout dev."

2\. Generate a text file labelled version01.txt and populate it with the provided content.

3\. Employ the "git add" command followed by the file names to stage the tracked changes. Subsequently, commit this update with the message "Added new feature.

4\. Push the `dev` branch to the remote repository using the command:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691657950783/dfd9c652-13a6-4950-bfb7-4580ff5c8e59.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691660939129/231b5191-242b-4594-b9e4-27ad6da6f88b.png align="center")

### **Task 2: Branching, Merging, and Rebasing**

Let's unite the "dev" branch with the "main" branch. Start by inspecting the commits on the "dev" branch using "git checkout dev" 👩‍💻. Next, switch back to the "main" branch and examine its commits as well. Finally, execute the "git merge dev" command to blend the commits and observe the fascinating outcomes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691661195789/58c29a43-1bab-4159-a711-c94cec51e52d.png align="center")

Now will run the **"git rebase dev"** command and will see the results. The working branch is switched to "master," and a rebase is performed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691661589376/b3426022-cc08-4e57-8fa8-4b3a03131d28.png align="center")

**Great job on completing Day 10 of the #90DaysOfDevOps challenge!**