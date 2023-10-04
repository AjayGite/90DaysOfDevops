---
title: "Basics of Python"
datePublished: Thu Aug 17 2023 10:52:42 GMT+0000 (Coordinated Universal Time)
cuid: cllf1lqy9000r09kzc60jdltq
slug: basics-of-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692175121770/58280067-d7e0-470e-ac58-3001f8f84a34.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692269528648/95efbcb8-9dab-463a-be49-020fee0e8671.png
tags: python, trainwithshubham, 90daysofdevopschallenge

---

## **What is Python?**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691936665880/05ee001b-1723-48de-b54d-800ada0311c5.png?auto=compress,format&format=webp align="left")

🐍Python is a high-level, general-purpose programming language with an elegant syntax that allows programmers to focus more on problem-solving than on syntax errors. One of the primary goals of Python Developers is to keep it fun to use. Python has become a big buzz in the field of modern software development, infrastructure management, and especially in [**Data Science**](https://intellipaat.com/blog/what-is-data-science/)🔭 and [**Artificial Intelligence**](https://intellipaat.com/blog/what-is-artificial-intelligence/)🔬. Most recently, Python has risen to the top 3 list of the TIOBE index of language popularity.

Python is becoming increasingly everywhere, but you must be wondering why Python has become such a hot topic in the developers’ world. In this tutorial, you will understand all the reasons behind Python’s popularity.

🏃‍♂️Let's Understand In Short Way:-

* Python is an Open source, general purpose, high-level, and object-oriented programming language.
    
* It was created by **Guido van Rossum**
    
* Python consists of vast libraries and various frameworks like Django, Tensorflow, Flask, Pandas, Keras etc.
    

### **How to Install Python?**

Here are the few steps, which are required for the installation of Python: -

1. **Visit the Official Website:** Go to the official Python website at [**python.org/downloads**](http://python.org/downloads) **in your web browser.**
    
2. **Choose a Version:** Python has multiple versions available, but it's recommended to choose the latest version from the Python 3. x series (e.g., Python 3.9). Python 3. x is the current and actively maintained version.
    
3. **Download the Installer:** On the Python website, click on the "Downloads" tab. You'll see various download options for different platforms (Windows, macOS, Linux). Choose the installer that matches your operating system.
    
4. **Run the Installer:**
    
    * **Windows:** Double-click the downloaded installer executable (usually named something like `python-3.9.6.exe`). Check the box that says "Add Python 3.9 to PATH" during the installation process. This will make it easier to run Python from the command line.
        
    * **macOS:** Double-click the downloaded installer package (usually named something like `python-3.9.6-macosx10.9.pkg`). Follow the on-screen instructions to complete the installation.
        
    * **Linux:** Python is often pre-installed on Linux systems. To check if Python is already installed, open a terminal and type `python3 --version`. If it's not installed, you can use your package manager to install it.
        

### **Task 1*: -* Install Python in your respective OS, and check the version**

To install Python on Linux, use the below command. Once the python is installed, check the version.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692179030617/dbbf5189-bd5d-40ac-a589-d9ec891a8ca8.png align="center")

### **Task 2*: -* Data Types In Python**

The different Data Types in Python are as follows: -

### **Data Types Table:**

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Data Types</strong></p></td><td colspan="1" rowspan="1"><p><strong>Classes</strong></p></td><td colspan="1" rowspan="1"><p><strong>Description</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>Numeric</p></td><td colspan="1" rowspan="1"><p>int, float, complex</p></td><td colspan="1" rowspan="1"><p>holds numeric values</p></td></tr><tr><td colspan="1" rowspan="1"><p>String</p></td><td colspan="1" rowspan="1"><p>str</p></td><td colspan="1" rowspan="1"><p>holds sequence of characters</p></td></tr><tr><td colspan="1" rowspan="1"><p>Sequence</p></td><td colspan="1" rowspan="1"><p>list, tuple, range</p></td><td colspan="1" rowspan="1"><p>holds collection of items</p></td></tr><tr><td colspan="1" rowspan="1"><p>Mapping</p></td><td colspan="1" rowspan="1"><p>dict</p></td><td colspan="1" rowspan="1"><p>holds data in key-value pair form</p></td></tr><tr><td colspan="1" rowspan="1"><p>Boolean</p></td><td colspan="1" rowspan="1"><p>bool</p></td><td colspan="1" rowspan="1"><p>holds either <code>True</code> or <code>False</code></p></td></tr><tr><td colspan="1" rowspan="1"><p>Set</p></td><td colspan="1" rowspan="1"><p>set, frozeenset</p></td><td colspan="1" rowspan="1"><p>hold collection of unique items</p></td></tr></tbody></table>

## **Python Numeric Data type:**

In Python, numeric data type is used to hold numeric values.

Integers, floating-point numbers and complex numbers fall under python numbers category. They are defined as `int`, `float` and `complex` classes in Python.

* `int` - holds signed integers of non-limited length.
    
* `float` - holds floating decimal points and it's accurate up to **15** decimal places.
    
* `complex` - holds complex numbers.
    

We can use the `type()` function to know which class a variable or a value belongs to.

Let's see an example,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692200097376/e0331023-4c65-403f-8255-9a8931c7f0e5.png align="center")

In the above example, we have created three variables named num1, num2 and num3 with values 21, 22**.0**, and `1+5j` respectively.

We have also used the `type()` function to know which class a certain variable belongs to.

Since,

* **21** is an integer value, `type()` returns `int` as the class of num1 i.e `<class 'int'>`
    
* **22.0** is a floating value, `type()` returns `float` as the class of num2 i.e `<class 'float'>`
    
* `1 + 5j` is a complex number, `type()` returns `complex` as the class of num3 i.e `<class 'complex'>`
    

## **Python List Data Type:**

List📝 is an ordered collection of similar or different types of items separated by commas and enclosed within brackets `[ ]`. For example, Here, we have created a list named languages with **4** strings values inside it

### **Access List Items🧏**

To access items from a list, we use the index number **(0, 1, 2 ...)**. For example,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692249002316/7af003cb-c4d0-4960-aeef-08b9b642837a.png align="center")

