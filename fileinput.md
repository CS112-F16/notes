File Input, Exceptions, and Command Line Arguments
=================


There are several ways to get input from files in Java. The [Java I/O Tutorial](http://docs.oracle.com/javase/tutorial/essential/io/index.html) provides extensive information about the [java.io](https://docs.oracle.com/javase/8/docs/api/java/io/package-summary.html) package. In this document we will look at how to use the [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html) class to read text from a file. The tutorials provide more information about reading in binary data, for example image files, as well as more efficient ways to read text from a file.

To understand file input it is also important to understand how [exceptions](https://docs.oracle.com/javase/tutorial/essential/exceptions/) work in Java. 

## Search and Replace Example

This document will discuss the following example that reads a text file and prints the text found replacing all instances of a *search* term with a *replace* term. The example with complete documentation may be found here: [SearchAndReplace.java](https://github.com/CS112-F16/code/blob/master/GeneralExamples/SearchAndReplace.java).

```java
import java.io.File;
import java.io.FileNotFoundException;

import java.util.Scanner;

public class SearchAndReplace {

	public static void main(String[] args) {

		if(args.length != 3) {
			System.out.println("usage: java SearchAndReplace <infile> <searchTerm> <replaceTerm>");
			System.out.println("\texample: java SearchAndReplace in.txt hello goodbye");
			System.exit(1); //exit the program 
		}

		String inFileName = args[0];
		String search = args[1];
		String replace = args[2];

		File inputFile = new File(inFileName); 
		try (Scanner input = new Scanner(inputFile)) { 

			while(input.hasNext()) {
				String line = input.nextLine(); //read in the next line of the input
				line = line.replaceAll(search, replace); 
				System.out.println(line);
			}

		} catch(FileNotFoundException fnf) {
			System.out.println("File not found.");
			System.out.println(fnf.getMessage());
			System.exit(1);
		}

	}

}
```


## File Input using `Scanner`

Recall that the `Scanner` constructor takes as input a source from which it will read text. Passing it `System.in` will allow you to read text from the command line. To read text from a file, you must (1) create a `File` object passing it the name of the file and (2) create the `Scanner` passing it the `File`.

### Command Line Arguments

To get the name of the file from the user, the example above uses a command line argument. One way to read input from the command line is to use `System.out` to prompt the user for a value and then read the result. Another option is to pass the input to the program when the program is run.

The `args` parameter passed to the main method is a list of strings that follow the name of the class when the program is launched. Consider the following program:

```java
public class CommandLineArgs {
	public static void main(String[] args) {
		System.out.println(args[0]);
	}
}
```

If this program is executed with the command `java CommandLineArgs HELLO` then the output of the program will be `HELLO`.

`args` is an *array*, or a list of values. The first item in the list is accessed by using the `[]` and the index 0. The second item is accessed as `args[1]`, and so on.

The `SearchAndReplace` example expects three things to be passed as input at the command line. An example execution of the program follows: `java SearchAndReplace in.txt fish dog`

The first thing that happens in `SearchAndReplace` is that the program verifies that the *length* of the `args` parameter is exactly 3. If the length is not three then the program prints a message indicating how it is expected to be used and exits with an error code of 1.

For convenience, the next thing that happens in the program is that the values passed in are saved in local variables with convenient names. The following code takes the value in the first position of the list and saves it in a local variable named `inFileName`.

```java
String inFileName = args[0];
```

### Creating a `File`

To create a `Scanner` to read from a file we need to pass it an object of type `File`. To create an object of type `File` we need to pass it a `String` that indicates the name of the file. The following two lines do just that:

```java
String inFileName = args[0];

File inputFile = new File(inFileName); 
```

### Exceptions

Once the `File` object exists, we can now create the `Scanner` that will allow us to read from the file. When performing an action such as opening a file it is possible that something could go wrong, for example the user could have provided an invalid file name. Java indicates these issues using *exceptions*. 

There are two types of exceptions: checked and unchecked. There are also two ways to handle exceptions: `try-catch` and propagation. This example uses a `try-catch` statement to handle a checked exception.

The statement below uses a `try` block and, in `()` attempts to create the `Scanner`. If Java is unable to create the `Scanner` because the file is not found the code inside of the `try` block, denoted by the `//...` will not be executed. Instead, the code inside of the `catch` block will execute. 

If the file is found and no `FileNotFoundException` is generated then the code in the `try` block will execute and the code in the `catch` block will not execute.

```java
try (Scanner input = new Scanner(inputFile)) { 
	
	//...

} catch(FileNotFoundException fnf) {
	System.out.println("File not found.");
	System.out.println(fnf.getMessage());
	System.exit(1);
}

```

This example is using a newish feature of Java called `try-with-resources`. Because the `Scanner` is opened in the `()` it will automatically be closed. An alternative approach, where the programmer must remember to close the input stream when finished, is below:

```java
try { 
	Scanner input = new Scanner(inputFile);
	while(input.hasNext()) {
		String line = input.nextLine(); 
		line = line.replaceAll(search, replace); 
		System.out.println(line);
	}
	input.close(); //remember to close the file!
} catch(FileNotFoundException fnf) {
	System.out.println("File not found.");
	System.out.println(fnf.getMessage());
	System.exit(1);
}
```

Inside of the `try` block the `Scanner` may be used to read from the file just as it may be used to read from the command line:

```java
while(input.hasNext()) {
	String line = input.nextLine(); //read in the next line of the input
	line = line.replaceAll(search, replace); 
	System.out.println(line);
}
```

Note that strings are *immutable*! This means that when we call `replaceAll` a new string will be created and we must save that result in order to use it later in the program. In this case, we reuse the same `String` variable, but we could have chosen a different name.

### The `useDelimiter` Method	

The preceding example uses the `nextLine` method to read the input one line at a time. In this case, the newline character is the *delimiter*. Each time `nextLine` is called the `Scanner` returns a series of characters until it finds the next newline. 

The `useDelimiter` method allows the programmer to change the character that is used to separate the tokens in the file. For example, in the following file the programmer may want to use the `#` as the delimiter to separate the tokens or elements of the file:

```
one#two#three four#five
```
The following code fragment:

```java
String fileName = "hashdelimiter.txt";
File file = new File(fileName);
try (Scanner input = new Scanner(file)) { 
	
	//change the delimiter used by the Scanner
	input.useDelimiter("#");

	while(input.hasNext()) {
		String nextToken = input.next();
		System.out.println(nextToken);
	}
} catch(FileNotFoundException fnf) {
	System.out.println("File not found.");
	System.out.println(fnf.getMessage());
	System.exit(1);
}

```

would produce the output:

```
one
two
three four
five
```