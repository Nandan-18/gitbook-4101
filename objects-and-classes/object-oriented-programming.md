# Object-Oriented Programming

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 4.1 and 4.2
{% endhint %}

## Classes

Object-oriented programming \(informally known as OOP\) is one of the most popular programming paradigms in use today, and Java is an inherently object-oriented language. While you've been able to create some pretty cool programs using a strictly procedural approach, you'll need to understand what object-oriented programming is to go further.

An object-oriented program is composed of objects, which store data and provide specific behaviors. The behavior, itself, is exposed to users, while the implementation details remain hidden. A class is the template or blueprint from which objects are made. There are thousands of Ford Focuses on the road today, each of which was manufactured using the same design template. Sure, there are differences in colors and trim packages, but they all look and behave alike—they can drive, go in reverse, turn left or right, just to name a few. If the design template used to produce the Ford Focus is the class, then each individual vehicle is an instance or object of that class.

The standard Java library provides thousands of built-in classes to help you create diverse programs. You've already used a few of these, such as the `String` and `Scanner` classes. If you need something not provided in the library, you can write your own classes to represent objects specific to your program.

### Encapsulation

Sometimes called information hiding, the concept of encapsulation is a key component to creating classes and using objects. It is the process by which programmers combine data and behavior in a single class, but hide the implementation details from the users of that class. This is often referred to as black box behavior, which means that users know what an object can do but not how it does it.

The data members of an object typically are called instance fields \(or variables\). These types of variables are declared at the class level, and are accessible to the entire class. The behavior of a class is defined in its methods. If you remember the past couple problem sets, a method is a logical unit within a class that is tasked with performing a specific function. Methods use and often modify the values of the instance fields.

## Objects

There are three key characteristics of an object.

* The behavior of an object—what can you do with this object, and what methods can you apply to it?
* The state of an object—how does the object react when you invoke those methods?
* The identity of an object—how is the object distinguished from others that may have the same behavior and state?

Remember, objects are instances of a single class. Each object supports the same behavior defined by the methods you can call on it. The state of an object is represented by the values of its instance fields. However, even if two objects have the same behavior and state, their identities are different.

### Identifying Classes

Before you start writing code, it is important to plan your approach. Analyze the problem at hand. What classes should you create? What methods should you write? Suppose you wanted to develop an order processing application. If you analyze everything that might go into such a system, you can more clearly define your program.

* An order can shipped to a shipping address.
* A product can be added or removed from an order.
* A payment can be applied to an order.
* An account can create or cancel an order.

This certainly isn't a comprehensive system, but it's a good start \(and a good example\). The nouns in the analysis are underlined, and the verbs are italicized. As a general rule of thumb, the nouns become your classes and the verbs become methods in those classes. It's a guiding principle, and experience helps you to decide which nouns and verbs are important enough to become classes and methods.

This program might use the following classes.

* `Order`
* `ShippingAddress`
* `Product`
* `Payment`
* `Account`

The following methods might be defined in these classes.

* A `shipOrder` method might be defined in the `Order` class, which would require some input—the `ShippingAddress`.
* `add` and `remove` methods might be defined in the `Order` class, which would require some input—the `Product` to be added or removed.
* An `applyPayment` method might be defined in the `Account` class, which would require some input—the `Payment` to be applied.
* `create` and `cancel` methods might be defined in the `Account` class. The `cancel` method would require some input—the `Order` to be canceled.

## Relationships

There are three primary class relationships.

* Dependence \("uses-a"\)
* Aggregation \("has-a"\)
* Inheritance \("is-a"\)

### Dependence

If a class uses the methods of another class, accepts as a parameter or returns the objects of another class, or otherwise manipulates the objects of another class, then the first class is said to be dependent on the second. Using the earlier order processing example, there would be a dependency relationship between the `Order` and `Product` classes because the `Order` class references the `Product` class in its `add` and `remove` methods \(as parameters\).

It's good practice to limit the number of dependencies in your code. The more you have, the more likely it becomes that a change in one class might potentially introduce bugs into another class. The process of removing unnecessary dependencies is called decoupling.

### Aggregation

This is a little easier to understand. If an object of one class contains objects of another, then there is an aggregation relationship. The `Order` class has an `add` method, which adds `Product` objects to the order. While the `add` method implies a dependency, this means also that the `Order` object contains one or more `Product` objects \(i.e., it stores them\). This creates an aggregation relationship, too.

### Inheritance

This is something you'll learn much more about in the [Inheritance and Interfaces](https://apcs.gitbook.io/java/inheritance-and-interfaces/superclasses-and-subclasses) unit. For now, focus on the broad strokes. This type of relationship is one in which a more specialized class derives some of its base functionality from a more general one. This is a powerful characteristic of Java.

Remember, the `Order` class? What if you needed to create a special type of order, called a `RushOrder`? It would do a lot of the same things that the `Order` class does, but would add some specialized behavior of its own. It doesn't make a lot of sense to reimplement the `Order` class in its entirety. Instead, the `RushOrder` class would extend the `Order` class, thereby inheriting the methods responsible for adding `Product`s and billing `Account`s without re-writing the code.

## Using Objects

We've seen the use of the `new` operator, as well as a few different class constructors.

```java
String word = new String("word");
Scanner input = new Scanner(System.in);
```

We haven't really gone too much into detail about what these lines of code do. When we use a constructor of a class \(in this case, the `String` and `Scanner` classes\), we are creating a new instance of that class. Remember, the class itself is the blueprint, whereas instances of that class are objects built using that blueprint.

`word` and `input` in the example above are instances or objects of the `String` and `Scanner` classes, respectively. But what can we do with these objects after we've created them?

The underlying classes will have defined variables and methods that we can reference and use. We'll learn all about how this works in the [Writing Classes](writing-classes.md) section. For now, let's focus on the behaviors available to us through these objects and how we can use them.

### Calling Methods

Objects have a set of actions or behaviors available to them called methods. These methods are defined in the class, and programmers can utilize their functionality. The term programmers use for this is call \(i.e., we call the method\).

Generally, method calls assume the following format.

```java
objectName.methodName();

objectName.methodName(parameterName);

int result = objectName.methodName(firstParameter, secondParameter);
```

Whenever you call a method, you use the name of the object, a dot, and then the name of a method defined in the class. Some methods take input \(called parameters\), and others produce a result \(called a return value\).

We've already seen plenty of examples in the `String` and `Scanner` classes, and we'll see quite a few more in the next few sections.

