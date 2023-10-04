---
title: "Day 3: Basic Linux Commands"
datePublished: Thu Jul 20 2023 17:10:20 GMT+0000 (Coordinated Universal Time)
cuid: clkberjtq000i0amd65bv6ioe
slug: day-3-basic-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689866119609/dcf408d7-05f8-4aa4-b1fa-5023708a6f2c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689873009378/94da8b70-f17a-415d-874c-3fac977621f1.png
tags: linux, devops, permissions, 90daysofdevops, trainwithshubham

---

### **1\. To view what's written in a file**

To view the contents of a file in Linux, you can use the "**cat**" command.

cat - concatenate files and print on the standard output.

```bash
[ec2-user@ip-172-31-87-129 ~]$ echo "Task 3: Basic Linux Commands #90DaysOfDevops" > tasks
[ec2-user@ip-172-31-87-129 ~]$ cat tasks 
Task 3: Basic Linux Commands #90DaysOfDevops
```

### **2\. To change the access permissions of files.**

We can use the "**chmod"** command which allows us to modify the permissions using a numeric or symbolic representation, which stands for "change mode".

Syntax:

```bash
chmod <permissions> <filename>
```

**chmod in Linux \[options\]**

\-R - Apply the permission change recursively to all the files and directories within the specified directory.

\-v - It will display a message for each file that is processed. while indicating the permission change that was made.

\-f - It helps in avoiding the display of error messages.

\-h - Change the permissions of symbolic links instead of the files they point to.

**The following letters can be used in symbolic mode:**

r -&gt; Read permission

w -&gt; Write permission

x -&gt; Execute permission

**The following reference are used:**

u -&gt; Owner

g -&gt; Group

o -&gt; Others

a -&gt; All (owner,group,others)

Let's learn to change the permissions of files, by using octal and symbolic - For example:

* Read, write and execute permissions to the file owner:
    

```bash
[ec2-user@ip-172-31-87-129 ~]$ ls -l
total 4
-rw-r--r--. 1 ec2-user ec2-user 45 Jul 20 15:18 tasks
[ec2-user@ip-172-31-87-129 ~]$ chmod u+rwx tasks 
[ec2-user@ip-172-31-87-129 ~]$ ls -l
total 4
-rwxr--r--. 1 ec2-user ec2-user 45 Jul 20 15:18 tasks
[ec2-user@ip-172-31-87-129 ~]$ 
```

* Read for Owner, and no permission for group and others:
    

```bash
[ec2-user@ip-172-31-87-129 ~]$ ls -l
total 4
-rwxrwxrwx. 1 ec2-user ec2-user 45 Jul 20 15:18 tasks
[ec2-user@ip-172-31-87-129 ~]$ chmod u-r,go-rwx tasks
[ec2-user@ip-172-31-87-129 ~]$ ls -l
total 4
--wx------. 1 ec2-user ec2-user 45 Jul 20 15:18 tasks
[ec2-user@ip-172-31-87-129 ~]$
```

#### **Examples of Using the Octal mode:**

```bash
[ec2-user@ip-172-31-87-129 ~]$ ls -l
total 4
--wx------. 1 ec2-user ec2-user 45 Jul 20 15:18 tasks
[ec2-user@ip-172-31-87-129 ~]$ chmod 777 tasks 
[ec2-user@ip-172-31-87-129 ~]$ ls -l
total 4
-rwxrwxrwx. 1 ec2-user ec2-user 45 Jul 20 15:18 tasks
[ec2-user@ip-172-31-87-129 ~]$
```

### **3\. To check which commands you have run till now.**

You can use the history command to check the previously executed commands:

```bash
[ec2-user@ip-172-31-87-129 ~]$ history | tail -n 11
  431  clear
  432  ls -l
  433  chmod u-r,go-rwx tasks
  434  ls -l
  435  clear
  436  ls -l
  437  chmod 777 tasks 
  438  ls -l
  439  man history 
  440  clear
  441  history 
```

### **4.To remove a directory/ folder**

rmdir command is used to remove the empty directories in Linux.

