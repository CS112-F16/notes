Composition
===========

In most cases, objects will contain data members that are references to other objects.  For example, we might have a `Student` class and an instance of `Student` has a reference to an instance of `Name`. 

## Student Record - Two Ways

```java
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
    
}

 public class Student {
    private Name name;
    private int id;
    
    public Student(Name name, int id) {
        this.name = name;
        this.id = id;
    }
    
    public Name getName() {
        return this.name;
    }
    
}

public class Driver {

    public static void main(String[] args) {
        Name n = new Name("Bob", "Jones");
        int id = 1234;
        Student s = new Student(n, id);
        
        //change the last name
        Name curname = s.getName();
        curname.setLast("Smith");
    }

}
```

In this first example, the `Driver` must be aware of how the `Student` object stores the `Name`.  It creates a `Name` object and passes it to the `Student` constructor.  When the `Driver` wishes to change the last name stored in the `Name` object, it first retrieves the object from the `Student` object and then invokes the appropriate method.

```java
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
    
}

public class Student {
    private Name name;
    private int id;
    
    public Student(String first, String last, int id) {
        this.name = new Name(first, last);
        this.id = id;
    }
    
    public void changeLast(String last) {
        this.name.setLast(last);
    }
    
}

public class Driver {

    public static void main(String[] args) {
        String first = "Bob";
        String last = "Jones";
        int id = 1234;
        Student s = new Student(first, last, id);
        
        //change the last name
        s.changeLast("Smith");
        
    }

}
```

In this second example, the `Driver` does not have to be aware of how the `Student` stores the `Name`.  In many ways, this is preferable since `Student` can change the way it stores the name and the API it exposes does not need to change.  No other code that uses `Student`'s API must change.  Notice that the `Name` class remains the same.  