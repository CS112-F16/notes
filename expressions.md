Expressions
===========

A single `=` represents assignment and is typically read as "gets the value of".  For example, `x = 4` would be read as "x gets the value of 4".  The right-hand side of the equals sign may be any expression that evaluates to the type denoted by the type of the variable specified on the left.

## Mathematical Operators

- `+` - addition
- `-` - subtraction
- `*` - multiplication
- `/` - division
- `%` - modulo (remainder)

Java also provides **increment** and **decrement** operators.  `++` indicates add 1 and `--` indicates subtract 1.  The operator may appear on the right or the left of a variable name.  On the left, we refer to pre-increment/decrement, and on the right we refer to post-increment/decrement.  A pre-increment will first increment the variable and then execute the rest of the statement and a post-increment will first execute the statement and then increment the variable.  An example follows:

```
x = 5;
System.out.println(++x); //prints 6

x = 5
System.out.println(x++); //prints 5
```

You may also use `[operator]=`, for example `+=`, to indicate that you wish to operate on the variable provided on the left side of the assignment.  For example, `a += 3` is the same as `a = a + 3`.

## Relational Operators

- `==` - true if the left side is equal to the right side
- `!=` - true if the left side is not equal to the right side
- `>` - true if the left side is greater than the right side
- `<` - true if the left side is less than the right side
- `>=` - true if the left side is greater than or equal to the right side
- `<=` - true if the left side is less than or equal to the right side

```
int a = 5;
int b = 4;

System.out.println(a == b); //false
System.out.println(a != b); //true
System.out.println(a < b); //false
System.out.println(a > b); //true
System.out.println(a <= b); //false
System.out.println(a >= b); //true
```

## Logical Operators

- `!` - not
- `&&` - and
- `||` - or

## `==` versus `.equals`

`==` is used to compare **primitive types**. When using `==` to compare reference types you are comparing the memory locations of the objects. The expression will evaluate to true only if the references refer to exactly the same object.

Given the following class `Name`:

```
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

    public boolean equals(Name toCompare) {
        if(this.first.equals(toCompare.getFirst())&&
             this.last.equals(toCompare.getLast())) {
            return true;
        } 
        return false;
    }

}
```

The following statements would give the output indicated:

```
Name n1 = new Name("Bob", "Smith");

Name n2 = new Name("Sally", "Sue");

Name n3 = new Name("Bob", "Smith");
        
System.out.println(n1 == n2); //false
System.out.println(n1 == n3); //false
System.out.println(n1.equals(n3)); //true

n3 = n1;
System.out.println(n1 == n3); //true
```

In select cases it makes sense to compare references using `==`.  In most cases, you will want to implement a `.equals` method in each class.  The equals method returns true if the contents of the object on which it is called are the same as the contents of the object passed as input.

## DeMorgan's Theorem

- `!(a && b)` is the same as `!a || !b`
- `!(a || b)` is the same as `!a && !b`