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

### Accessing Array Elements

Each array element has a subscript that identifies its position in the array. It is extremely important to remember that the subscripts begin at 0. Therefore, an array of size 5 would have subscripts 0, 1, 2, 3, and 4. To access an array element, specify the name of the array followed by the element's subscript in square brackets. The subscript may also be represented by an int variable or expression that results in an int value. 

```java
int firstElement = numbers[0];
System.out.println("The second score is " + scores[1]);
int toChange = 3;
numbers[toChange+1] = 75; //use the assignment operator to change a value
```

If your program attempts to access an array element that does not exist, you will experience a runtime `ArrayIndexOutOfBoundsException`. Make sure that the number you place between the square brackets is a valid index for the given array.

### Arrays and Loops

Arrays and for loops go hand in hand. It is quite common to use a `for` loop to iterate through every element of an array and perform a specific action. The example below initializes every element of the array `numbers` to 100.

```java
int[] numbers = new int[10];
for (int i = 0; i < numbers.length; i++) {
 numbers[i] = 100;
}
```

Notice that the length of an array can be retrieved by using the dot operator to access the member `length`. However, it is important to note that the length of an array is the total number of elements one can store in the array. It is certainly possible that the number of valid elements in an array is smaller than the total number of elements the array can store. In this case, it is common to keep a separate integer variable to represent the number of valid elements in an array as shown below.

```java
int count = 0;
int[] array = new int[5];
array[count++] = 4;
array[count++] = 12;
for(int i = 0; i < count; i++) {
    System.out.println(array[i]);
}
```

### Arrays and Methods

A single array element can be passed to a method, as can an entire array. If an entire array is passed into a method, a reference to the original array is passed. As a result, any changes made to the array by the method will be reflected in the caller.

```java
public class ArraysAndMethods {

	public void absoluteValues(int[] numbers) {

		for(int i = 0; i < numbers.length; i++) {
			if(numbers[i] < 0) {
				numbers[i] = numbers[i] * -1;
			}
		}
	}

	public static void main(String[] args) {
		int[] numbers = {4, -1, 5, 3, -9, 4, -4, 2};

		ArraysAndMethods aam = new ArraysAndMethods();
		aam.absoluteValues(numbers);
		for(int number: numbers) {
			System.out.println(number);
		}
	}

}
```

### Arrays of Objects

Each element of an array may be an object, not simply a primitive type. In this case, the array variable is a reference to a list of references. Each element of the array is a reference to an object. When the array itself is created, the objects are not instantiated (as shown below). 

```java
//assume a class Name exists
Name[] names = new Name[5];
```

Below, we create two new objects of type `Name` and place their addresses in positions 0 and 1 of the array, respectively.

```java
names[0] = new Name("Bob", "Smith");
names[1] = new Name("Jane", "Wu");
```

### Inserting Elements into an Array

Adding a new element at an arbitrary position in a array is more challening then adding to an `ArrayList`. If the element's value dictates that it should be inserted anywhere but in the rightmost position, the insert procedure must shift the the right all elements that come after the element to be inserted. The following example implements a procedure to insert an element at index 1 of an array containing `count` elements. 

```java
//insert an item at position 1
int newItemLocation = 1;
int newItem = 2;
int index = count;

//move items 3-count to the right one space
while(index > newItemLocation && index >= 0) {
	numbers[index] = numbers[index-1];
	index--;
}

numbers[newItemLocation] = newItem;
count++; //don't forget to update the count of items in the array!
```

Notice that the example assumes that there is at least one empty space in the array. If there is not, one option is to disallow the insertion. Another option is to create a new, larger array, copy all elements from the first array to the second, and insert the new element at the correct position.

### Deleting Elements from a Sorted Array

Similar to insertion, deletion requires that all elements to the right of the element removed be moved to the left one position. The following example illustrates a procedure to delete the element at position 0 of an array. 

```java
int deleteLocation = 0;
for(int i = deleteLocation; i < count; i++) {
	numbers[i] = numbers[i+1];
}
count--;
```

### Two-Dimensional Arrays

Java also supports two-dimensional arrays. All of the data in a two-dimensional array must be of the same type. However, you can imagine the data stored in a matrix of several rows and columns. To declare a two-dimensional array, you simply use two sets of square brackets. Similarly, the access and modify elements of a two-dimensional array, you must specify the element's row and column. 

```java
//declare a 2D array with 5 rows and 10 columns
//the array might represent 10 homework scores for each
//of 5 students
double[][] scores = new double[5][10];
scores[0][0] = 90; 
```