In the above example, we have used the index values to access items from the languages list.

* `cars[2]` - access the second item from languages i.e. `Nexon`
    
* `cars.append` - Appending the item in list
    
* `cars[4]` - access the fourth item from languages i.e. `BMW`
    

## **Python Tuple Data Type:**

Tuple is an ordered sequence of items same as a list. The only difference is that tuples are immutable. Tuples once created cannot be modified.

In Python, we use the parentheses `()` to store items of a tuple.

Here, the product is a tuple with a string value `India, Australia, England` and integer values **1, 2, 3**.

### **Access Tuple Items**

Similar to lists, we use the index number to access tuple items in Python. For example,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692255384933/4f09fb83-68b5-4993-b537-6b1513adec96.png align="center")

## **Python String Data Type:**

String is a sequence of characters represented by either single or double quotes. For example,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692255889444/0bce34c2-b64c-4325-8ce4-84da0864de6d.png align="center")

In the above example, we have created string-type variables: name and message with values `'My name is Ajay Gite'` and `'Let's learn Python'` respectively.

## **Python Set Data Type:**

Set is an unordered collection of unique items. Set is defined by values separated by commas inside braces `{ }`. For example,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692268862756/2cd4263d-b581-44af-adce-aa85e29505b5.png align="center")

Here, we have created a set named student\_info with **5** integer values 2 with same number. So, while printing it doesn't display duplicate numbers.

Since sets are unordered collections, indexing has no meaning. Hence, the slicing operator `[]` does not work.

## **Python Dictionary Data Type:**

Python dictionary is an ordered collection of items. It stores elements in key/value pairs. Here, keys are unique identifiers that are associated with each value.

Let's see an example,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692269215470/b5ef44d0-a25b-49b9-a195-9a8b57cecfbe.png align="center")

In the above example, we have created a dictionary named teams. Here,

1. **Keys** are `'Team'`, `'Captain'`, `'Vice-Captain'`
    
2. **Values** are `'India'`, `'Virat Kohli'`, `'Bumrah'`
    

### **Access Dictionary Values Using Keys🔐**

We use `keys` to retrieve the respective `value`. But not the other way around. For example,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692269384588/6c386373-873a-4184-872e-10638b3dfa4c.png align="center")

Here, we have accessed values using keys from the capital\_city dictionary. Since `'Team'` is key, `teams['Team']` accesses its respective value i.e. `India` However, `'Virat Kohli'` is the value for the `'Captain'` key, so `teams['Virat Kohli']` throws an error message.

## **Conclusion:**

Python is an important tool for organizations, as we learned in today's blog. In addition, we examined different types of data in Python, which might sound complicated but is actually quite straightforward. Learning about Python's different data types can be fun and useful for organizations. Let's continue to explore the amazing world of Python programming together in my next blog!