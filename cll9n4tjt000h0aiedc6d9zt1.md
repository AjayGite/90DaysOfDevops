---
title: "Linux and Git-GitHub Cheat Sheet"
datePublished: Sun Aug 13 2023 16:08:46 GMT+0000 (Coordinated Universal Time)
cuid: cll9n4tjt000h0aiedc6d9zt1
slug: linux-and-git-github-cheat-sheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691939390739/32bc13e3-0c2b-4647-bb44-ec78877793ee.png
tags: linux, github, cheatsheet, trainwithshubham, 90daysofdevopschallenge

---

here's a basic Linux file system commands cheat sheet:

**Navigating the File System:**

* `pwd`: Print working directory (displays the current directory).
    
* `ls`: List files and directories.
    
    * `ls -l`: Long format, shows detailed information.
        
    * `ls -a`: List all files, including hidden files.
        
    * `ls -lh`: Long format with human-readable file sizes.
        
* `cd`: Change directory.
    
    * `cd ..`: Move to the parent directory.
        
    * `cd ~`: Move to the home directory.
        
* `mkdir`: Create a new directory.
    
* `rmdir`: Remove an empty directory.
    

**Working with Files:**

* `touch`: Create an empty file.
    
* `cp`: Copy files or directories.
    
    * `cp source destination`: Copy a file.
        
    * `cp -r source destination`: Copy a directory recursively.
        
* `mv`: Move or rename files or directories.
    
* `rm`: Remove files or directories.
    
    * `rm file`: Remove a file.
        
    * `rm -r directory`: Remove a directory and its contents recursively.
        
* `cat`: Display the contents of a file.
    
* `more`: Display the contents of a file page by page.
    
* `less`: Display the contents of a file with backward navigation.
    
* `head`: Display the beginning of a file.
    
* `tail`: Display the end of a file.
    
* `nano` or `vim`: Text editors to create and edit files.
    

**File Permissions:**

* `chmod`: Change file permissions.
    
* `chown`: Change file ownership.
    

**Searching:**

* `grep`: Search for a pattern in files.
    
* `find`: Search for files and directories.
    
* `sort`: Sort lines of text files.
    
* `uniq`: Display or filter duplicate lines in a file.
    

**File Compression and Archiving:**

* `tar`: Create or extract tar archives.
    
    * `tar -cvf archive.tar files`: Create a tar archive.
        
    * `tar -xvf archive.tar`: Extract files from a tar archive.
        
* `gzip` or `gunzip`: Compress or decompress files.
    
    * `gzip file`: Compress a file (creates .gz file).
        
    * `gunzip file.gz`: Decompress a compressed file.
        

**Disk Usage:**

* `df`: Display disk space usage.
    
* `du`: Display file and directory space usage.
    
    * `du -h`: Human-readable sizes.
        
    * `du -sh directory`: Summarize directory size.
        

**Other:**

* `ln`: Create symbolic or hard links.
    
* `file`: Determine file type.
    
* `mount` and `umount`: Mount and unmount filesystems.
    

### **Managing Processes:**

* `ps`: Display information about currently running processes.
    
    * `ps aux`: Display detailed information about all processes.
        
    * `ps -ef`: Similar to `ps aux`, different syntax.
        
* `top`: Display real-time system monitoring and process information.
    
* `htop`: Interactive version of `top` with more features and controls.
    
* `pgrep`: Search for processes by name.
    
    * Example: `pgrep firefox` to find the process ID of the Firefox browser.
        
* `pkill`: Terminate processes by name.
    
    * Example: `pkill firefox` to terminate all Firefox processes.
        
* `kill`: Send signals to processes (commonly used with process IDs).
    
    * `kill -9 PID`: Forcefully terminate a process with the given process ID.
        
* `killall`: Terminate processes by name.
    
    * Example: `killall chrome` to terminate all Chrome browser processes.
        
