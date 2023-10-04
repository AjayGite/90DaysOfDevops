---
title: "Python Libraries For DevOps"
datePublished: Sun Aug 20 2023 12:06:28 GMT+0000 (Coordinated Universal Time)
cuid: clljek66t000209jtcfdbd9s6
slug: python-libraries-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692532731622/5e9fe855-4e88-4136-b1f9-e545bee14fa0.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692533179802/130825a5-5c83-4924-b2e1-131b998b178b.png
tags: python, python-libraries, 90daysofdevops, day15, trainwithshubham

---

# **1\. Python In-Built Libraries**

Python has a wide range of built-in libraries that provide developers with a variety of functionalities to help solve complex programming problems. Some of them are os, sys, datetime, re, math, random, json, yaml, etc.

DevOps engineers should know which library needs to be used for a particular action. Because as a DevOps Engineer, you should be able to parse files, be it txt, json, yaml, etc.

# **2\. JSON File**

JSON stands for “JavaScript Object Notation”, but it’s not limited to just JavaScript and can be used in many programming languages. A JSON file is a file format used for storing and exchanging data.

JSON files are composed of key-value pairs, where the keys are strings and the values can be strings, numbers, arrays, objects, booleans, or null.

*Usage:* JSON is often used to transfer data between web applications and servers as it is lightweight, easy to read and write, and can be parsed by most programming languages.

*Extension:* .json

*Example of a JSON file:*

```bash
{
  "name": "XYZ",
  "age": 100,
  "email": "abcde@gmail.com",
}
```

# **3\. YAML File**

YAML stands for “YAML Ain’t Markup Language” which uses indentation to represent data hierarchies and is designed to be easy to read and write by humans.

Like JSON, YAML is a key-value-based format, but it has a more relaxed syntax and can handle more complex data structures, including lists and nested objects.

*Usage:* YAML file is used for configuration files and data exchange between different programming languages.

*Extension:* .yaml or .yml

*Example of a YAML File:*

```bash
name: XYZ
age: 100
email: abcde@gmail.com
```

### **JSON in Python**

In Python, JSON data is represented as String. We use the JSON module for this.

Below two methods is used to convert Python to JSON-

i) dumps(): Converts Python file to JSON format without creating file

ii) dump(): Converts Python file to JSON format by creating a file

Below two methods are used to convert JSON to Python-

i) loads(): Convert JSON to Python without reading from file

ii) load(): Convert JSON to Python by reading from file. `json.load()` takes a file object and returns the JSON object.

# **4\. Tasks**

1. ### **Create a Dictionary in Python and write it to a json File.**
    

In the following code, we have imported json module using `import json` and created a dictionary named `data`. After that, we specified the file path where the converted data needs to be stored. We have used 'w' keyword to write in a file and the dump() function to convert JSON file to Python. Once the script is executed you'll find a file named `data.json` in the same directory as your Python script, containing the JSON representation of the dictionary.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692532878798/0b598c04-df93-400f-9cc9-95fcd89644e2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692532913538/386f5a3c-0fb7-4f9b-8969-131d2050d7c7.png align="center")

### **Read a JSON file** `services.json` kept in this folder and print the service names of every cloud service provider.

```bash
output

aws : ec2
azure : VM
gcp : compute engine
```

services.json file:

```bash
{
    "services": {
      "debug": "on",
      "aws": {
        "name": "EC2",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      },
      "azure": {
        "name": "VM",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      },
      "gcp": {
        "name": "Compute Engine",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      }
    }
  }
```

Code to read the JSON file and execute it to get the service names of every cloud service provider:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692533021448/9b3f2f0b-089d-4b38-a6fc-e6cd82a5715e.png align="center")

### **Read YAML file using Python, file** `services.yaml` and read the contents to convert yaml to json.

services.yaml :

```bash
---
services:
  debug: 'on'
  aws:
    name: EC2
    type: pay per hour
    instances: 500
    count: 500
  azure:
    name: VM
    type: pay per hour
    instances: 500
    count: 500
  gcp:
    name: Compute Engine
    type: pay per hour
    instances: 500
    count: 500
```

Code to read the yaml file and convert the yaml file data to JSON file:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692533083499/6b4ea1a3-c175-4b1c-8a82-96a6a2516589.png align="center")

In this code, the [`yaml.safe`](http://yaml.safe)`_load()` function is used to parse the YAML file into a Python dictionary. Then, the `json.dumps()` function is used to convert the dictionary to JSON format with proper indentation.

After running the code, you'll get the JSON representation of the YAML data printed in the console.