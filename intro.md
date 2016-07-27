CS 112 - Introduction to CS II (using Java)
===========================================

### Welcome to your second-semester computer science class!

The goal of this class is to introduce you to intermediate-level computer science concepts. You will be doing a lot of programming using the Java programming language, but please do not think of this as a Java class. The concepts and problem solving techniques you will learn in this course can be applied using any programming language. Once you understand how to solve problems using programming you should easily be able to pick up another language, like javascript, ruby, rust, or go.

## Java

The Java programming language is an object-oriented language designed to be *portable*.  Unlike languages like C, Java programs follow a "write once, run anywhere" model.  You write the program one time, compile it to byte code, and run it on any computer that has a Java Virtual Machine (JVM) available.

## Writing and Compiling Java

Writing and running a Java program involves three steps:

1. **Write** - The programmer writes code and stores that code in files ending with the extension ```.java```. 
 - Open an editor of your choice and write your code. You may use any editor ([Sublime](https://www.sublimetext.com/) is recommended) to write Java code, however a *class* named ```X``` must be stored in a file named ```X.java```. 
2. **Compile** - The Java code is compiled into Java byte code.  The byte code for the code stored in file ```X.java``` is stored in file ```X.class```.
  - From the command line, navigate to the directory where your Java file is stored and type ```javac Classname.java```.
  - If there are errors in your program, the compiler will tell you.  If there are no errors, a ```.class``` file will be created.
3. **Run** - The Java Virtual Machine (JVM) is launched.  The JVM reads and interprets the byte code stored in the specified class files.  The result is a running program.
  - From the command line, navigate to the directory where your Java file is stored and type ```java Classname```.
  - Note that you do not include an extension after the class name.

Many programmers use Integrated Development Environments (IDEs), like [Eclipse](https://eclipse.org/), to write code. IDEs make some things easier, but hide details that are important to understand. For now, you will not use an IDE to develop your Java code.


## Syntax Highlights

- **Classes** - A Java program consists of one or more classes. A class named ```X``` must be stored in a file named ```X.java```.
- **Comments** - There are two ways to comment your code in Java. The first option is to use ```//```. In this case, the comment begins with the ```//``` and continues until the end of the line.

```java
//declare a variable a
int a; 
a = 4; //initialize a to the value four
```
The second option is to use ```/*``` and ```*/```. These symbols allow for multi-line comments. 

```java
/*
 * declare a variable a and
 * initialize it to four
 */
int a = 4;
```

- **Statements** - All Java statements end with a semi-colon ```;```.
- **Curly Braces** - Code blocks are surrounded by curly braces ```{}```. This applies to if statements, loops, classes, and methods.

```java
class X {
    //class definition
}

if (condition) {
    //body of if
}

while (condition) {
    //body of while
}

void method() {
    //body of method
}
```

- **Whitespace** - White space is irrelevant in Java. Though you should make sure your code is properly indented (in order to get a good grade!) the compiler does not care.
- **Keywords** - Java keywords include ```class return break continue try catch public private package import```. See the [Java Tutorials - Java Language Keywords](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/_keywords.html) page for a full list.