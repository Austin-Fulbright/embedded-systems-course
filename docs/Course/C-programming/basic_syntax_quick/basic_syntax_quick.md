# Introduction to C and Basic Syntax



### History of C

The C programming language was developed in the 1970s and during this time there was not a consensus on what high level language was going to be best for writing operating systems. Most operating systems were written in the Assembly language. The Assembly language is a set of instructions you write that will compile into machine code instructions for the cpu. So each time you write a line of Assembly that will represent machine code. To give you some context the windows operating system has **50 million lines** of code. The windows operating system is not written in Assembly, there are probably some files that are written in Assembly but it is written mainly in the C language. If you had to write the windows operating system completely in Assembly it would probably end up being like 5 billion lines of code.

So the programmers in the 70s knew that they wanted to create a language that could effectively write operating systems and allow them to write it within the age of one persons life. There were some predecessors to C. There was fortran and B. B is was an attempt to write what C would eventually become. In 1972 the new B was released by the GOAT Dennis Ritchie and eventually named it C. The missing ingredient of C was a compiler which basically takes code and turns it into a binary that the computer can execute. ![[Pasted image 20240915105701.png]]
And the C programming language was born!


### Why you should use C

When I was in college I took many programming classes, Introduction to Computer Science, Theory of Computing, Introduction to Software Development, Web Development, Software Engineering, I even took Systems Engineering which had us program in C. However, there is this feeling that you get and I am sure that others have felt this as well. "How does this even work" what I mean to say is. How does this 

```
for(int i = 0; i < 10; i ++){
printf("this \\n")
}
```
turn into this

```
this
this
this
this
this
this
this
this
this
this
```

and further more how the fuck does the command "npm install" work. There is so much prerequisite knowledge you are missing to understand how these commercial development tools actually work. And it is way easier to understand these things if you learn how to build them from the ground up. 

Now you might say, "I only have so much time in my life, I am never going to build an operating system or a usb driver, I am not going to make money learning all the capablities of the C language", That is a good point. If you want to get a job in tech, you can just take a Angular.js course that will take about 6 months and you will know everything you need to know to make 70k a year building beautiful websites. If you are just looking to make money from software this course is not for you. If you are worried that Chatgpt-4o1 could take your job. This course is not for you. This course is for people who are passionate about programming. People who program for the sake of programming and want to contribute to the overall software engineering knowledge base. I am not getting my masters and phd because I want to make more money. I am doing it because I love programming. This course is an open source project and I hope others will help me contribute to an amazing knowledge base.


So why should you learn C. You should learn C because it is the language that wrote the language that was used to build your development tools. It is the language that wrote your operating system. It is the language that you need to know to talk to hardware. It is the language that wrote the most popular language in the world right now, Python. So for people who don't care about efficiency and time, and people who are a lot more about understanding and improving as developers, C is the best language. We will dip into other languages like C++ and Python occasionally since there are some great tools used in Python. However, we wont use any tools unless we 100% know how they work first. So that is why we will use C.


### C programming syntax and fundamentals 

The C language uses 4 basic primitive types:
`char`, `int`,`float`, and `double`.

C has added a lot more complex types since its release but the only other important type you should know about is the Boolean type which can be added through the <stdbool.h> header. and use as `bool`.

Lets break down some C syntax real quick

```
#include <stdio.h>  
  
int main() {  
  printf("Hello World!");  
  return 0;  
}
```

The top line #include <studio.h> is the header file that it is including stdio.h is a standard library for C and contains most of the common input/output functionality in C.

The main function has a return type of int and takes no parameters. Inside the function there is a print statement. The C language uses `printf` in order to print to standard output.

The main function returns 0. if you read the C documentation you will see that every main function has a return value which represents that type of exit that was produced.

Hopefully this is all review the next chapters will go into more advanced concepts in the C language.


---


&Sources
1. https://www.youtube.com/watch?v=de2Hsvxaf8M&ab_channel=Computerphile
2. https://softkeys.uk/blogs/blog/how-many-lines-of-code-in-windows-10
3. https://en.wikipedia.org/wiki/C_(programming_language)
4. https://www.linkedin.com/pulse/why-you-should-learn-c-your-first-language-saroj-kumar-sharma/
