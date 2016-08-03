Iteration
=========

Iteration allows you to repeat a sequence of steps.  Java provides three different loops the allow you to implement an iterative algorithm: `for` loops, `while` loops, and `do-while` loops.

## `for`

The `for` loop is typically used as a counting loop.  If you want to execute a sequence of steps a fixed number of times (e.g., you know you need to do the same operation 10 times) you should use a `for` loop.  The syntax for a `for` loop is as follows:

```java
for(initialization; condition; update) {
    //statements
}
```

The keyword `for` is followed by parentheses.  Inside of the parentheses is the initialization of the control variable followed by a semi-colon, the condition followed by a semi-colon, and the update of the control variable.  The body of the loop is surrounded by curly braces.  A common for loop might look as follows:

```java
for(int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

Java also provides an `Iterable` interface.  Many of the data structures provided by Java are iterable, which means that they can be traversed using an enhanced `for` loop.  The *for-each* loop is similar to the `for` loop, but the syntax is more concise; the programmer need not maintain a control variable.

The following example shows two `for` loops, one typical `for` loop and the equivalent *for-each* loop:

```java
ArrayList<String> al = new ArrayList<String>();
al.add("one");
al.add("two");
al.add("three");

for(int i = 0; i < al.size(); i++) {
    String s = al.get(i);
    System.out.println(s);
}

for(String s: al) {
    System.out.println(s);
}
```

## `while`

The `while` loop is used in situations when the loop should execute as long as some condition is true.  For example, you might use a `while` loop to indicate that you want to continue to get input from a user until that user enters a sentinel value (e.g, enter 0 to end input).  The general syntax for a `while` loop is as follows:

```java
//control variable initialization
while(condition) {
    //statements
    //update control variable
}
```


The control variable is initialized before the loop, the condition is in parentheses following the `while` keyword, and the body of the loop is surrounded by curly braces.  The body of the loop must contain the update of the control variable.  Failing to update the control variable results in an **infinite loop**.

A `while` loop can be translated to a `for` loop and vice versa.  Below are two examples of `while` loops: the first is identical to the `for` loop above and the second is a better example of a `while` loop that executes until a sentinel value is entered.

```java
int i = 0;
while(i < 10) {
    System.out.println(i);
    i++;
}

System.out.println("Enter an int (0 to end input): ");
int i = scanner.nextInt();
while(i != 0) {
    System.out.println(i);
    System.out.println("Enter another int (0 to end input): ");
    i = scanner.nextInt();
}
```

## `do`

While a `for` loop can be translated to a `while` and vice versa, a `do` loop operates differently.  A `do` loop always executes at least once.  The syntax for a `do` loop is as follows:

```java
do {
    //control variable initialization/update
} while(condition);
```

Because you know the body of the loop will execute at least once, you can initialize your control variable in the same place where you update it. 

## Iterators

A common operation is traversal of all elements of a collection.  An iterator is an object that allows you to do so in a simple way.

The `java.util.Iterator` interface provides the following methods:

- `boolean hasNext()` - Returns true if the iteration has more elements.
- `E next()` - Returns the next element in the iteration.
- `void remove()` - Removes from the underlying collection the last element returned by the iterator (optional operation).

The `java.util.Scanner` class is an example of a class that implements the `Iterator` interface. The following piece of code reads the text of a file one word at a time.

```java
java.util.Scanner s = new java.util.Scanner(new java.io.File("test.txt"));
while(s.hasNext()) { 
 System.out.println(s.next());
}
```

Notice that the example uses the fully qualified names for the `Scanner` and `File`. This obviates the need to import `java.util` and `java.io` at the top of the class.