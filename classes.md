Classes
=======

## Overview

Every Java program is comprised of one or more **classes**.

```java
public class Name {
    private String first;
    private String last;

    public Name(String first, String last) {
        this.first = first;
        this.last = last;
    }

    public String getFirst() {
        return this.first;
    }

    public String getLast() {
        return this.last;
    }

    public void setFirst(String first) {
        this.first = first;
    }

    public void setLast(String last) {
        this.last = last;
    }
    public String toString() {
        return this.first + " " + this.last;
    }

}
```

A class is a collection of **data members** and **methods**.  It is a template or blue print for the behaviors that an instance of the class can execute.  An instance of a class is called an **object**. An object is created by invoking the class **constructor**.  An executing Java program is comprised of many objects interacting to provide the specified functionality.

An object's **data members** are variables that store the data associated with that object.   In the example above, an instance of the ```Name``` class will contain two variables: ```first``` and ```last```.  

An object's methods define its behaviors, or the functions it can perform.  Often, methods provide the ability to access and modify the data members of the object.  In the example above, the ```getFirst```, ```setFirst```, ```getLast```, and ```setLast``` methods provide the ability to view or change the first and last data members.  

In some cases, methods may operate only on the input given, and not access data members.  An example of that is shown below:

```java
public class Adder {
    
    public int add(int num1, int num2) {
        return (num1 + num2);
    }

}
```

In this example, the ```add``` method takes two pieces of input, ```num1``` and ```num2```, adds them together, and returns the result.

## Syntax and Logistics

A class name describes the functionality it supports.  For example, the ```Name``` class defines the template of an object that will store a person's name.  A class with name ```Foo``` must be stored in a file named ```Foo.java```.  Conventionally, class names begin with an upper-case letter.

## Instantiation

To create an instance of a class you invoke its constructor.  A constructor is similar to a method, but it must have the same name as the class and it does not indicate the type of output it returns.  The constructor is called by using the ```new``` keyword.  An example follows:

```java
Name n = new Name("Mickey", "Mouse");
```

## HelloWorld Three Ways

```java
public class Hello {

    public static void main(String[] args) {
        System.out.println("Hello, world!");
    }

}
```

This first example program demonstrates a class Hello that contains a single method.  The method in the ```Hello``` class is a special method, ```main```.  Every standalone Java application has a main method that tells the Java Runtime Environment where to start.  When the program is run, the JRE starts by executing the first line of the main method.  In this case, that line prints "Hello, world!".  

```java
public class Hello {
    private String msg; 

    public Hello(String msg) {
         this.msg = msg;
    }

    public void displayMsg() {
        System.out.println(msg);
    }
}

public class HelloDriver {

    public static void main(String[] args) {
        Hello h = new Hello("Hello, world!");
        h.displayMsg();
    }

}
```

The second example program demonstrates a class ```Hello``` that contains a data member that holds the message we wish to print.  The class ```HelloDriver``` contains our main method.  When the program begins, the driver program creates a new object of type ```Hello``` and asks the object to print its message.  This is a more object-oriented design.

It is common to use a ```Driver``` class that contains the entry point for your program.  The driver creates the objects and invokes the appropriate methods.  In some cases, however, you may wish to include your main method in a class it will instantiate.  This is common for testing purposes.  An example of this follows:

```java
public class Hello {
    private String msg;

    public Hello(String msg) {
        this.msg = msg;
    }

    public void displayMsg() {
        System.out.println(msg);
    }

    public static void main(String[] args) {
        Hello h = new Hello("Hello, world!");
        h.displayMsg();
    }

}
```