# Implementing Methods

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 4.3 through 4.7
{% endhint %}

## Black Boxes

A method is a named set of instructions that can be referenced \(i.e., called\) from your program. If you're writing a grade processing system, surely your program will need to be able to calculate a student's grade point average. This might take a few lines of code.

```text
1. retrieve numeric grade (0-100) for each course
2. convert numeric grades to grade points (0-4)
2. compute the sum of the grade points
3. retrieve credit hours for each course
4. compute the sum of the credit hours
5. divide total grade points by total credit hours
```

This is a fixed process. It doesn't matter whose account you are accessing, the process the program needs to take to compute that student's GPA is the same.

```java
public double calculateGpa() {
    // do all of the things you need to do to
    // calculate a student's grade point average
}
```

I've left out the details of how to do this in Java on purpose. And that's because it doesn't matter. If I am using this system, I don't really care how the program computes a student's GPA. I only care that it does so correctly.

Programmers refer to methods as being black boxes, and this is exactly what they mean. There are a number of ways in which you might've implemented this method. As long as your implementation is correct and reasonably efficient, the users of your class don't need to know the details of what's going on under the hood.

### Library Methods

Consider the `println` method, which is built into the language.

```java
System.out.println("Hello, world!");
```

You've used this method a hundred times. It's calling the `println` method, which is defined in the standard Java library class `PrintStream`.

```java
public void println(String x) {
    synchronized (this) {
        print(x);
        newLine();
    }
}
```

There's a lot going on here that you aren't yet going to understand. Focus on the pieces that \(hopefully\) make a little bit of sense. Inside of the `println` method, there are two additional method calls: one to `print` and one to `newLine`. These secondary methods, in turn, make several calls to a set of tertiary methods.

This is all done to achieve what turns out to be the fairly complicated task of printing a line of text to the console. Fortunately for you, as a user of the standard library, you can treat these methods as black boxes. You don't need to concern yourself with how the `println` method works. You only care that it does what it claims to do.

Obviously, as we shift gears from using methods to writing methods, we'll need to care a great deal about how things work under the hood.

## Methods

First and foremost, your methods should perform a single task. Long, unwieldy methods are difficult to write, harder to debug, and impossible to maintain. Keep it simple, and break tasks into multiple methods as needed.

Think about the logic behind your programs. Are there similar segments of code you find yourself writing more than once? That's a perfect example of code that should be refactored into a method. Now, instead of duplicated that code, you can call your method.

