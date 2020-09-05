---
layout: post
title: "Basic Bash Scripting Tutorials For Beginners"
categories: [linux, programming]
image: basic-important-bash-scripting-tutorials/1.png
tags:
- Linux
- Ubuntu
- CentOS
- Unix
- Bash-Scripting
- Shell-Scripting
- Tutorials
- Basic-Advance
- Programming
- Beginners-Guide
description: "Learn basic to advance bash shell scripting language in Linux/Unix. This article provides tutorials to the beginners who are new to the bash shell command."
---

![Basic Bash Scripting Tutorials For Beginners | sTechalon.com](/static/img/posts/basic-important-bash-scripting-tutorials/1.png)<br><br>
<span style="color:#bb1919">*Bash Scripting*</span> is a simple plain text that contains a [series of commands](https://stechalon.com/linux-bash-shell-command-types){:target="_blank"}. The commands used in bash scripting are the same commands that we use in linux shells (**eg:** **cp**, **mv**, **mkdir** etc). This series of commands request the computer to do the required operation.

# Creating Bash Script File
Bash script uses **.sh** extension in the filename. For example, **myFirstScript.sh** will be a file for scripting. For <span style="color:#bb1919">*creating*</span> such a file you can use your favourite text editor in linux such as vim, nano, gedit etc. In below example I am using [vim text editor](https://stechalon.com/vim-editor-tutorial-linux-command-example){:target="_blank"}.
{%highlight runy%}

vi myFirstScript.sh 

{%endhighlight%}
You do not need to add additional code for writing bash script. Any command you use to run in the linux shell the same command will be run through scripting. 

# Executing Bash Script File
After creating the script file, it is very simple to  <span style="color:#bb1919">*run or execute*</span>. To execute the script file, first you need to provide the <span style="color:#bb1919">*execute permission*</span> to the file. For that use the syntax shown below:

**Providing Execute Permission**

{%highlight runy%}

chmod +x myFirstScript.sh 

#OR

chmod 755 myFirstScript.sh

{%endhighlight%}

After providing execute permission, now you are ready to execute the script file. For that use the syntax shown below:

**Executing Script File**
{%highlight runy%}
./ myFirstScript.sh

#OR

bash myFirstScript.sh
{%endhighlight%}
Now you know how to create and execute the script file. Let's learn the most common operation of bash scripting with simple examples.

**Content:**

[**1. Printing Hello World**](#pinting-hello-world-in-bash-script)<br>
[**2. Series Of Command**](#writing-series-of-command-in-bash-script)<br>
[**3. Commenting**](#types-of-comment-in-bash-script)<br>
[**4. Variables**](#variables-in-bash-script)<br>
[**5. Conditional Statement**](#conditional-statement-in-bash-script)<br>
[**6. Loops**](#using-loops-in-bash-script)<br>
[**7. Function**](#using-function-in-bash-script)<br>


# Pinting Hello World In Bash Script
Let us create our first program that prints Hello World. We will do this by two methods.

First  directly input command in linux shell.

{%highlight ruby%}

[alon@stechalon]$ echo "Hello World"

Hello World

{%endhighlight%}


The **output** of the above command is <span style="color:#bb1919">*Hello World*</span>.

Now let us print the same output using the same command through script programming.

Create script file name **firstScript.sh**
{%highlight ruby%}
[alon@stechalon]$ vi firstScript.sh

{%endhighlight%}

Add the following command and save using <span style="color:#bb1919">*':wq'*</span> command.
{%highlight ruby%}
#!/bin/bash
echo "Hello World"
{%endhighlight%}

Provide execute permission to the firstScript.sh file.

{%highlight ruby%}
chmod +x firstScript.sh
{%endhighlight%}

Execute the firstScript.sh file.

{%highlight ruby%}
./firstScript.sh
{%endhighlight%}

**Output:**

<span style="color:#bb1919">*Hello World*</span>

# Writing Series Of Command In Bash Script

In a series of commands, we will input multiple commands in a scripting file. For that create new scripting file and include the following command given below:

{%highlight ruby%}
#!/bin/bash

sudo cd /home/ && mkdir bash-files
{%endhighlight%}    

The above command tells the computer to change directory to  <span style="color:#bb1919">*'/home/'*</span> and make the directory name <span style="color:#bb1919">*'bash-files'*</span>. You should have root access to run this command if you are not allowed to do this action.

**Output:**

{%highlight ruby%}
[alon@stechalon]$ ls /home/

bash-files
{%endhighlight%}


# Types Of Comment In Bash Script

Comments while programming is the most essential way to debug the code and provide information to other users who are reading the same code. There are different ways to comment in a bash scripting file. You can comment a single line by using **#** and multiple line by using **: '** or **<<commnet-name comment-name**.

**Example**

{%highlight ruby%}
#!/bin/bash
#This is a single line comment1.
#This is a single line comment2.
#This is a single line comment3.

echo "Hello World1"

: '
This is 
Multiple Line
Comment1.
'
echo "Hello World2"

<<comment
    This is
    Multiple Line
    Comment2.
comment

echo "Hello World3"
{%endhighlight%}

**Output:**

{%highlight ruby%}
Hello World1
Hello World2
Hello World3
{%endhighlight%}

# Variables In Bash Script

Declaring variables in bash scripting is very easy. It can be done by directly assigning value to the variable. **$** symbol is used with the variable name for reading the values of the variables.

**Example**
{%highlight ruby%}
#!/bin/bash
#Printing Sting 

str="This Is String Type"
echo $str

#Airthmetic Operation

a=5
b=5
c=$(( $a + $b ))
echo $c
{%endhighlight%}

**Output**
{%highlight ruby%}
This Is String Type
10
{%endhighlight%}

# Conditional Statement In Bash Script

Like other programming languages, bash scripting also supports conditional statements. <span style="color:#bb1919">*if-then, else*</span> and <span style="color:#bb1919">*case(switch)*</span> are the conditional statements used in bash. Conditional statement starts with **if** and ends with **fi** in **if-else** statement and in **switch-case** statement starts with **case** and ends with **esac**.

**Example For If-then, else Statement**

{%highlight ruby%}
#!/bin/bash

echo "Enter your 1st number"
read fst
echo "Enter your 2nd number"
read snd

if [[ $fst -gt  $snd ]]
then
echo "1st Number Is Greater Than 2nd Number"
else
echo "2nd Number Is Greater Than 1st Number"
fi
{%endhighlight%}

**Output:**
{%highlight ruby%}
Enter your 1st number
5
Enter your 2nd number
10
2nd Number Is Greater Than 1st Number
{%endhighlight%}

{% include tip.html content= "'-gt' is know as greater than, '-le' is known as less than or equal to, '-lt' is used for comparison, '-eq' is known as equal to, '-ne' is known as not equal to" %}

**Example For Case Statement**

{%highlight ruby%}
echo "Enter the number of the day 1-7"
read day
case $day in
1)
echo "Sunday"
;;
2)
echo "Monday"
;;
3)
echo "Tuesday"
;;
4)
echo "Wednesday"
;;
5)
echo "Thursday"
;;
6)
echo "Friday"
;;
7)
echo "Saturday"
;;
*)
echo "No matching information found"
;;
esac
{%endhighlight%}

**Output**

{%highlight ruby%}
Enter the number of the day 1-7
2
Monday
{%endhighlight%}

# Using Loops In Bash Script

When you need to run or execute some task multiple times then loop is used. There are different types of loops in bash scripts. They are for loop, while loop and until loop.

## For Loop
The for loop is different from other programming languages. It let's you iterate over a series of 'words' within a string.

**Example**
{%highlight ruby%}
#!/bin/sh
for i in 1 2 3 4 5
do
  echo "$i"
done
{%endhighlight%}


**Output**
{%highlight ruby%}
1
2
3
4
5
{%endhighlight%}


## While Loop
The while loop executes a piece of code if the control expression is true, and only stops when it is false or a explicit break is found within the executed code.

**Example**
{%highlight ruby%}
#!/bin/bash 
         COUNT=0 #Initial count value 0
         while [  $COUNT -lt 5 ]; do #Condition if $COUNT is less than 5
             echo The counter is $COUNT
             let COUNT=COUNT+1 # COUNT is incremented by 1 
         done

{%endhighlight%}
 

**Output**

{%highlight ruby%}
The counter is 0
The counter is 1
The counter is 2
The counter is 3
The counter is 4
{%endhighlight%}


## Until Loop

The until loop is similar to the while loop, instead of executing while a condition is true you are assuming the condition is false and executing until it becomes true. 
{%highlight ruby%}

#!/bin/bash 
         COUNT=0 #Initial count value 0
         until [  $COUNT -gt 5 ]; do #Condition if $COUNT is greater than 5
             echo The counter is $COUNT
             let COUNT=COUNT+1 # COUNT is incremented by 1 
         done
{%endhighlight%}


**Output**
{%highlight ruby%}
The counter is 0
The counter is 1
The counter is 2
The counter is 3
The counter is 4
The counter is 5

{%endhighlight%}

# Using Function In Bash Script
Implementing functions is the best way to reuse the same code for different operations. It is very easy to use functions in bash script. Functions are denoted as  <span style="color:#bb1919">*'function_name()'*</span>.

**Example Of Function**
{%highlight ruby%}
function_print () { #Initializing Funtion
echo Hello I am a function
}

function_print  #Calling function
function_print #Calling function again
{%endhighlight%}


**Output**
{%highlight ruby%}
Hello I am a function
Hello I am a function
{%endhighlight%}


**Example Of Function With Passing Arguments**
{%highlight ruby%}
function_print () {
echo $1
}

function_print Sunday  #Passing argument to function
function_print Monday  #Passing different argument to function again
{%endhighlight%}


**Output**
{%highlight ruby%}
Sunday
Monday
{%endhighlight%}

{% include summaryCallout.html heading= "Summary" content= "Hope you learn the basic operation in bash scripting. If you have any issue please let me know through comment secetion below." %}