* `nice` and `renice`: Adjust process priority.
    
    * `nice -n 10 command`: Run a command with a lower priority (higher niceness value).
        
    * `renice -n 5 -p PID`: Change the priority of a running process.
        

### **Background and Foreground Execution:**

* `&`: Run a command in the background.
    
    * Example: `command &` runs `command` in the background.
        
* `jobs`: List background jobs.
    
* `fg`: Bring a background job to the foreground.
    
* `bg`: Resume a suspended background job.
    

### **Process Control:**

* `Ctrl+C`: Interrupt (terminate) the currently running foreground process.
    
* `Ctrl+Z`: Suspend the currently running foreground process.
    
* `nohup`: Run a command that keeps running even after the terminal is closed.
    
    * Example: `nohup command &`.
        

### **System Monitoring and Logs:**

* `uptime`: Display system uptime and load average.
    
* `vmstat`: Display virtual memory statistics.
    
* `dmesg`: Display kernel ring buffer (boot messages).
    
* `sar`: Collect and display system activity information.
    
* `iostat`: Display I/O statistics.
    

### **Network Configuration:**

* `ifconfig` or `ip addr`: Display network interface information.
    
* `ifup interface_name`: Bring a network interface up.
    
* `ifdown interface_name`: Bring a network interface down.
    
* `ip link set interface_name up`: Another way to bring an interface up.
    
* `ip link set interface_name down`: Another way to bring an interface down.
    
* `ping host`: Send ICMP echo request packets to a host.
    
* `traceroute host`: Trace the route that packets take to reach a host.
    

### **Network Connectivity:**

* `ping host`: Check network connectivity to a host.
    
* `traceroute host`: Display the path taken by packets to reach a host.
    
* `nslookup host`: Perform DNS lookups to retrieve IP addresses.
    
* `dig host`: Another tool to query DNS information.
    
* `host host`: Display DNS information.
    

### **Networking and Transfers:**

* `wget`: Download files from the internet.
    
* `curl`: Transfer data to/from servers.
    

### **Network Diagnostics:**

* `netstat`: Display network statistics (deprecated; use `ss` instead).
    
* `ss`: Display socket statistics.
    
* `nmap host`: Perform network scanning to discover open ports and services.
    
* `arp`: Display and manipulate the ARP cache.
    
* `iftop`: Display bandwidth usage on an interface.
    
* `iftop -i interface_name`: Monitor bandwidth of a specific interface.
    

### **Firewall and Security:**

* `ufw`: Uncomplicated Firewall management tool.
    
* `iptables`: Powerful tool for configuring firewall rules.
    

### **Package Management:**

### **Debian-based Distributions (e.g., Ubuntu):**

* `apt-get update`: Update the package list.
    
* `apt-get upgrade`: Upgrade installed packages.
    
* `apt-get install package_name`: Install a package.
    
* `apt-get remove package_name`: Remove a package (keeps configuration files).
    
* `apt-get purge package_name`: Completely remove a package (including configuration files).
    
* `apt-cache search keyword`: Search for packages.
    
* `apt-cache show package_name`: Display package information.
    
* `dpkg -i package.deb`: Install a package from a .deb file.
    
* `dpkg -r package_name`: Remove a package.
    
* `dpkg -l`: List all installed packages.
    

### **Red Hat-based Distributions (e.g., CentOS):**

* `yum update`: Update installed packages.
    
* `yum install package_name`: Install a package.
    
* `yum remove package_name`: Remove a package.
    
* `yum search keyword`: Search for packages.
    
* `yum info package_name`: Display package information.
    
* `rpm -ivh package.rpm`: Install a package from an .rpm file.
    
* `rpm -e package_name`: Remove a package.
    
* `rpm -qa`: List all installed packages.
    

### **Common for Both:**

* `apt` (Ubuntu) / `yum` (CentOS): Package managers to manage software.
    
* `snap`: Package manager for installing and managing snap packages.
    
* `dnf`: Modern package manager replacing `yum` in newer Fedora distributions.
    

