Command Line Input/Output
=========================

## Output

There are several common ways to print to the standard output stream in Java.

```java
System.out.println("text to print");
```

This code invokes the `println` method of the object `out` that is a static data member of the class `System`. The object `out` is of type `java.io.PrintStream`.  `PrintStream` provides both a `println` method and a `print` method.  Both methods can take as input strings (as shown above) or ints, chars, doubles, floats, longs, and booleans.  The `print` method prints the data and does not advance to the next line.  The `println` method prints the data given and then prints a newline.  

```java
/*
The output of the following code is:

Hello there, Bob
Good to see you!

*/
String name = "Bob";
System.out.print("Hello ");
System.out.println("there, " + name);
System.out.println("Good to see you!");
```

The code above demonstrates the difference between `print` and `println`.  It also demonstrates **string concatenation**.  Two strings can be concatenated using the `+` operator.

## Input

Command line input in Java is a bit tricky.  The easiest way to achieve this is by using the `Scanner` class.  An example follows:

```java
import java.util.Scanner;

public class IOExamples {

	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		System.out.println("Enter some text: ");
		String str1 = scan.nextLine();
		System.out.println("Enter some more text: ");
		String str2 = scan.nextLine();	
		System.out.println("You said: " 
							+ str1 + " and "
							+ str2);
		scan.close(); //close the stream when we are doing using it
	}

}

```

- The `Scanner` constructor takes as input an `InputStream`.  To get input from the command line, pass it the `in` object that is a static data member of the `System` class.
- The `nextLine` method of `Scanner` takes no input and returns the next line of text, ending with a newline.
- Once you have created a `Scanner` object, you can use it repeatedly to get input.
- At the top of the class that includes these lines of code, you must import the `Scanner` class.  This means that you explicitly tell the compiler that you will be using this class you can do this as follows:
`import java.util.Scanner;`

The `Scanner` also provides methods `nextInt`, `nextDouble`, and so on.  You can use these methods to retrieve data of a particular type as in the example below:

```java
Scanner scan = new Scanner(System.in);
System.out.println("Enter a number: ");
int x = scan.nextInt();
System.out.println("Enter another number: ");
int y = scan.nextInt();
```

It becomes a bit tricky, however, to retrieve different types of data.

```java
Scanner scan = new Scanner(System.in);
System.out.println("Enter a number: ");
int x = scan.nextInt();
System.out.println("Enter some text: ");
String s = scan.nextLine();
```

In the example above, the scanner will retrieve the number entered by the user, but will leave a newline character in the buffer.  When the scanner retrieves the next line of text, it thinks that there is already a line in the buffer, and will not wait for the user to enter new data.  

You must also be careful in the case that the user enters a `String` if the `Scanner` expects a number or other type. In this situation, you might end up with an `InputMismatchException`. One way to address these problems is to consistently read in data as strings and convert the strings to numbers or other types as appropriate.