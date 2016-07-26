CS 112 - Introduction to CS II (using Java)
===========================================

### Welcome to your second-semester computer science class!

The goal of this class is to introduce you to intermediate-level computer science concepts. You will be doing a lot of programming using the Java programming language, but please do not think of this as a Java class. The concepts and problem solving techniques you will learn in this course can be applied using any programming language. Once you understand how to solve problems using programming you should easily be able to pick up another language, like javascript, ruby, rust, or go.

## Java

The Java programming language is an object-oriented language designed to be *portable*.  Unlike languages like C, Java programs follow a "write once, run anywhere" model.  You write the program one time, compile it to byte code, and run it on any computer that has a Java Virtual Machine (JVM) available.

## Writing and Compiling Java

Writing and running a Java program involves three steps:

1. The programmer writes code and stores that code in files ending with the extension ```.java```. 
 - Open an editor of your choice and write your code. You may use any editor ([Sublime](https://www.sublimetext.com/) is recommended) to write Java code, however a *class* named ```X``` must be stored in a file named ```X.java```. 
2. The Java code is compiled into Java byte code.  The byte code for the code stored in file ```X.java``` is stored in file ```X.class```.
  - From the command line, navigate to the directory where your Java file is stored and type ```javac Classname.java```.
  - If there are errors in your program, the compiler will tell you.  If there are no errors, a ```.class``` file will be created.
3. The Java Virtual Machine (JVM) is launched.  The JVM reads and interprets the byte code stored in the specified class files.  The result is a running program.
  - From the command line, navigate to the directory where your Java file is stored and type ```java Classname```.
  - Note that you do not include an extension after the class name.

Many programmers use Integrated Development Environments (IDEs), like [Eclipse](https://eclipse.org/), to write code. IDEs make some things easier, but hide details that are important to understand. For now, you will not use an IDE to develop your Java code.