## **Git and GitHub Cheat Sheet: Key Operations**

### **Cloning a Repository:**

* `git clone <repository_url>`: Clone a remote repository to your local machine.
    

### **Basic Workflow:**

1. **Checking Status:**
    
    * `git status`: Check the status of your working directory and staged changes.
        
2. **Adding Changes:**
    
    * `git add <file>`: Stage a specific file for commit.
        
    * `git add .` or `git add -A`: Stage all changes for commit.
        
3. **Committing Changes:**
    
    * `git commit -m "Your commit message"`: Commit staged changes with a message.
        
4. **Pushing Changes:**
    
    * `git push origin <branch>`: Push committed changes to a remote branch.
        

### **Branching and Merging:**

1. **Creating and Switching Branches:**
    
    * `git branch`: List all branches.
        
    * `git branch <new_branch>`: Create a new branch.
        
    * `git checkout <branch>`: Switch to an existing branch.
        
2. **Merging Branches:**
    
    * `git merge <branch_to_merge>`: Merge changes from another branch into the current branch.
        

### **Pulling Changes:**

* `git pull origin <branch>`: Fetch and merge remote changes into your local branch.
    

### **Inspecting History:**

* `git log`: Display commit history.
    
* `git log --oneline`: Display compact commit history.
    
* `git diff`: Show differences between working directory and staging area.
    
* `git diff --staged`: Show differences between staging area and last commit.
    

### **Remote Repositories:**

* `git remote -v`: List remote repositories.
    
* `git remote add <name> <repository_url>`: Add a new remote repository.
    
* `git remote remove <name>`: Remove a remote repository.
    
* `git push origin -d <branch-name>` : Delete remote branch
    

### **Undoing Changes:**

* `git reset <file>`: Unstage changes from a file.
    
* `git checkout -- <file>`: Discard changes in a file.
    
* `git revert <commit>`: Create a new commit that undoes changes of a previous commit.
    

### **Resetting Commits:**

* `git reset --soft <commit>`: Move the branch pointer to a specific commit, keeping changes staged.
    
* `git reset --mixed <commit>` (default behavior): Move the branch pointer and unstage changes, preserving changes in working directory.
    
* `git reset --hard <commit>`: Move the branch pointer, unstage changes, and discard changes in working directory.
    

### **Ignoring Files:**

* Create a `.gitignore` file in the repository to list files and patterns to be ignored.
    

### **Renaming and Deleting:**

* `git mv <old_file_name> <new_file_name>`: Rename a file.
    
* `git rm <file>`: Delete a file.
    

### **Remote Collaboration:**

* `git clone <repository_url>`: Clone a remote repository.
    
* `git fetch`: Fetch changes from a remote repository.
    
* `git pull origin <branch>`: Fetch and merge remote changes.
    
* `git push origin <branch>`: Push changes to a remote branch.
    

### **Removing Untracked Files:**

* `git clean -n`: List untracked files that will be removed.
    
* `git clean -f`: Remove untracked files from the working directory.
    

### **Stashing Changes:**

* `git stash`: Stash your changes (both staged and unstaged).
    
* `git stash save "message"`: Stash changes with a descriptive message.
    

### **Listing Stashes:**

* `git stash list`: List all stashes with their IDs and messages.
    

### **Applying Stashes:**

* `git stash apply`: Apply the most recent stash and keep it in the stash list.
    
* `git stash apply stash@{n}`: Apply a specific stash by its index.
    

### **Popping Stashes:**

* `git stash pop`: Apply and remove the most recent stash.
    
* `git stash pop stash@{n}`: Apply and remove a specific stash by its index.
    

### **Dropping Stashes:**

* `git stash drop stash@{n}`: Remove a specific stash by its index.
    
* `git stash clear`: Remove all stashes.
    

Stay in the loop with my latest insights and articles on Cloud ☁️ and DevOps 🚀 by following me on Hashnode and LinkedIn.