# Static Members

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 4.4
{% endhint %}

## Static Fields

You've used the `static` modifier only sparingly in your programs. The `main` method, of course, is always `static`. And once or twice, you declared a `Scanner` as `static`. Now, you'll see why and how to declare and use `static` fields. More importantly, you'll see the difference between `static` and non-static fields.

{% code title="Student.java" %}
```java
public class Student {
    private int id;
    private static int nextId = 1;

    // some implementation details not shown
}
```
{% endcode %}

The difference between a `static` and non-static variable is simple. Every instance of the `Student` class will have a separate `id` variable with a unique value. However, the `nextId` variable is shared among all instances. Changing its value from any instance changes it for all instances.

{% code title="Student.java" %}
```java
public class Student {
    private int id;
    private static int nextId = 1;

    public Student() {
        id = nextId++;
    }
}
```
{% endcode %}

`nextId` will always represent a value one greater than the largest `id` currently in use across all instances of the `Student` class. The constructor uses this value to set the `id` of any object it creates, then increments the `nextId` value.

The `nextId` variable is `private`, and therefore, only available from within the `Student` class. `static` variables accessible from other classes typically are referenced using the name of the class in which it is defined.

{% code title="Teacher.java" %}
```java
public class Teacher {
    public static int id = 1;
}
```
{% endcode %}

{% code title="Student.java" %}
```java
public class Student {
    private int id;
    private static int nextId;

    // some implementation details not shown

    public void someMethod() {
        int teacherId = Teacher.id;    // syntax: ClassName.staticVariableName
    }
}
```
{% endcode %}

You can reference all `static` variables in this manner, it's just not necessary when doing so from within the same class in which they're defined.

### Static Constants

`static` variables aren't incredibly common, but `static` constants certainly are. The `Math` class uses several `static` constants, which you've seen already.

```java
Math.PI    // Math is the name of the class, and PI is the static constant
```

You've also been using `System.out.println` since the very beginning of the course. `System` is a class, and `out` is a `static` variable \(referring to a `PrintStream` object\) declared in that class. It is tagged with a `public` access modifier, which is why you can reference it in the way you do.

```java
public class System {
    public final static PrintStream out = /* ... */;

    // some implementation details not shown
}
```

Since it is marked as `final`, you're free to make it `public`. And since it's `static`, you can reference it through the class itself \(as opposed to through an object of that class\).

We've touched on the `final` keyword in a few different places, and there are a few more still that we haven't gotten to yet. We'll table the conversation on method overriding and subclassing, as we'll be covering those topics in a later section.

{% embed url="https://www.youtube.com/watch?v=Y8xBrYyqIqg&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## Static Methods

A `static` method is one that doesn't operate on an object. There's no implicit parameter, though there can be zero or more explicit parameters. The `Math` class is a great example of `static` methods you've used in your programs.

```java
Math.max(a, b)
Math.min(a, b)
Math.pow(a, b)
```

These are all `static` methods. There is no `Math` object on which they're invoked.

When you write your own `static` methods, it's important to remember that these methods cannot access your instance variables. You should have very few `static` methods. If you find yourself converting fields or methods to `static` to satisfy compilation problems, there's probably a deeper issue with your code.

{% code title="Student.java" %}
```java
public class Student {
    private static int nextId = 1;

    private int id;
    private double gpa;
    private String name;

    public Student(double gpa, String name) {
        this.id = Student.nextId++;    // assign id and increment nextId
        this.gpa = gpa;
        this.name = name;
    }

    public static int getNextId() {
        // you'll get a compilation error if you try to
        // access non-static fields from a static method
        
        return Student.nextId;
    }
}
```
{% endcode %}

### Using Static Methods

There are three primary scenarios in which a `static` method might be a good design choice.

* If a method never needs to access an object's state because all required information is supplied via explicit parameters.

An example of this would be the `Math.pow` method \(or any of the `static` methods of the `Math` class\). It doesn't need to access the state of any `Math` object, because all of the information it needs is supplied through the explicit parameters.

```java
Math.pow(a, b)
```

This method computes `ab`, and information hypothetically contained in the state of a `Math` object doesn't change how this is done or assist in doing it.

* If a method only needs to access `static` fields of the class in which it is defined.

An example of this would be the `getNextId` method of the `Student` class. It is a simple method, serving only to return the value of the `static` variable `nextId`.

```java
public static int getNextId() {
    return Student.nextId;
}
```

It doesn't need to know about or access any of the instance variables.

* If you want to create a factory method.

Factory methods are something you haven't used too much, but they are an important design pattern to understand. Certain classes opt for `static` factory methods \(rather than constructors\) to construct objects. An example of this would be the `NumberFormat` class.

```java
NumberFormat currencyFormatter = NumberFormat.getCurrencyInstance();
NumberFormat percentFormatter = NumberFormat.getPercentInstance();

double x = 0.78;   // this is what you'll be formatting

System.out.println(currencyFormatter.format(x));    // $0.78
System.out.println(precentFormatter.format(x));     // 78%
```

Constructors impose a few restrictions on how objects are created, which gives rise to the use case of `static` factory methods as an alternative.

* You can't name your constructors. They must take on the name of the class.

If you're the author of the `NumberFormat` class, you'd want to distinguish between the currency and percent instances. This can be done by adding a parameter that aligns to one instance or another. However, it is much more clear to specify the requested instance right in the name of the method. Constructors cannot do this, but `static` factory methods can.

* Constructors can't vary the type of the constructed object.

The factory methods of the `NumberFormat` class sometimes return instances of the `DecimalFormat` class, which is a specialized subclass that extends the `NumberFormat` class. This allows for more customized formatting, as needed, but is not something a constructor can do.

Now that we have a better understand of static members, let's take a look at some of the differences between static and non-static methods.

{% embed url="https://www.youtube.com/watch?v=ZXQFGiGtoo4&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

