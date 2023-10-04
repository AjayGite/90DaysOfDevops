---
title: "Basic Linux Shell Scripting for DevOps Engineers"
datePublished: Sun Jul 23 2023 17:52:56 GMT+0000 (Coordinated Universal Time)
cuid: clkfqlw46000209mh7vne61a4
slug: basic-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690123170123/ab4effee-dc2d-4acd-819e-233f808fdc1e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690134768334/1a371591-0363-40bd-b3a1-96f6f7e0964d.png
tags: trainwithshubham, tws, devops-shellscripting-automation-linux-techjourney-linkedin-continuousimprovement

---

### Introduction:

Shell scripting is a powerful skill that allows system administrators, developers, and IT professionals to automate tasks, streamline workflows, and improve productivity. In this blog, we will delve into the world of shell scripting, exploring its fundamentals, best practices, and practical examples. Whether you're a beginner looking to get started or an experienced user seeking advanced techniques, this guide will equip you with the knowledge to become proficient in shell scripting.

### What is Shell?

A shell is a command-line interface (CLI) program that provides users with a text-based way to interact with an operating system. It acts as an intermediary between the user and the operating system, allowing users to execute commands, run programs, and manage the system using text-based commands.

### What is Linux Shell Scripting?

Linux Shell Scripting refers to the practice of writing scripts using shell commands and programming constructs to automate tasks and perform various operations on a Linux or Unix-like operating system. A shell script is a series of commands written in a scripting language interpreted by the shell, which is the command-line interface (CLI) to the operating system. Shell scripts allow users to combine multiple commands, create loops, perform conditional operations, and define functions to streamline processes and improve efficiency.

### What is #!/bin/bash? can we write #!/bin/sh as well?

The `#!/bin/bash` (<mark>shebang</mark>) at the beginning of a shell script is called a shebang line. It is a special directive that tells the operating system which interpreter to use for executing the script. In this case, `#!/bin/bash` indicates that the script should be executed using the Bash shell, which is a popular shell on many Unix-like operating systems, including Linux.

Yes, you can write `#!/bin/sh` instead of `#!/bin/bash`. When you use `#!/bin/sh`, it instructs the system to use the system's default shell to execute the script. In most cases, on Linux systems, `sh` is a symbolic link to the Bourne shell or a compatible shell-like Dash, which is a lightweight POSIX-compliant shell designed for efficiency.

The main difference between using `#!/bin/bash` and `#!/bin/sh` is the shell that will interpret the script:

1. `#!/bin/bash`: When you specify `#!/bin/bash`, the script will be interpreted by the Bash shell, which provides all the features of Bash, including arrays, associative arrays, extended globbing, and other Bash-specific features.
    
2. `#!/bin/sh`: If you use `#!/bin/sh`, the script will be executed by the system's default shell, which is often the Bourne shell (sh) or a compatible shell like Dash. The Bourne shell is simpler compared to Bash and lacks some of the advanced features of Bash.
    

### Setting up the environment: Choosing a shell and installing it.

1. Check if the Shell is Installed:  
    Before proceeding, check if the shell you want to use is already installed on your system. To do this, open a terminal or command prompt and enter the following command for each shell to check its version:
    

For Bash:

```bash
[ec2-user@ip-172-31-87-129 ~]$ bash --version
GNU bash, version 5.2.15(1)-release (x86_64-amazon-linux-gnu)
Copyright (C) 2022 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

1. Install the Shell (if needed):
    
    If the shell you want to use is not installed, you can install it using the package manager specific to your operating system.
    
    For example, on Ubuntu or Debian-based systems, you can install Bash with the following command:
    

```bash
[ec2-user@ip-172-31-87-129 ~]$ sudo yum install bash
```

Replace the package manager command with the appropriate one for your Linux distribution or macOS.

Set the Default Shell (Optional):

If you want to set your preferred shell as the default shell for your user account, you can use the `chsh` command. But, before that you can install the chsh command using below command. For example, to set Bash as the default shell, use:

```bash
[ec2-user@ip-172-31-87-129 ~]$ sudo yum install util-linux-user
[ec2-user@ip-172-31-87-129 ~]$ sudo chsh -s /bin/bash ec2-user
Changing shell for ec2-user.
Shell changed.
[ec2-user@ip-172-31-87-129 ~]$ sudo cat /etc/passwd | grep -i ec2-user
ec2-user:x:1000:1000:EC2 Default User:/home/ec2-user:/bin/bash
[ec2-user@ip-172-31-87-129 ~]$
```

(by default Amazon Linux AMI only has **lchsh**, but I can not figure how it work).

Replace `/bin/bash` with the path to the shell you want to set as the default.

### /Wite a Shell Script which prints `I will complete #90DaysOofDevOps challenge`

Create a shell script with the name **90daysofdevops\_challenge.sh**

```bash
[ec2-user@ip-172-31-87-129 scripts]$ vim 90daysofdevops_challenge.sh
[ec2-user@ip-172-31-87-129 scripts]$ cat 90daysofdevops_challenge.sh 
#!/bin/bash

#Write a Shell Script which prints I will complete #90DaysOofDevOps challenge
echo "I will complete #90DaysOofDevOps challenge"
```

Provide the executable permissions to a file:

```bash
[ec2-user@ip-172-31-87-129 scripts]$ chmod 700 90daysofdevops_challenge.sh 
[ec2-user@ip-172-31-87-129 scripts]$ ./90daysofdevops_challenge.sh 
I will complete #90DaysOofDevOps challenge
```

### Write a Shell Script to take user input, input from arguments and print the variables.

Create a shell script with the name **userinput\_args\_1.sh**

```bash
[ec2-user@ip-172-31-87-129 scripts]$ vim userinput_args_1.sh
[ec2-user@ip-172-31-87-129 scripts]$ cat userinput_args_1.sh 
#!/bin/bash

#Take inputs from user
echo "Enter the name:"
read name

#Take argument from the script file and take it into variable
arg_name=$1

#Print the variables
echo "My name is : $name"
echo "Argument Take: $arg_name"
echo "Total argument: $#"
```

Provide the executable permissions to a file:

```bash
[ec2-user@ip-172-31-87-129 scripts]$ chmod 755 userinput_args_1.sh
[ec2-user@ip-172-31-87-129 scripts]$ ./userinput_args_1.sh 8 
Enter the name:
Ajay Gite
My name is : Ajay Gite
Argument Take: 8
Total argument: 1
```

**<mark>Note:</mark>**

* `$0`: The name of the script or the path to the script itself.
    
* `$1`: The first argument passed to the script.
    
* `$2`: The second argument passed to the script.
    
* `$3`: The third argument passed to the script.
    
    ### **Write an Example of If else in Shell Scripting by comparing 2 numbers.**
    

```bash
#!/bin/bash

# Taking user input for two numbers
read -p "Enter the first number: " num1
read -p "Enter the second number: " num2

# Comparing the numbers
if [ "$num1" -gt "$num2" ]; then
  echo "$num1 is greater than $num2."
elif [ "$num1" -lt "$num2" ]; then
  echo "$num1 is less than $num2."
else
  echo "Both numbers are equal."
fi
```

* `read -p` help to take the input in the same line.
    
* `-gt` means greater than.
    
* `-lt` means less than.