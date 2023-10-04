---
title: "Demystifying File Permissions and Access Control Lists (ACLs)"
datePublished: Wed Jul 26 2023 10:50:29 GMT+0000 (Coordinated Universal Time)
cuid: clkjlu6e400020amc2bxmdq6q
slug: demystifying-file-permissions-and-access-control-lists-acls
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690282146493/6a4baaf7-5e78-4053-8381-e70aeb2ff323.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690368594540/fd780730-837c-4ba2-9fa0-acb00375ab8b.jpeg
tags: 90daysofdevops, trainwithshubham, tws, linuxpermissions-userpermissions-filepermissions-directorypermissions-linuxsecurity-accesscontrol-setuid-setgid-stickybit-linuxuseraccounts-ownershipandpermissions-linuxfilesystem-commandline-linuxadministration-systemsecurity

---

File permissions and Access Control Lists (ACLs) are powerful tools that allow system administrators to control access to files and directories on Unix-like systems. In this blog, we will delve into the concepts of file permissions and ACLs, along with practical examples to illustrate their usage and importance in data security.

## Basic Types of Permissions in Linux File Systems:

The three basic types of permissions in Linux are <mark>read (r)</mark>, <mark>write (w)</mark>, and <mark>execute (x)</mark>. They are represented as three characters in the permission string for each file or directory.

**The following letters can be used in symbolic mode:**

r -&gt; Read permission

w -&gt; Write permission

x -&gt; Execute permission

**The following reference is used:**

u -&gt; Owner

g -&gt; Group

o -&gt; Others

a -&gt; All (owner, group, others)

For example, "rw-r--r--" represents read and write permissions for the owner, and read-only permissions for the group and others.

To add execute permissions for the owner, group and others on a file named "<mark>file.txt</mark>" you can use the following command:

```bash
[ec2-user@ip-172-31-87-129 day6]$ touch file1.txt && ls -lrth
total 0
-rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 17:17 file1.txt
[ec2-user@ip-172-31-87-129 day6]$ chmod ugo+w file1.txt && ls -lrth
total 0
-rw-rw-rw-. 1 ec2-user ec2-user 0 Jul 25 17:17 file1.txt
```

### Explain the octal notation used to set file permissions in Linux.

Octal notation represents file permissions using a three-digit number. Each digit corresponds to a permission set for the owner, group, and others, respectively. The value of each digit is a sum of the following values: <mark>4 for read (r), 2 for write (w), and 1 for execute (x).</mark>

For example, "chmod 666 file.txt" sets read and write permissions for the owner, and read-only permissions for the group and others.

```bash
[ec2-user@ip-172-31-87-129 day6]$ touch file.txt && ls -lrth
total 0
-rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 17:30 file.txt
[ec2-user@ip-172-31-87-129 day6]$ chmod 666 file.txt && ls -lrth
total 0
-rw-rw-rw-. 1 ec2-user ec2-user 0 Jul 25 17:30 file.txt
```

### Changing the ownership of a file and directory:

The command that can use here is "<mark>chown</mark>" which stands for "change owner" and is used to change the ownership of files and directories.

Let's deep dive into it by practising some examples:

1. Changing the ownership of a file:
    
    Let's say you have a file named "file.txt" owned by the user "ec2-user" in the group "ec2-user," and you want to change the ownership to "user1" in the group "group1." You would use the following command:
    
    ```bash
    [ec2-user@ip-172-31-87-129 day6]$ sudo chown user1:group1 file.txt 
    [ec2-user@ip-172-31-87-129 day6]$ ls -l
    -rw-r--r--. 1 user1 group1 0 Jul 25 18:14 file.txt
    ```
    
2. Changing the ownership of a directory:
    
    Suppose you have a directory named "data" owned by "user1" in "group1," and you want to change the ownership of the entire directory and its contents to "user2" in "group2." You would use the following command:
    
    ```bash
    [ec2-user@ip-172-31-87-129 day6]$ ls -l
    drwxr-xr-x. 2 user1 group1 6 Jul 25 18:18 data
    [ec2-user@ip-172-31-87-129 day6]$ sudo chown -R user2:group2 data
    [ec2-user@ip-172-31-87-129 day6]$ ls -l
    drwxr-xr-x. 2 user2 group2 6 Jul 25 18:18 data
    ```
    
    The "-R" option stands for "recursive," which means it will change ownership for all files and subdirectories within the "data" directory.
    
3. Recovering ownership after an FTP upload:
    
    Sometimes, when you upload files to a server using FTP (File Transfer Protocol), the ownership might get changed to the FTP user.
    
    In such cases, you can use "<mark>chown</mark>" to restore the correct ownership. For example:
    
    ```bash
    [ec2-user@ip-172-31-87-129 day6]$ sudo chown -R www-data:www-data /var/www/html
    ```
    

This command sets the ownership of all files and directories within "/var/www/html" to the user "www-data" and the group "www-data," which is a common web server user and group.

## Changing group ownership of a file and directory:

The "<mark>chgrp</mark>" command is another Unix-like operating system command that allows you to change the group ownership of files and directories.

1. Changing group ownership of a file:
    
    Suppose you have a file named "file.txt" owned by the user "user1" in the group "group1," and you want to change the group ownership to "group2." You would use the following command.
    

```bash
[ec2-user@ip-172-31-87-129 day6]$ ls -l file.txt 
-rw-r--r--. 1 user1 group1 0 Jul 25 18:14 file.txt
[ec2-user@ip-172-31-87-129 day6]$ sudo chgrp group2 file.txt && ls -l
-rw-r--r--. 1 user1 group2 0 Jul 25 18:14 file.txt
```