```bash
[ec2-user@ip-172-31-87-129 ~]$ mkdir 90DaysOfDevops
[ec2-user@ip-172-31-87-129 ~]$ cd 90DaysOfDevops/
[ec2-user@ip-172-31-87-129 90DaysOfDevops]$ ls
[ec2-user@ip-172-31-87-129 90DaysOfDevops]$ cd ..
[ec2-user@ip-172-31-87-129 ~]$ rmdir 90DaysOfDevops/
[ec2-user@ip-172-31-87-129 ~]$
```

To remove the nested directories in Linux

```bash
[ec2-user@ip-172-31-87-129 ~]$ mkdir -p GitHUb/Docker/Jenkins
[ec2-user@ip-172-31-87-129 ~]$ tree
.
├── GitHUb
    └── Docker
        └── Jenkins

3 directories, 1 file
[ec2-user@ip-172-31-87-129 ~]$ rmdir -p GitHUb/Docker/Jenkins/
[ec2-user@ip-172-31-87-129 ~]$ ls -l
total 0
[ec2-user@ip-172-31-87-129 ~]$
```

### **5\. To create a fruits.txt and to view the content.**

touch command is used to create an empty file and cat command to view the contents.

```bash
[ec2-user@ip-172-31-87-129 ~]$ touch fruits.txt 
[ec2-user@ip-172-31-87-129 ~]$ cat fruits.txt
Apple
Banana
```

### **6\. Add content in fruits.txt(One in each line) - Apple, Mango, Banana, Cherry, Kiwi, Orange, Guava.**

Using echo command we can insert all the fruits using one command in txt files

```bash
[ec2-user@ip-172-31-87-129 ~]$ echo $'Apple\nMango\nBanana\nCherry\nKiwi\nOrange\nGuava' > fruits.txt 
[ec2-user@ip-172-31-87-129 ~]$ cat fruits.txt 
Apple
Mango
Banana
Cherry
Kiwi
Orange
Guava
[ec2-user@ip-172-31-87-129 ~]$
```

### **7\. To show only the top three fruits from the file.**

head command is used to display the top three fruits.

```bash
[ec2-user@ip-172-31-87-129 ~]$ head -n 3 fruits.txt 
Apple
Mango
Banana
[ec2-user@ip-172-31-87-129 ~]$
```

### **8\. To show only the last three fruits from the file.**

tail command is used to display last three furits

```bash
[ec2-user@ip-172-31-87-129 ~]$ tail -n 3 fruits.txt 
Kiwi
Orange
Guava
[ec2-user@ip-172-31-87-129 ~]$
```

### **9\. Create a colors.txt file and to view the content.**

Touch command is used to create a file and cat command to view the content

```bash
[ec2-user@ip-172-31-87-129 ~]$ touch colors.txt
[ec2-user@ip-172-31-87-129 ~]$ cat colors.txt 
[ec2-user@ip-172-31-87-129 ~]$
```

### **10\. Add content in Colors.txt (One in each line) - Red, Pink, White, Black, Blue, Orange, Purple, Grey.**

Using echo command we can insert all the colors using one command in txt files.

```bash
[ec2-user@ip-172-31-87-129 ~]$ echo $'Red\nPink\nWhite\nBlack\nBlue\nOrange\nPurple\nGrey' > colors.txt 
[ec2-user@ip-172-31-87-129 ~]$ cat colors.txt 
Red
Pink
White
Black
Blue
Orange
Purple
Grey
[ec2-user@ip-172-31-87-129 ~]$
```

### **11\. To find the difference between fruits.txt and colors.txt file.**

diff stands for **difference**. This command is used to display the differences in the files by comparing the files line by line.

```bash
[ec2-user@ip-172-31-87-129 ~]$ diff fruits.txt colors.txt 
1,5c1,5
< Apple
< Mango
< Banana
< Cherry
< Kiwi
---
> Red
> Pink
> White
> Black
> Blue
7c7,8
< Guava
---
> Purple
> Grey
[ec2-user@ip-172-31-87-129 ~]$
```