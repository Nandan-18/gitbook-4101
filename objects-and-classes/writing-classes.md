# Writing Classes

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 4.3, 4.6, and 4.7
{% endhint %}

## Custom Classes

Although there are thousands of classes built into the language, Java allows you to define your own classes to create custom data types. This will lead into the creation of more complex programs composed of multiple classes and source files.

{% embed url="https://www.youtube.com/watch?v=MDLK8PyrkwY&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

### A Student Class

A typical class contains instance variables, constructors, and methods. You'll learn about each of these in detail in the coming sections, but the general format looks like this.

```java
public class ClassName {
    // instance variables go here

    // then constructors

    // and lastly methods
}
```

Consider the following `Student` class that might represent a student entity in a grading system. There are some references to more advanced aspects of the language, so don't worry if you're unsure what some of these terms mean. We'll cover them in detail throughout this section.

{% code title="Student.java" %}
```java
public class Student {
    private long id;
    private double gpa;
    private String name;
    
    /*
     * Constructs an instsance of the Student class.
     */
    public Student(long id, double gpa, String name) {
        this.id = id;
        this.gpa = gpa;
        this.name = name;
    }
    
    public long getId() {
        return id;
    }
    
    public double getGpa() {
        return gpa;
    }
    
    public String getName() {
        return name;
    }
}
```
{% endcode %}

You probably noticed that there's no `main` method. Usually, classes that represent program entities like this don't contain the `main` method. That's written in a separate class designed to run the program. Each program needs to have a single `main` method, so most classes will not have one.

{% code title="StudentTester.java" %}
```java
public class StudentTester {
    public static void main(String[] args) {
        Student student = new Student(1234L, 3.73, "John Doe");
        
        // we've created a Student object and stored it in a
        // variable called student. we can call the methods
        // of the Student class through this variable.
        
        long studentId = student.getId();          // retrieve student id
        double studentGpa = student.getGpa();      // retrieve student gpa
        String studentName = student.getName();    // retrieve student name
        
        System.out.println(studentId);             // print student id
        System.out.println(studentGpa);            // print student gpa
        System.out.println(studentName);           // print student name
    }
}
```
{% endcode %}

To compile and run the program, you need to compile both source files but execute only the file with the `main` method \(in this case, the `StudentTester` class\).

```text
$ javac Student.java StudentTester.java
$ java StudentTester
1234
3.73
John Doe
```

Since this program has two source files, we need to compile them both. We pass both files to `javac` \(separating them with a single space\). Alternatively, we could've used a wildcard to compile all files with a `.java` extension.

```text
$ javac *.java
$ java StudentTester
1234
3.73
John Doe
```

## Instance Variables

An object stores its data in class-level fields called instance variables. The `Student` class has three instance variables—`id`, `gpa`, and `name`. Instance variables look similar to the variables you've already worked with \(which are called local variables\), except they come with an access modifier.

* `private`
* `default`
* `protected`
* `public`

A `private` variable is accessible only within the class in which it's defined. Unless you have a good reason to break this convention, your instance variables should declared as `private`. A `public` variable is accessible from everywhere within your program.

`default` and `protected` variables are a little different, and require some additional knowledge about program and class structure that you haven't yet learned. A package is a group of related classes, similar to a folder. A `default` variable is accessible within the class in which it's defined, as well as from within the same package. A `protected` variable is accessible within the class in which it's defined, from classes defined in the same package, and from all subclasses \(even if these are defined in a separate package\).

Instance variables are customarily defined at the top of the class.

{% code title="Student.java" %}
```java
public class Student {
    private long id;
    private double gpa;
    private String name;

    // implementation details not shown
}
```
{% endcode %}

### Final Instance Variables

If you wish to define a `final` instance variable, you can do so in much the same way that you've done with local variables. Conventionally, you should group any `final` variable declarations separate from the rest of your instance variables.

{% code title="Student.java" %}
```java
public class Student {
    private final long id;    // once set, this value will never change
    private double gpa;
    private String name;
}
```
{% endcode %}

If you implement your program to assign a single, permanent `id`, it might make sense to make it `final`. Fields like `gpa` and `name`, which may change over time, should not be `final`. You must guarantee that a `final` variable is assigned a value in each of your constructors.

Let's take a deep dive into fields. Don't worry if some of the content of this video sounds unfamiliar. We haven't covered it all yet, so it should! It talks about instance variables, static fields, and getter and setter methods. Static fields, getter methods, and setter methods are all covered in more detail in the next couple sections.

{% embed url="https://www.youtube.com/watch?v=wIiZ-7sgq50&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## Constructors

A constructor is in charge of creating an instance of a class. For simple programs like the ones you'll be writing, this means initializing your instance variables. You can include several constructors for your class, each of which construct the object in slightly different ways. The `Student` class, though, has only one.

{% code title="Student.java" %}
```java
public class Student {
    private final long id;
    private double gpa;
    private String name;

    /*
     * Constructs an instsance of the Student class.
     */
    public Student(long id, double gpa, String name) {
        this.id = theId;
        this.gpa = theGpa;
        this.name = theName;
    }
}
```
{% endcode %}

The name of your constructor must always be the same name as your class. Almost all constructors that you'll be using and writing should be `public`. Constructors may accept as input the values they will use to initialize the instance variables of the object.

### The `this` Keyword

The `Student` constructor accepts the local variables `id`, `gpa`, and `name`. Often times, you'll see the local variables and instance variables are given the same name. Understandably, this can get a bit confusing.

{% code title="Student.java" %}
```java
public class Student {
    private final long id;
    private double gpa;
    private String name;

    /*
     * Constructs an instsance of the Student class.
     */
    public Student(long id, double gpa, String name) {
        // how you do distinguish between the local constructor variables
        // and the class-level instance variables?
    }
}
```
{% endcode %}

In situations like these, you need to use the `this` keyword to indicate that you're referring to a class-level variable declared in this class. The general format is `this.instanceVariable = localVariable;`.

{% code title="Student.java" %}
```java
public class Student {
    private final long id;
    private double gpa;
    private String name;

    /*
     * Constructs an instsance of the Student class.
     */
    public Student(long id, double gpa, String name) {
        this.id = id;
        this.gpa = gpa;
        this.name = name;
    }
}
```
{% endcode %}

While we've covered the `this` keyword within the context of constructors, but that's not the only ways in which it is \(or can be\) used.

{% embed url="https://www.youtube.com/watch?v=cdrTzCY4q4w&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

