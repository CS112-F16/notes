Exam 3 Review
=============

Following is a list of topics that may appear on Exam 3. *This list is subject to change.*

You may be asked to define a term; explain a concept; answer a short-answer, multiple choice, or true/false question about a concept; trace a block of code and describe its output; or implement a block of code.

There may be more programming/implementation questions on Exam 3 than there were on Exam 2.

Exam 3 **will** be cumulative but will focus more heavily on topics introduced since Exam 2. In addition to the book sections and topics noted below, Exam 3 may also ask questions related to the topics from [Exam 1](exam1review.md) and [Exam 2](exam2review.md).

### Book Sections Covered Since Exam 2
1. Chapter 12 - 12.1, 12.2
2. Chapter 13 - 13.1, 13.2


### Topics Covered Since Exam 2

1. Recursion
  - Defining the base case
  - Recursive call and making progress toward the base case
  - Tracing recursive methods
  - Helper methods
2. Linked Lists
  - Implementation 
  - Insertion/deletion
  - Recursive methods
3. HashMaps
  - `get` and `put` operations
  - `containsKey` method
  - Iterating over keys in a `HashMap`

### Practice questions

1. Write a while loop that verifies that a user enters a positive integer value.

2. Write a method called `evenlyDivisible` that accepts two integer parameters and returns true if the first parameter is evenly divisible by the second, or vice versa, and false otherwise.  Return false if either parameter is zero.

3. Write a method that takes as input an array of integers and will print the array in reverse order.  You do not need to use recursion for this question.

4. Write a method `getIth` for the `LinkedList` class.  The method will take as input an integer `i` and will return the object from the ith node in the list.  For a list containing A, B, C, D, E (in that order), given the input 2 the method would return B.

5. Implement a recursive method that takes as input a `char` and a `String` and returns the number of times the `char` appears in the `String`.  Given input 'c' and 'computer' the method would return 1.  For full credit, implement this method without using any loops.

6. Implement a `LinkedList` method `removeLastN`.  The method takes as input an integer n and removes the last n nodes from the list.  If the list contained 6 nodes, a call to removeLastN(3) would result in the list containing the first three nodes of the original list (e.g., original list: head->A->B->C->D->E->F new list: head->A->B->C) 

7. Implement a method that takes as input two `int[]` `arr1` and `arr2` and returns a new `int[]` where the ith position of the new array is the sum of the ith position of `arr1` and the ith position of `arr2`.  Example 1: arr1={1, 2, 3} arr2={4, 5, 6} returnedarr={5, 7, 9} Example 2: arr1={1, 2, 3} arr2={4, 5} returnedarr={5, 7, 3}

8. What does the following method of a LinkedList class do?
```
    public boolean mystery() {
        if(this.head == null) {
            return true;
        }
        return mystery(this.head, this.head.getNext());
    }
    private boolean mystery(Node n1, Node n2) {
        if(n2 == null)
            return true;
        if(n1.getData().compareTo(n2.getData()) < 0)
            return mystery(n2, n2.getNext());
        return false;
    }
```    