{% embed url="https://www.youtube.com/watch?v=nFFEqTKFBws&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

Consider the following program that is designed to prompt a user for a number between 1 and 10 and perform a countdown starting at the number the user entered.

{% code title="Countdown.java" %}
```java
import java.util.Scanner;

public class Countdown {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        int start = -1;
        while (start < 1 || start > 10) {
            System.out.print("Enter a number between 1 and 10: ");
            start = in.nextInt();
        }
        
        for (int i = start; i > 0; i--) {
            System.out.println(i);
        }
        
        System.out.println("Blast off!");
        in.close();
    }
}
```
{% endcode %}

There are two distinct sections of this program. The first prompts the user for a value in a specific range, and the second uses that value to perform a countdown. This might be a good example for the use of methods.

{% code title="Countdown.java" %}
```java
import java.util.Scanner;

public class Countdown {
    public int getNumberInRange(int low, int high) {
        System.out.printf("Enter a number between %d and %d: ", low, high);
        int value = in.nextInt();
        
        while (value < low || value > high) {
            System.out.printf("Enter a number between %d and %d: ", low, high);
            value = in.nextInt();
        }
        
        return value;
    }
    
    public void count(int start) {
        for (int i = start; i > 0; i--) {
            System.out.println(i);
        }
        System.out.println("Blast off!");
    }
}
```
{% endcode %}

It's a few more lines of code, but it's more dynamic and scalable. You can execute this code with whatever range you want, and you never have to change you code. It will always work the same way.

You can create your own black boxes. It doesn't matter how the code works, only that it does. If you call `getNumberInRange`, your code will prompt the user continually until he or she enters a number in that provided range. And if you call `count`, your code will perform a countdown starting at the number you provide.

### Method Signatures

Java uses something called a method signature to determine the uniqueness of a method. You cannot duplicate methods within a single class.

```java
methodName(dataType parameter1, dataType parameter2, ...)
```

Methods contain access modifiers and return types, too, but these aren't part of the signature.

```java
accessModifier dataType methodName(dataType parameter1, dataType parameter2, ...)
```

You've already seen some examples of methods with different return types and parameter lists, even if you weren't sure what those things meant.

```java
public int getNumberInRange(int low, int high) { ... }

public void count(int start) { ... }
```

The method signatures here are `getNumberInRange(int, int)` and `count(int)`, respectively.

### Parameters

The purpose of a parameter list is to allow your method to accept certain input values that will help it to do its job. For example, the `count` method is supposed to perform a countdown sequence. It needs to know where to start that sequence, and it gets this information passed to it as an argument. This allows the method to dynamically respond to different inputs.

```java
public void count(int start) {    // one parameter, an int called start
    // you can reference the start variable in the method just
    // like you would any other local variable you declared
}
```

Like any variable, a parameter needs a specific data type and a name. When you use the method, you need to provide a value whose data type matches. The name does not need to match, but the method will always reference the variable using its own parameter name.

Many of the built-in methods you've used have accepted parameters.

```java
String str = "hello";
String sub = str.substring(1, 3);    // sub is "el"
```

The `substring` method accepts two arguments, a starting index and an ending index. You need to provide these, and the method uses them to produce the desired substring.

Interestingly, there are actually three parameters in play for the above call to the substring method. There are two explicit parameters—the beginning and ending indices. But there is also an implicit parameter, which is the object on which the method is called. In this case, that is the `str` object.

#### Call-by-Value v. Call-by-Reference

This is something you'll see in just about every programming language you learn. Some languages are call-by-value, while others are call-by-reference. These terms are referring to calling methods, whether the arguments provided to those methods are values or references.

Call-by-value means that methods receive copies of the values of a particular variable, while call-by-reference means that methods receive the memory address of a particular variable. Methods can modify the values of variables that are passed by reference, but the original value of variables passed by value cannot be modified.

Java uses call-by-value, meaning your methods receive copies of variables. You can modify the values of these copies without impacting the values of the originals. Consider the following method.

```java
public void triple(int x) {
    x = x * 3;
}
```

And now, consider its usage.

```java
int number = 5;
triple(number);
```

You might think that `number` is going to be 15. However, if you print its value after the call to `triple`, you'll see it is unchanged.

```java
System.out.println(value);    // prints 5
```

The `triple` method receives a copy of the `number` variable. It is this copy that is tripled within the scope of the method. At the conclusion of the method, that value is discarded and the `number` variable is unaffected.

This is always the case with primitive data types. Reference types \(i.e., objects\) work a little differently. It is possible to write methods that modify objects passed in as parameters. However, this does not mean that Java uses call-by-reference for object types. It uses call-by-value for all types.

#### Overloading

You can overload your methods by writing methods whose names are the same, but whose signatures \(by nature of their parameter lists\) are different. Remember the `println` method? That is overloaded in the `PrintStream` class.

```java
println()
println(boolean x)
println(char x)
println(int x)
println(float x)
println(double x)
println(String x)
```

There are even more than this, but you get the point. There are many `println` methods, each designed to accept to a different type of argument. The JVM figures out which of these methods to invoke based on the data type of the argument passed to it.

{% embed url="https://www.youtube.com/watch?v=Egzz2I3iseg&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

### Return Types

If parameters provide the means by which methods accept input, then a return statement is how they produce an output. Java keeps track of the caller of a method, and return statements direct output back to that caller.

Like variables and parameters before it, methods, too, have a data type. It's the data type of the information it will return to the caller. It can be any of the primitive data types, a built-in reference type \(i.e., an object\), or a class you wrote yourself \(also a reference type, also an object\).

```java
public int getNumberInRange(int low, int high)
```

The `getNumberInRange` method accepts two parameters, as you've already seen. Additionally, it returns a value. The return type is specified right before the name of the method: `int`.

```java
public int getNumberInRange(int low, int high) {
    System.out.printf("Enter a number between %d and %d: ", low, high);
    int value = in.nextInt();
        
    while (value < low || value > high) {
        System.out.printf("Enter a number between %d and %d: ", low, high);
        value = in.nextInt();
    }
        
    return value;    // this is the return statement
}
```

The return statement sends value back to the caller of the method. You can use this to assign a value to a variable based on the result of calling a method.

#### Guaranteeing a Return

When you specify a return type, you need to guarantee that your code will always return something. No matter what. Consider the following code snippet.

```java
public int getNumber() {
    int number = /* get from user input */;

    if (number % 2 == 0) {
        return number / 2;
    } else {
        if (number % 3 == 0) {
            return number / 3;
        }
    }
}
```

At first glance, this code appears fine. It will return the number divided by either 2 or 3. However, if the number isn't divisible by these values, then the code never hits a return statement. There needs to be a return statement for every possible path the code can take.

```java
public int getNumber() {
    int number = /* get from user input */;

    if (number % 2 == 0) {
        return number / 2;
    } else {
        if (number % 3 == 0) {
            return number / 3;
        }
    }

    return number;    // now the code will compile
}
```

If your method is not designed to return a value, then you should set the return type to `void`.

```java
public void doesNotReturnAnything() {
    // this code does something
    // but it doesn't return anything
}
```

## Constructors

We've seen constructors already, but we're going to going through them again. They're responsible for building each of the objects we use in our programs, so they're pretty important.

{% embed url="https://www.youtube.com/watch?v=KWNxnC6ocS0&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

A constructor is a special type of method. It takes the same name as your class.

{% code title="Student.java" %}
```java
public class Student {    // this is the class
    public Student() {    // this is the constructor
    
    }
}
```
{% endcode %}

Inside your constructor is where you'll do all of the setup for your object. This typically includes providing default values for your instance variables.

{% code title="Student.java" %}
```java
public class Student {
    private final long id;
    private double gpa;
    private String name;
    
    /*
     * Constructs an instance of the Student class.
     */
    public Student(long id, double gpa, String name) {
        this.id = id;
        this.gpa = gpa;
        this.name = name;
    }
}
```
{% endcode %}

### Multiple Constructors

You might need to construct an object differently under different circumstances. Using the `Student` class as an example, let's consider incoming freshmen and transfers. An incoming won't have a GPA yet, but a transfer will have a GPA from a previous school. Schools might computer GPAs differently, so we'd need to account for that. We can do so by writing separate constructors for each case.

{% code title="Student.java" %}
```java
public class Student {
    private final long id;
    private double gpa;
    private String name;
    
    /*
     * Constructs an instance of the Student class for incoming freshman.
     */
    public Student(long id, String name) {
        this.id = id;
        this.gpa = 0.00;
        this.name = name;
    }
    
    /*
     * Constructs an instance of the student class for transfers.
     */
    public Student(long id, double previousGpa, String name) {
        this.id = id;
        this.gpa = /* compute GPA from previousGpa */;
        this.name = name;
    }
}
```
{% endcode %}

## Getters and Setters

Most of the classes you write will have a set of specialized instance methods called getters and setters. Sometimes other parts of your programs may need access to the instance variables of a certain class. To maintain encapsulation, you can provide this access under your terms.

{% embed url="https://www.youtube.com/watch?v=qVuYtdTHfA4&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

### Getters

A getter is responsible for retrieving the current value of an instance variable. It is referred to as an accessor method. It is up to you, as the programmer, to determine which instance variables reasonable require getters. It might be all of them, none of them, or some of them.

A getter method must be `public`, should have a return type that matches the data type of the instance variable, and fit the following format.

```java
public dataType getInstanceVariable() {
    return instanceVariable;
}
```

If you apply this concept to the `Student` class, your code might look like this.

{% code title="Student.java" %}
```java
public class Student {
    // some implementation details not shown

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

### Setters

A setter is responsible for assigning a value to an instance variable. This, of course, is first done in the constructor, but you might need to change this value later. Because a setter modifies the state of an object, it is called a mutator method. Again, it is up to you to decide which instance variables require setters.

For the `Student` class, it makes a lot of sense to update the value of a student's grade point average. And as rare as it may be, a student can legally change his or her name. However, the id cannot change \(hence the `final` modifier\). So, you don't need a setter for the id.

A setter method, too, must be `public`, it has no return type, and it follows the same convention as the getters.

```java
public void setInstanceVariable(dataType localVariable) {
    this.instanceVariable = localVariable;
}
```

The `void` keyword means this method does not return a value. If you applied this to the `Student` class, you'd have something like this.

{% code title="Student.java" %}
```java
public class Student {
    // some implementation details not shown

    public void setGpa(double gpa) {
        this.gpa = gpa;
    }

    public void setName(String name)  {
        this.name = name;
    }
}
```
{% endcode %}

I've chosen not to implement a `setId` method. A student's ID doesn't change once initially set in the constructor, so a setter is unnecessary.

## Private Methods

All of the methods you've used and written so far have been `public`. Sometimes, it makes sense to write `private` methods. Usually, a `private` method serves as a helper method to a `public` one. It's good practice to limit the public exposure of your classes.

Remember the `println` method? This is exposed through the public interface. Behind the scenes, though, the `println` method makes use of `private` helper methods that the user doesn't need to use directly \(or even know about\).

```java
private void doSomethingPrivate() {    // see the change in the access modifier?
    // this method is only visible (and therefore callable)
    // from within the class in which it is defined
}
```

`private` methods also give you the freedom to change \(or even drop\) the implementation from your code without the risk of affecting other classes in your program.

## Null Pointers

We've been dancing around this subject in a few sections already, and I can almost guarantee that we've all seen our program crash with a reference to a `NullPointerException`. We knew it was bad and we knew we messed up, but we didn't really know why.

`null` is a special reference type that means it points at nothing. Weird, right? Anything that isn't a primitive data type is an object type, and any object type can be `null`.

{% embed url="https://www.youtube.com/watch?v=7tuK9UgCSjs&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

It's really important that you get in the habit of writing defensive code. That means checking that an object explicitly isn't `null` before trying to use it.

{% page-ref page="../problem-sets/problem-set-8.md" %}

