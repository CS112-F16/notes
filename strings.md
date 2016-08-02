Strings
=======

A String is a sequence of characters. The `String` class provides various methods to access portions of a String, but note that Strings are **immutable**. That means that they do not change. To morph one String into another, you must use methods to create a new String object containing 
the new set of characters.

See the [Java Strings Tutorial](https://docs.oracle.com/javase/tutorial/java/data/strings.html) for more detail.

## Common Methods

There are several common methods you may invoke on a String as shown below. See the [String API](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html) for more detail:

- `charAt`
- `compareTo`
- `compareToIgnoreCase`
- `equals`
- `equalsIgnoreCase`
- `length`
- `substring`
- `replace`

## Concatenation

The `+` operator can be used to concatenate two or more strings together.  It can also be used to concatenate a string with other primitive types.

## Escape Sequences

**Escape sequences** tell the compiler to interpret the following character in a special way.  For example, in order to insert a quotation mark in a string, you must use the character sequence `\"`. If you use only the quotation mark (") the compiler will interpret it as the end of the string.  An example follows: `System.out.println("I \"love\" computer science.");`

The list of escape sequences in Java is as follows:

- `\t` - tab
- `\b` - backspace
- `\n` - newline
- `\r` - carriage return
- `\f` - formfeed
- `\'` - single quote
- `\"` - double quote
- `\\` - backslash

## Number/String Conversion

When an `int` is concatenated with a string it will automatically be converted to a string.

```java
int x = 2;
String s = "A number: " + x;
```

In the preceding example, the string `s` will have the value "A number: 2".

To convert an `int` into a `String` without concatenating it with another string, use the `valueOf` method of the `String` class.

```java
int x = 2;
String s = String.valueOf(x);
```

To convert a `String` to an `int`, use the `parseInt` method of the `Integer` class.

```java
String s = "2";
int x = Integer.parseInt(s);
```

## The `split` Method

The `split` method can be used to divide a String into several substrings. It takes as input a *regular expression* denoting the how the string should be split and returns an array of Strings. In the simplest case, the expression is a character denoting the delimiter to be used. The following example splits the String around the colon. The result is an array of Strings - `[a,b,c]`. Note that the delimiter is removed from the result.

```java
String s = "a:b:c";
String[] splitString = s.split(":");
```

