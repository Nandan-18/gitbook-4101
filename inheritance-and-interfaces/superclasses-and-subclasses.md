# Superclasses and Subclasses

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 5.1 and 5.2
{% endhint %}

## Hierarchies

Java classes are structured into hierarchies, where each class is either an ancestor or descendant of one or more other classes. This hierarchy defines a set of inherited properties and behaviors, much like our own familial lineages define certain traits about ourselves.

As we dive more into the concept of inheritance and class extension, we'll see just how this works. We'll see ways in which we can define custom hierarchies, as well as parent-child relationships that exist amongst built-in Java classes.

### A Parent to them All

At the top of the hierarchy of classes sits the `Object` class. All classes, whether they are built into the language or defined by another programmer \(i.e., you!\), implicitly inherit properties from the `Object` class. We say this extension is implicit because you, as the programmer, do not to include any special keywords. In fact, you cannot prevent your class from inheriting from the `Object` class even if you wanted to.

#### Passed Down

From the `Object` class, all Java classes inherit the following methods.

* `clone()`
* `equals(Object obj)`
* `finalize()`
* `getClass()`
* `hashcode()`
* `notify()`
* `notifyAll()`
* `toString()`
* `wait()`
* `wait(long timeout)`
* `wait(long timeout, int nanos)`

