File Output
===========

## Search and Replace Example

The notes on [file input](https://github.com/CS112-F16/notes/blob/master/fileinput.md) demonstrate a search and replace program where the output is printed to the standard output stream. The following example extends `SearchAndReplace` to save the output to a new file.

The code is also available here: [SearchAndReplaceWithOutput.java](https://github.com/CS112-F16/code/blob/master/GeneralExamples/SearchAndReplaceWithOutput.java).

```java
import java.io.File;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.PrintWriter;
import java.io.FileWriter;

import java.util.Scanner;


/**
  * A class to demonstrate one method of file input in Java.
  * 
  * @author Sami Rollins
 **/
public class SearchAndReplaceWithOutput {

	public static void main(String[] args) {

		//if the appropriate arguments are not passed as input
		//print an error and exit the program
		if(args.length != 4) {
			System.out.println("usage: java SearchAndReplace <infile> <outfile> <searchTerm> <replaceTerm>");
			System.out.println("\texample: java SearchAndReplace in.txt out.txt hello goodbye");
			System.exit(1); //exit the program 
		}

		//store the command line arguments in temporary variables
		String inFileName = args[0];
		String outFileName = args[1];
		String search = args[2];
		String replace = args[3];

		//create an object wrapper around the file
		File inputFile = new File(inFileName); 

		//open the input file in a
		//try-with-resources block
		try (Scanner input = new Scanner(inputFile);
			PrintWriter output = new PrintWriter(new FileWriter(outFileName))) { 
			while(input.hasNext()) {
				String line = input.nextLine(); //read in the next line of the input

				//replace all instances of the search term with the replace
				//term
				//note: strings are immutable, so we need to save the result
				line = line.replaceAll(search, replace); 
				//send result to output file
				output.println(line);
			}
		} catch(FileNotFoundException fnf) {
			System.out.println("File not found.");
			System.out.println(fnf.getMessage());
			System.exit(1);
		} catch(IOException ioe) {
			System.out.println("Problem with output file.");
			System.out.println(ioe.getMessage());
			System.exit(1);			
		}

	}
}
```

This example expects four command line input values: 

- the input file name
- the output file name
- the search term
- the replace term

There are many ways to write output to a file in Java. Using a `PrintWriter` is very convenient as `System.out` is a `PrintWriter` and you are very familiar with the methods it provides, for example `println`. 

The following code creates a `PrintWriter` that will save output to the file with the name denoted by the contents of the variable `outFileName`:

```
PrintWriter output = new PrintWriter(new FileWriter(outFileName))
```

If the file does not exist it will be created. 

Notice that this code is in the try-with-resources statement. This means that the output stream will be automatically closed at the end of the `try` statement.

Also notice that a second `catch` block has been added to the statement. The instantiation of the `FileWriter` may generate an exception, for example if the file cannot be opened, and the exception must be caught. 

Finally, notice that several `import` statements have been added to allow the program to use several classes from the `java.io` package.