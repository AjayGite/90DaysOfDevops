---
title: "Advanced Linux Shell Scripting for DevOps Engineers: Streamlining Automation and Optimization"
datePublished: Tue Jul 25 2023 08:27:09 GMT+0000 (Coordinated Universal Time)
cuid: clki19ztx000009jw9eike5qs
slug: advanced-linux-shell-scripting-for-devops-engineers-streamlining-automation-and-optimization
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690220305760/c5701726-e8a0-4df8-acc0-09bcf2a60cfb.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690273615516/4995bed1-3b40-4c11-97a7-f8596d52e589.jpeg
tags: linux, devops, user-management, trainwithshubham, shellscripting

---

Hello DevOps Engineers and fellow tech enthusiasts! In this blog, we will embark on an exciting journey into the realm of Advanced Linux Shell Scripting. As DevOps professionals, mastering shell scripting is a game-changer, empowering us to automate complex tasks, optimize workflows, and enhance system efficiency.

## **Task 1: Bash Script to Create Dynamic Directories!**

**Example 1:**

```bash
./createDirectories.sh
```

This will create 90 directories as day\_1, day\_2, day\_3, ..., day\_90.

🌟 Here's the enchanting [`createDirectories.sh`](http://createDirectories.sh) script:

```bash
#!/bin/bash

# Create 90 directories using a for loop

directory="day"

for (( i=1;i<=90;i++ ));
do
	mkdir "${directory}_${i}"
	echo ""${directory}_${i}" have been successfully created"
done
```

**Example 2:**

```bash
./createDirectories_args.sh Movie 20 50
```

This will create 30 directories as Movie20, Movie21, Movie22, ..., Movie50.

🌟 Here's the enchanting [`createDirectories_args.sh`](http://createDirectories.sh) script:

```bash
#!/bin/bash

directory_name=$1
start=$2
end=$3

for (( i=start; i<=end; i++ ))
do
  dir_name="$directory_name$i"
  mkdir $dir_name
  echo "Created directory: $dir_name"
done
```

Get ready to watch the magic unfold as the script creates directories with dynamic names.

## **Task 2: Create a Script to back up all your work done till now:**

Now let's create the backup\*\*.\*\*sh, a file which we can run and create the backup of the contents that are present in scripts directory.

```bash
[ec2-user@ip-172-31-87-129 scripts]$ cat backup.sh 
#!/bin/bash

#Name of the source and destination backup file
backup_source="/home/ec2-user/90DaysOfDevOps/scripts"
backup_destination="/home/ec2-user/90DaysOfDevOps/scripts/backup"

#Create a timestamp for the backup filename
time=$(date +"%m%d%Y_%H%M%S")

#Create a backup filename with timestamp
backup_filename="backup_file_${time}.tar.gz"

#Command to create the backup of a file
tar -czvf "${backup_destination}/${backup_filename}" "${backup_source}"
```

We are using tar command here to archive and also compress the file to create a backup file.

* In the command ***tar -czvf,*** **c** indicates **create, z** is used to zip/compress the file,v= enables verbose mode which means ***tar*** will display detailed information about the files being archived.
    
* `-f "${backup_destination}/${backup_filename}"`: The `-f` option is used to specify the filename of the archive that will be created. `${backup_destination}/${backup_filename}` is the full path to the backup file, which combines the `backup_destination` (destination directory) with the `backup_filename` (the name of the backup file).
    
* `"backup_source"`: This is the source directory that we want to back up.
    

Upon execution of the backup.sh, we get the following result :)

```bash
[ec2-user@ip-172-31-87-129 scripts]$ bash backup.sh
[ec2-user@ip-172-31-87-129 scripts]$ cd backup/
[ec2-user@ip-172-31-87-129 backup]$ ls
backup_file_07252023_065527.tar.gz
[ec2-user@ip-172-31-87-129 backup]$
```

## **Cron Job & Crontab:**

* Cron Job: A cron job is a scheduled task that allows you to automate repetitive tasks by scheduling them to run at specified intervals or times.
    
* Crontab: Each scheduled task, known as a "cron job," is defined in a crontab (cron table) file. The crontab file contains a list of commands or scripts along with the timing information for when each command should be executed.
    

```bash
Syntax for a crontab:
* * * * * command_to_be_executed
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690060990845/dc35c150-62d8-48da-a2ea-7a7272d05764.avif?auto=compress,format&format=webp align="left")

* Some useful commands crontab commands to use in the terminal :
    
    * `crontab -e`: Edit the crontab file, or create one if it doesn’t already exist.
        
    * `crontab -l`: Display crontab file contents.
        
    * `crontab -r`: Remove your current crontab file.
        
    * `crontab -i`: Remove your current crontab file with a prompt before removal.
        

**Example**:

1. Type the command: crontab -e to edit the cron schedule.
    
2. To run it daily at 8:00 PM, write:
    

```bash
[ec2-user@ip-172-31-87-129 backup]$ crontab -e
[ec2-user@ip-172-31-87-129 backup]$ crontab -l
20 * * * * /home/ec2-user/90DaysOfDevOps/scripts/backup.sh
```

Save the cron schedule and exit the text editor.

## User management in Linux:

User management is at the heart of system security and access control. By properly managing users and their permissions, DevOps engineers can ensure the right people have the right access to resources, prevent unauthorized access, and safeguard critical data.

Let's create 2 users:

```bash
[root@ip-172-31-87-129 ~]# useradd user1
[root@ip-172-31-87-129 ~]# useradd user2
[root@ip-172-31-87-129 ~]# cd /home/
[root@ip-172-31-87-129 home]# ls
ec2-user  user1  user2
```

To modify user properties, such as their password or home directory, use the "**usermod**" command. For example:

```bash
[root@ip-172-31-87-129 home]# mkdir directory
[root@ip-172-31-87-129 home]# ls
directory  ec2-user  user1  user2
[root@ip-172-31-87-129 home]# usermod -d /home/directory user1
```

* \-d: new home directory for the user account
    

To display the usernames that were created:

```bash
[root@ip-172-31-87-129 ~]# grep -E 'user1|user2' /etc/passwd
user1:x:1002:1002::/home/directory:/bin/bash
user2:x:1003:1003::/home/user2:/bin/bash
```

* \-E: This option treats the pattern you used as an **extended regular expression**.
    

To delete a user:

```bash
[root@ip-172-31-87-129 home]# userdel -r user1
[root@ip-172-31-87-129 home]# userdel -r user2
```

* \-r - remove home directory and mail spool
    

## Conclusion:

As we embark on this enriching journey, you will witness the true power of shell scripting as it transforms your DevOps workflow. From simplifying server management to orchestrating complex deployments, you will have the skills to optimize processes, minimize downtime, and enhance collaboration across your team.

Our goal is to empower you with the expertise to leverage shell scripting as a potent tool to overcome challenges and drive innovation in modern software development. So, buckle up and get ready to elevate your DevOps journey through the power of Advanced Linux Shell Scripting!

Stay tuned for our upcoming posts, where we'll dive into specific advanced techniques, real-world use cases, and tips to enhance your scripting prowess. Together, we'll revolutionize the world of DevOps, one script at a time.

Happy scripting and happy DevOps-ing! 🚀