Variables
=========

## Strong Typing

> The Java programming language is a strongly typed language, which means that every variable and every expression has a type that is known at compile time.

Java Language Specification, Third Edition


Each variable is given a type when it is declared.  A variable may not be assigned a value that is not of the type specified.  Types are checked at compile time and errors (as shown below) are reported.

```java
BasicSyntax.java:14: error: incompatible types: String cannot be converted to int
		int a = "Hello";
		        ^
1 error
```

## Declaring and Initializing

```java
public class Hello {

    public static void main(String[] args) {
        //Line 1               
        String msg;
        
        //Line 2
        msg = "Hello, world!";

        //Line 3
        System.out.println(msg);
    }
}
```

Line 1 of the main method above **declares** a variable of type ```String``` named ```msg```.  This gives you a memory cell that can hold something of type ```String``` and you may refer to this memory cell using the label ```msg```.  To declare a variable in Java, you must specify its type followed by its name.  

The rules for naming variables are as follows:

- Names consist of letters, digits, the underscore (_), and the dollar sign ($)
- Names are case sensitive
- Names must begin with a letter, the underscore, or a dollar sign and usually - begin with a lower-case letter
- Typically, names do not use the dollar sign

Line 2 of the main method above assigns the value "Hello, world!" to the variable ```msg```. An assignment statement consists of a variable name, followed by the assignment operator (=), followed by the value.  You read this line of code as "msg 'gets the value of' Hello, world!".  You should never say "msg equals Hello, world!".  We'll see why later.

You can also declare a variable and assign it a value in a single line of code as follows:

```java
String msg = "Hello, world!";
```
## Primitive Types and Reference Types

In Java, there are eight **primitive** types as shown below:

| Type | Size | Min Value | Max Value |
| ---- | -----| ----- | ----- |
| byte	 | 8 bits | -128 | 127 |
| short | 16 bits | -32,768 | 32,767 |
| int	| 32 bits | -2,147,483,648 | 2,147,483,647 |
| long	| 64 bits | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |
| float|	 32 bits | Approximately -3.4E+38 with 7 significant digits | Approximately 3.4E+38 with 7 significant digits |
| double| 64 bits | Approximately -1.7E+308 with 15 significant digits | Approximately 1.7E+308 with 15 significant digits |
| char	| 16 bits | [Unicode character set](http://unicode.org/charts/) | 
| boolean |	 undefined	| true or false| 

A primitive type variable that is not initialized is typically given a value of 0, but it is bad programming style to rely upon that.  Your program should always initialize variables appropriately.  The example below declares a variable of type ```int``` named ```number``` and initializes it to the value 4.

```java
int number; //Line 1
number = 4; //Line 2
```

**Reference** types are pointers to objects.  In the example above, line 1 declares a variable of type ```Hello``` and names it ```h```.  ```h``` is the label of 32-bits of memory that initially contains the value **```null```**.  ```null``` is the special value used to indicate that a reference contains no value.

Line 2 of the example initializes the variable ```h``` by creating a new instance of the ```Hello``` class and setting the value stored in ```h``` to be the memory address of the new object.  To create a new object you must use the **```new```** keyword.  This calls the constructor of the class.  A new object is created on the heap, and the location of the new object is stored in the variable ```h```.

The ```String``` type is treated in a special way in Java.  It is not a primitive type, but you can create a String object without using the new keyword.  In addition, String objects are **immutable**, which means they cannot be changed.  

```java
//Line 1
String name = "Michael Mouse";
        
//Line 2
name = "Mickey Mouse";
```

In line 1 of the example, an object with contents "Michael Mouse" is created and the address of that object is stored in the reference labeled ```name```.  In line 2, a new object with contents "Mickey Mouse" is created and the address of that object is stored in ```name```.  Note that the address of the object containing "Michael Mouse" is overwritten.  If there are no other references to the "Michael Mouse" object, it will eventually be reclaimed by the **garbage collector**.  The garbage collector periodically looks at all of the memory that your program has requested to use and reclaims all of the memory that your program is no longer using.