Many of these are beyond the scope of this course. However, we've already used \(and overridden, which we'll talk more about later\) a couple of these: `equals(Object obj)` and `toString()`. You can read more about the behavior and uses of these methods in [the documentation](https://docs.oracle.com/javase/7/docs/api/java/lang/Object.html).

Any class your write or use in Java will have access to these methods, and programmers have the option of overriding their behavior \(as we've done with `toString()`\). You haven't written any of these methods, but have access to them because they are inherited from the `Object` class.

## Relationships

In object oriented programming, we typically encounter _is-a_ or _has-a_ relationships. We'll be reviewing both, but it determines whether inheritance is the right design decision or not.

When deciding if a class we're writing is a good candidate for inheritance, we need to ask ourselves a simple question. Is the class we're writing a type of some other potential parent class we've already written? Let's clarify.

Suppose we write an `Animal` class, and later we're designing a `Tiger` class. The question we need to ask is: Is a `Tiger` an `Animal`? Clearly, the answer is yes. So, yes, the `Tiger` class is a good candidate to inherit from the  `Animal` class. If the answer is no, then perhaps inheritance is not the best choice.

### To Inherit or Not to Inherit

Let's quickly review the _is-a_ relationship. Suppose we've written a `BankAccount` class. Now, as we're writing `CheckingAccount` and `SavingsAccount` classes, we ask ourselves:

> Are checking accounts and savings accounts bank accounts?

In both cases, the answer is yes. `CheckingAccount` and `SavingsAccount` should inherit from `BankAccount`. They are both _types_ of bank accounts.

Now, suppose we have an `AccountHolder` class that keeps track of the information of the owner of a bank account. We, again, ask ourselves:

> Is an account holder a bank account?

Eh, not really. But, a bank account _has_ an `AccountHolder`. In this case, the `AccountHolder` should be an instance variable of the `BankAccount` class, but should not extend `BankAccount`.

### Parents and Children

When we talk about class inheritance and hierarchies, we need a reliable way in which we can refer to each component of the relationship. A superclass refers to the class from which other classes inherit. It is the parent in the relationship, and is often referred to as the parent class. A subclass refers to the class that inherits from another class. It is the child in the relationship, and is often referred to as the child class.

Naturally, a class can be simultaneously a parent and a child \(just as we, as humans, have parents and might one day also have children of our own\). A subclass can have only one direct parent class; however, parent classes might \(and often do\) have many children who extend it.

#### Parents

When we create a class intended to serve as a parent, we do not need to do anything differently from what we've always done. Suppose we're writing a `Vehicle` class that will serve as our parent. The `Vehicle` class will store general properties and support general actions that might be common of all vehicles.

```java
public class Vehicle {
    protected int wheels;
    protected int capacity;

    public Vehicle(int wheels, int capacity) {
        this.wheels = wheels;
        this.capacity = capacity;
    }

    public void drive() {
        // implementation details here
    }
}
```

Surely, there would be more to this class, but we can leave it here for now. This is purely for demonstration purposes. You'll notice that our instance variables have been declared as `protected`, which is different from the typical `private` access modifier we've used. Protected variables are visible \(i.e., accessible\) from any subclasses, while private variables are not \(subclasses can still access private instance variables of their parents using the parent-provided getter/setter methods\).

#### Children

Our children classes can be specific _types_ of vehicles: cars, motorcycles, busses, trucks, etc. These will have similar basic functionality, but their implementations might need to be altered or enhanced in some way. Enter inheritance and the Java keyword `extends`.

We use the `extends` keyword to create a class that inherits all properties of its parent class plus whatever additional properties and functionalities we include in the child class. Suppose we wanted to write a `Motorcycle` class.

```java
public class Motorcycle extends Vehicle {
    public Motorcycle(int capacity) {
        super(2, capacity);    // more on the super keyword later
    }

    public void popWheelie() {
        // implementation details here
    }
}
```

Our `Motorcycle` class will now include everything the `Vehicle` class included, plus any additional things we choose to add to it \(i.e., popping a wheelie\). We're _enhancing_ the functionality of the `Vehicle` class through the `Motorcycle` class. Even though we haven't created a `drive` method in our `Motorcycle` class, we can use it because it exists in the `Vehicle` class. It's as if we've copied and pasted everything from `Vehicle` into `Motorcycle`.

{% embed url="https://www.youtube.com/watch?v=5nUPGlN2Ovo&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## Working from the Child

There are a few things we can do from our child classes, both within the context of the child class itself and in respect to the parent class. Let's take a look at few options.

{% embed url="https://www.youtube.com/watch?v=JaGfCDLLdd4&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

### Overriding Methods

We've already seen the concept of overriding methods with the `toString` method. Now, we'll take a look at overriding any method of a superclass.

```java
public class MySuperClass {
    public void sayHello() {
        System.out.println("Hello, there!");
    }
}
```

The `sayHello` method will simply print `Hello, there!` to the console. A subclass will have access to this method, but can also change its behavior by overriding it using the `@Override` keyword.

```java
public class MySubClass extends MySuperClass {
    
    @Override
    public void sayHello() {
        System.out.println("Hey!");
    }
}
```

Now, the `sayHello` method will print either `Hello, there!` or `Hey!` to the console depending on the calling class.

```java
MySuperClass superClass = new MySuperClass();
MySubClass subClass = new MySubClass();

superClass.sayHello();   // prints Hello, there!
subClass.sayHello();     // prints Hey!
```

### Referencing the Parent

We can access methods, constructors, and variables \(depending on their visibilities\) of the parent class from the child class. All we need to do is use the super keyword. Consider the example from last section.

```java
/*
 * Parent class.
 */
public class MySuperClass {
    public void sayHello() {
        System.out.println("Hello, there!");
    }
}

/*
 * Child class.
 */
public class MySubClass extends MySuperClass {

    @Override
    public void sayHello() {
        System.out.println("Hey!");
    }
}
```

If we want to specifically access the `sayHello` method of the parent class, we use the `super` keyword.

```java
super.sayHello();    // calls the sayHello method of MySuperClass
```

Let's take a look at how this might work in practice.

{% embed url="https://www.youtube.com/watch?v=4tQEsDZrJJo&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

We need to revisit constructors for a minute, since we can also call the constructors of parent classes \(there might be some setup required in the parent class\) by using the `super` keyword.

```java
super();    // pass in arguments to super() like we would for any other constructor
```

I omitted this in our initial discussion of constructors because we first needed to gain an understanding of inheritance and class hierarchies. You'll also get a look at another use of the `this` keyword.

{% embed url="https://www.youtube.com/watch?v=eKbQYL2EswQ&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

{% embed url="https://www.youtube.com/watch?v=n3oaB-R1Lx4&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

Note that calling `super` needs to take place as the first line in the child constructor.

```java
// assume we've already written the Vehicle class

public class Bus extends Vehicle {
   public Bus(int wheels, int capacity) {
      super(wheels, capacity);   // calls the parent constructor
      
      // child-specific setup
   }
}
```

As we've seen, there are certain fields in parent classes that are not inherited by the parent class. Typically, these are private methods or instance variables. Remember the getter and setter methods we looked at a couple sections back? Well, this is their time to shine.

{% embed url="https://www.youtube.com/watch?v=0HE-BU1h\_E4&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

Getter and setter methods are public, and therefore accessible. We can use these to access private data in not only parent classes, but any class that defines them.

### Referencing the Child

While it is often only used for clarity, the `this` reference specifies that the method \(or constructor or variable\) that we are referring to is declared and defined in the class from which we're calling it \(i.e., _this_ class\).

```java
public class MyClass {
    private int x;

    public MyClass() {
        this(-1);
    }

    public MyClass(int x) {
        this.x = x;
    }
}
```

There are a couple examples we'll need to look at here. The simplest is the variable assignment in the second constructor \(yes, classes can have more than one constructor\).

```java
this.x = x;    // assign x value into this.x value

// x is the parameter of the constructor, whereas this.x
// is the instance variable defined at the class level
```

The `this` reference is to clarify to the constructor that the value stored in the variable `x` \(the one within the scope of the constructor\) is being assigned the variable `x` \(declared at the class level\). The this reference implies that it is an instance member.

The next example is the call to `this` as a method \(well, really as a constructor\). What we're doing here is calling another constructor of _this_ class and passing in the argument `-1`. Just like `super`, calling other constructors in this manner must take place on the first line in another constructor.

```java
this(-1);    // call constructor of this class, passing in -1 as argument
```

## Polymorphism

Polymorphism is a powerful concept in Java that allows us to manipulate many different objects \(provided they share a base implementation\) in one program.

{% embed url="https://www.youtube.com/watch?v=wnX\_nFnvKQU&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

We can write a singlet block of code, rather than blocks of code for each object we need to support. Consider the follow structure.

```java
public class Question {
    // base implementation for Question

    public void askQuestion() {
        // details here
    }
}

public class MultipleChoice extends Question {
    // extended implementation for MultipleChoice

    public void askQuestion() {
        // details here
    }
}

public class FillInTheBlank extends Question {
    // extended implementation for FillInTheBlank

    public void askQuestion() {
        // details here
    }
}
```

Each class is a `Question` \(by extension\) and each class has its own implementation of `askQuestion`. If we need to manipulate objects of each of these classes, we can do so in a single setting without having to write custom code for `Question`, `MultipleChoice`, and `FillInTheBlank`.

```java
public class Tester {
    public boolean isCorrect(Question q) {
        q.askQuestion();

        // get answer from user and check if it is right

        // return true or false
    }
}
```

The important part here is that `isCorrect` accepts a `Question` object as input, but we can pass in any of our `Question` classes \(`Question`, `MultipleChoice`, or `FillInTheBlank`\). Java will determine what _type_ of object `q` is and direct the method call appropriately.

```java
Question q1 = new Question();
boolean b1 = isCorrect(q1);

Question q1 = new MultipleChoice();
boolean b2 = isCorrect(q2);
```

In this case, Java will figure out that it should call the `askQuestion` method of the `Question` class for `q1` and the `askQuestion` method of the `MultipleChoice` class for `q2`.

{% embed url="https://www.youtube.com/watch?v=cUh3Q9l3Q-0&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

### Object Casting

We've gone over casting, but it works a little differently with objects. Upcasts occur automatically, while we, the programmers, must downcast manually. Upcasting outlines two things for us:

1. The methods that are available, which is governed by the variable type.
2. The version of the method that is called, which is governed by the object type.

{% embed url="https://www.youtube.com/watch?v=Qpz2MA4KE9U&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

Downcasting might like a little chaotic at first glance. Suppose we have two classes: `Employee` and `Teacher`. In the `Employee` class, there is just one method: `work`. The `Teacher` class inherits this method, but also provides one of its own: `teach`.

```java
Employee patrick = new Employee();
Employee susan = new Teacher();        // Teacher extends from Employee

/*
 * The variable type of susan is Employee, so susan only has access to
 * methods that were defined in the Employee class. So, how can we call
 * the teach method with the susan object?
 */

((Teacher) susan).teach();  // cast susan to a Teacher
```

