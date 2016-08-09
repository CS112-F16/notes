Collections Framework
=====================

A collection groups multiple elements into a single unit. Examples include the following:

- A poker hand is a collection of cards.
- A mail folder is a collection of individual messages.
- A telephone directory is a collection of name and number pairs.

The [Java Collections Framework](https://docs.oracle.com/javase/tutorial/collections/) provides efficient implementation of many common data structures and algorithms. A programmer can use the classes provided in the `java.util` package to store and retrieve data efficiently. There are many common data structures and programmer will choose a data structure based on how individual data elements will be added to and accessed in the collection. 

## `ArrayList`

The `ArrayList` provides a way to maintain a list of items.  

Some of the key operations of an `ArrayList` are as follows:

- `add` - insert an object to the end of the list, or at an arbitrary position.  The first position of an `ArrayList` is position 0.
- `contains` - given an object, contains returns true of the `ArrayList` contains the object and false otherwise.
- `get` - given an index, returns the object at that position in the `ArrayList`.
- `indexOf` - given an object, returns the position of the object in the `ArrayList`.
- `isEmpty` - returns true if the `ArrayList` is empty and false otherwise.
- `remove` - you may remove a particular object, or the object at a particular index.
- `set` - given an index and an object, replaces the current object at the specified index with the new object.
- `size` - returns the number of objects currently in the `ArrayList`.
- `clear` - removes all elements from the list.

An example that declares and initializes a new `ArrayList` then adds two `String` objects to the list follows:

```java
ArrayList<String> names = new ArrayList<String>();
names.add("Bob Smith");
names.add("Sally Sue");
```

The example above uses slightly different syntax than we've seen in previous examples.  In particular, the `<String>` is new.  The Collections Framework uses [generics](https://docs.oracle.com/javase/tutorial/java/generics/).  An `ArrayList`, for example, can hold a list of any type of object.  The `<String>` allows us to specify the type of object we wish to store in a particular list.  The results are that only objects of the correct type can be added to the collection and when objects are removed they need not be cast to the appropriate type.

The example below demonstrates three `ArrayList` objects.  The first contains Strings and the second and third contain Integers.  Also, notice that, although a collection must store a reference, not a primitive type, Java will automatically convert from `int` to `Integer` and vice versa.

```java
ArrayList<String> names = new ArrayList<String>();
names.add("Bob Smith");
names.add("Sally Sue");
String firstname = names.get(0);

ArrayList<Integer> ids = new ArrayList<Integer>();
ids.add(new Integer(1234));
ids.add(new Integer(5678));
Integer firstid = ids.get(0).intValue();

ArrayList<Integer> moreids = new ArrayList<Integer>();
moreids.add(1234);
moreids.add(5678);
int morefirstid = moreids.get(0);
```

## `static` Methods of `Collections`

The `Collections` class provides several static methods that operate on `ArrayList` and other objects.  Two of the most notable methods are `sort` and `shuffle`.  Calling the `sort` method will sort a given `ArrayList`, and calling `shuffle` will arrange the elements of an `ArrayList` in random order.  An example follows:

```java
ArrayList<String> strs = new ArrayList<String>();
strs.add("one");
strs.add("two");
strs.add("three");
Collections.sort(strs);
/* items now in alphabetical order */

Collections.shuffle(strs);
/* items now in random order */
```

## `Map`

A `Map` provides a way to stored data that provides efficient access to a value given a key that maps to that value.  A good example of this is a search engine.  Google, for example, maps the words you enter in your search to a list of the web pages that contain those words.  To support this functionality, the `HashMap` class provides the following methods:

- `get` - takes an object representing a key and returns the corresponding value.
- `put` - takes a key and value pair (both objects) and inserts them into the `HashMap`.
- `clear` - removes all items from the `HashMap`.
- `isEmpty` - returns true if there are no items in the `HashMap`.
- `remove` - takes as input an object representing a key and removes the corresponding value from the `HashMap`.
- `keySet` - returns a `Set` of all of the keys in the `HashMap`. 
- `values` - returns a collection of all of the values in the `HashMap`.

```java
HashMap<String, ArrayList<String>> documents = new HashMap<String, ArrayList<String>>();
```

`HashMaps` also use generics. When declaring or instantiating a `HashMap`, you should specify the types of both the keys and the values.  The example above creates a `HashMap` that maps `Strings` to `ArrayLists` of `Strings`.  This would be appropriate if you wished to store a mapping from a word to a list of filenames where that word occurred.

It is also possible to create a `HashMap` of `HashMaps`:

```java
HashMap<String, HashMap<String, String>> booklist = new HashMap<String, HashMap<String, String>>();
HashMap<String, String> morrisonbooks = new HashMap<String, String>();
morrisonbooks.put("A Mercy", "0307264238");
morrisonbooks.put("Beloved", "1400033411");
booklist.put("Morrison, Toni", morrisonbooks);


String author = "Morrison, Toni";
String book = "A Mercy";
System.out.println("ISBN: " + booklist.get(author).get(book));
for(String nextbook : booklist.get(author).keySet()) {
    System.out.println("Book: " + nextbook);
}
```

The example above demonstrates how you might store data to make it efficient to access the ISBN number of a book given an author and title.  It also demonstrates how to list all books by a given author.