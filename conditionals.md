Conditional Statements
======================

Conditional statements allow the programmer to specify that a block of code should only be executed if a particular condition is met.

## `if`

The syntax of an `if` statement in Java is as follows:

```java
if (condition) {
	//one or more statements
}
```

- `if` is a keyword
- The condition is surrounded by parentheses.
- The block of statements to be executed is surrounded by curly braces.
  - If you only have one statement in the body you *may* omit the curly braces. It is recommended, however, that you always use them.
- It is good coding style to indent the body of your `if`. This is not required by the Java compiler, but it is required by the instructor!

You may follow an `if` with an `else`, and nest if-else statements as follows:

```java
if(score > 90) {
    System.out.println("A");
} else {
    if(score > 80) {
        System.out.println("B");
    } else {
        if(score > 70) {
            System.out.println("C");
        } else {
            System.out.println("F");
        }
    }
}
```

As the example above demonstrates, it can get quite messy to test several conditions.  The above code can also be written as shown below using `else if` conditions.

```java
if (x > 90) {
    System.out.println("A");
} else if (x > 80) {
    System.out.println("B");
} else if (x > 70) {
    System.out.println("C");
} else {
    System.out.println("F");
}
```

Following an `if` you may have 0 or more `else if`s and 0 or 1 `else`.

Once a condition is satisfied, the remaining conditions will not be tested.  In the example above, if score is 94, the first condition will be true, the program will print A, and skip the remaining else ifs.

The boolean operators `&&` and `||` are used to chain together multiple conditions.  For example, to determine whether a particular string contains the characters x, y and z, y, you might do the following:

```java
if(s.contains("a") && s.contains("b") && s.contains("c")) {
    //statements
}
```

Java uses **short-circuit evaluation**. When evaluating a boolean condition, the expression will be evaluated left to right and evaluation will stop as soon as it can be determined that the condition will be true or false.

Consider the following example:

```java
if (a == 1 || b == 2) {
	//do something
}
```

In the case that `a` is equal to `1` there is no need to check whether `b` is `2`. The expression will be true regardless of the value of `b`.

It is very common to see the following:

```java
if(reference != null && reference.method() == value) {
	//do something
}
```

If `reference` is `null` then the expression is guaranteed to be false and the second half of the expression will not be evaluated. Reversing the condition would not be equivalent as it would result in a `NullPointerException` in case `reference` is `null`.