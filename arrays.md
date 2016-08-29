Arrays
======

An array allows the programmer to store a list of elements, *all of the same type*, in a contiguous block of memory. The size of an array must be specified when it is instantiated and cannot change.


### Declaring Arrays

An array declaration creates a reference to the first element of the array. The declaration includes the type of the elements that will be stored in the array, a name for the array, and the square brackets (`[]`) specify that the variable will be an array. 

```java
int[] numbers;
```

The previous example declares a reference to the array, but does not instantiate the array. Note that the example does not specify the size of the array. To instantiate the array, the `new` operator must be used.

```java
//declare a reference to the array
int[] numbers;

//instantiate an array of 10 integers
numbers = new int[10]; 

//alternative: declare and instantiate all at once
double[] scores = new double[10];
```

It is also possible to assign values to each position of an array at the time of instantiation. The initializer list is used for this purpose: 

```java
//declare an array of size 5 called numbers and
//initialize its elements to 1, 2, 3, 4, and 5
//respectively
int[] numbers = {1, 2, 3, 4, 5};
```