1. Changing group ownership of multiple files:
    
    You can change the group ownership of multiple files at once by specifying them as arguments to the "<mark>chgrp</mark>" command. For instance:
    
    ```bash
    [ec2-user@ip-172-31-87-129 day6]$ touch file{1..10}
    [ec2-user@ip-172-31-87-129 day6]$ ls -l
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file1
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file2
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file3
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file4
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file5
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file6
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file7
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file8
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file9
    -rw-r--r--. 1 ec2-user ec2-user 0 Jul 25 18:30 file10
    
    [ec2-user@ip-172-31-87-129 day6]$ sudo chgrp group2 file{1..10}
    [ec2-user@ip-172-31-87-129 day6]$ ls -l
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file1
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file2
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file3
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file4
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file5
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file6
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file7
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file8
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file9
    -rw-r--r--. 1 ec2-user group2 0 Jul 25 18:30 file10
    ```
    
2. Recursively changing group ownership of a directory:
    
    If you want to change the group ownership of a directory and all its contents (files and subdirectories) recursively, you can use the "-R" option, similar to "chown."
    
    For example:
    
    ```bash
    [ec2-user@ip-172-31-87-129 day6]$ ls -lrth
    total 0
    drwxr-xr-x. 2 user2 group2 6 Jul 25 18:18 data
    [ec2-user@ip-172-31-87-129 day6]$ sudo chgrp -R group1 data
    [ec2-user@ip-172-31-87-129 day6]$ ls -lrth
    total 0
    drwxr-xr-x. 2 user2 group1 6 Jul 25 18:18 data
    [ec2-user@ip-172-31-87-129 day6]$
    ```
    
    This command sets the group ownership of all files and directories within "<mark>data</mark>" to the group "<mark>group2</mark>."
    

## Empowering Access Control: Linux ACLs with Real-World Examples

Linux ACLs are extensions of the standard file permissions, enabling administrators to set more nuanced access controls for files and directories. An ACL entry consists of a user or group, along with a set of permissions, such as read (r), write (w), and execute (x).

1. Setting ACL Permissions
    

Example 1: Granting Specific User Access to a File

Suppose we have a file called "sensitive\_file.txt," and we want to give "user1" read and write access:

```bash
[ec2-user@ip-172-31-87-129 day6]$ grep -E 'user1luser2' /etc/passwd
user1:: 1002:1002::/home/user1:/bin/bash
user2:x: 1003:1003::/home/user2:/bin/bash
|[ec2-user@ip-172-31-87-129 day6]$ getfacl sensitive_file.txt
# file: sensitive_file.txt
# owner: ec2-user
# group: ec2-user
user:: rw-
group:: r--
other::p-
[ec2-user@ip-172-31-87-129 day6]$ setfacl -m u:user1:rw sensitive_file.txt[[ec2-user@ip-172-31-87-129 day6]$ getfacl sensitive_file.txt
# file: sensitive_file.txt
# owner: ec2-user
# group: ec2-user
user:: rw-
user:user1: rw-
group::r-
mask:: rw-
other:: r-
```

1. Modifying ACL Permissions
    

Example 2: Adding Permissions for a Group

In a shared project folder, we want to allow the "project\_team" group to read, write, and execute all files:

```bash
[ec2-user@ip-172-31-87-129 day6]$ getfacl project_folder/
# file: project_folder/
# owner: ec2-user
# group: ec2-user
user::rwx
group::r-x
other::r-x
[ec2-user@ip-172-31-87-129 day6]$ setfacl -m g:group1:rwx -R project_folder/
[ec2-user@ip-172-31-87-129 day6]$ getfacl project_folder/
# file: project_folder/
# owner: ec2-user
# group: ec2-user
user::rwx
group::r-x
group:group1:rwx
mask::rwx
other::r-x
```

The "-R" flag ensures that the permissions are applied recursively to all files and subdirectories within the "project\_folder."

1. Removing ACL Entries
    

Example 3: Revoking Access for a User

Let's say we want to revoke all access for "user1" to the "confidential\_file.doc":

```bash
[ec2-user@ip-172-31-87-129 project_folder]$ getfacl file.txt 
# file: file.txt
# owner: ec2-user
# group: ec2-user
user::rw-
user:user1:rw-
group::r--
group:group1:rwx
mask::rwx
other::r--

[ec2-user@ip-172-31-87-129 project_folder]$ setfacl -x u:user1 file.txt 
[ec2-user@ip-172-31-87-129 project_folder]$ getfacl file.txt 
# file: file.txt
# owner: ec2-user
# group: ec2-user
user::rw-
group::r--
group:group1:rwx
mask::rwx
other::r--
```

1. Setting Default ACLs
    

Example 4: Defining Default ACLs

For a shared directory, we want to ensure that all newly created files inherit specific permissions for the "project\_folder" group:

```bash
[ec2-user@ip-172-31-87-129 day6]$ getfacl project_folder/
# file: project_folder/
# owner: ec2-user
# group: ec2-user
user::rwx
group::r-x
group:group1:rwx
mask::rwx
other::r-x

[ec2-user@ip-172-31-87-129 day6]$ setfacl -d -m g:group2:rwx project_folder/
[ec2-user@ip-172-31-87-129 day6]$ getfacl project_folder/
# file: project_folder/
# owner: ec2-user
# group: ec2-user
user::rwx
group::r-x
group:group1:rwx
mask::rwx
other::r-x
default:user::rwx
default:group::r-x
default:group:group2:rwx
default:mask::rwx
default:other::r-x
```

Now, any new file created within "project\_folder" will automatically inherit "rwx" permissions for the "shared\_group."