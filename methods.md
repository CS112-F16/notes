Methods
=======

Methods, similar to functions in other languages, are a mechanism for program decomposition.  They provide a way to group together statements that perform a particular operation.  If your program executes the operation repeatedly, you need only call a method that executes that operation rather than repeatedly writing the same several statements to perform the operation.

Each method has a **signature** that specifies its name and the type, number, and order of its **parameters**.  Parameters are the inputs to a method.

A method **header** includes the information provided in the signature, along with the return value of the method.  It may also (optionally) specify a **visibility modifier**.  This indicates from where the method can be called.  The modifier `public` indicates that the method may be called from anywhere.  The modifier `private` indicates that the method may only be called from other methods in the same class.

Example: `public int addOne(int input)`

## Calling Methods

A method is called on an object.  To call a method you specify the name of the variable that stores a reference to the object, followed by the **dot operator**, followed by the name of the method, followed by the parameters it accepts enclosed in parentheses.  If the method accepts no parameters, you use empty parentheses.

```java
String s = new String("Bob");
int size = s.length();
char c = s.charAt(1);
```

Typically, a call to a method that returns a value should appear on the right hand side of an equals sign.  This is because you typically want to save the value returned and do something with it later.  You can also pass the value as a parameter to another method.  For example: `System.out.println(s.length())` passes the result of calling the length method on `s` (which will be the size of the string in the example above) to the `println` method called on the object `System.out`.

## Writing Methods

```java
public void printMessage(String first, String last) {
    System.out.println("Hello " + first + " " + last  + ",");
    System.out.println("Welcome to our cool program.");
    System.out.println("We hope you enjoy it!");
}

public static String getMessage(String first, String last) {
    String s = "Hello " + first + " " + last + ",";
    s += "Welcome to our cool program.";
    s += "We hope you enjoy it!";
    return s;
}
```

The **body** of a method is enclosed in curly braces.  The parameter list contains a comma separated list where each item is a type followed by a name.  The name given to a parameter (e.g., `first` and `last` above) is the name used to refer to the variable within the method.

If a method does not return anything its return type is `void`.  If a method's return type is something other than void, it must return a value of that type. You will get a compiler error if the method does not return a value.

A return statement is simply the keyword `return` followed by the value you wish to return.

## Pass By Value

When a method is called, an **activation record** is created and placed on the top of the **call stack**.  Each activation record maintains information about state of the program during the execution of the method.  This information includes the values of local variables and formal parameters.  The top record on the call stack maintains information about the currently executing method. 

Java uses **pass-by-value** semantics.  That means, when a method is called, the values of the actual parameters are copied into the memory cells holding the formal parameters in the new activation record.  For primitive types, this means that copies of the variables are created.  However, for reference types, this means that there are now two references to the same object.  Changes made to the object from within the method will be reflected after the method returns.**

```java
public class Test {
  
    public static void addOne(int x) {
        x = x + 1;
        System.out.println("Test.addOne:: x=" + x); //x is 2
    }

    public static void main(String[] args) {
        int x = 1;
        System.out.println("Test.main:: x=" + x); //x is 1
        addOne(x);
        System.out.println("Test.main:: x=" + x); //x is 1
    }
}
```

In the example above, there are two copies of `x`, one in the activation record for main and one in the activation record for `addOne`.

```java
public class Test {

    public static void changeLastToSmith(Name n) {
        n.setLast("Smith");
    }

    public static void main(String[] args) {
        Name n = new Name("Bob", "Jones");
        System.out.println(n);//Bob Jones
        changeLastToSmith(n);
        System.out.println(n); //Bob Smith
    }
}

public class Name {
    private String first;
    private String last;

    public Name(String first, String last) {
        this.first = first;
        this.last = last;
    }

    public void setLast(String last) {
        this.last = last;
    }

    public String toString() {
        return this.first + " " + this.last;
    }
}
```


In the example above, there are two references to the `Name` object.  When the method changes the contents of the object, the changes are seen by the reference in the main method.

## Scope

**Scope** refers to the area of a program where a variable can be referenced.  

- Data members of a class may be referenced from anywhere in the class.  
- Parameters of a method may be referenced only within the method.
- **Local variables** declared in a method may be referenced only within the method.

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

    public void printFullName() {
        //the local variable full can 
        //only be referenced in the 
        //printFullName method                                               
        String full = first + " " + last;
        System.out.println(full);
    }

    public boolean equals(Name toCompare) {
        //the parameter toCompare can 
        //only be referenced in the 
        //equals method                                                      
        return (this.first.equals(toCompare.getFirst()) && this.last.equals(toCompare.getLast()));
    }

}
```


`this`

The `Name` class above also shows an example of using the `this` reference.  Notice that the `Name` constructor names its parameters `first` and `last`, but the class `Name` already has data members `first` and `last`.  In this case, there is a naming conflict in the constructor.  One way to solve the conflict would be to choose different names for the parameters (e.g., `newFirst` and `newLast`).  The more common practice, however, is to explicitly refer to the instance fields using `this`.  `this.first = first` indicates that the `first` variable of this object should get the value of the variable `first` that is local to the method.