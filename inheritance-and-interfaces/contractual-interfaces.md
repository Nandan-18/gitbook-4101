# Contractual Interfaces

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 6.1 and 6.2
{% endhint %}

## What is an Interface?

An interface defines a contract between classes that may choose to implement it. It declares behaviors that implementing classes must define in their own terms. This allows users \(i.e., programmers\) of the class to write code with confidence that the class will support certain behaviors out-of-the-box.

{% embed url="https://www.youtube.com/watch?v=xOcEuIR4pNU&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

Let's take a look at a popular interface called `Measurable`.

```java
public interface Measurable {
    double getMeasure();      // methods are automatically public
}
```

Any class that _implements_ the `Measurable` interface needs to implement the `getMeasure` method.

```java
public class BankAccount implements Measurable {
    public double getMeasure() {
        return balance;
    }
}
```

Classes can implement more than one interface, but can only extend a single class \(an important difference between abstract classes and interfaces\).

Interfaces can also be used as data types, where they represent any class that implements it \(in a way, this is like polymorphism\).

```java
public double getSum(Measureable[] objs) {
    double sum = 0;

    for (Measurable obj : objs) {
        sum = sum + obj.getMeasure();
    }

    return sum;
}
```

### The `Comparable` Interface

`Comparable` is a built-in interface in Java that defines a single method: `compareTo`. The `compareTo` method will compare two objects of the same class and return a positive value, 0, or a negative value. This corresponds to whether the first object is greater than, equal to, or less than the second object, respectively. We've seen this used with `String`s in earlier units.

Our job, as programmers and implementers of the `Comparable` interface, is to define what it means for an object to be greater than, equal to, or less than another object. For something like a `Card` class, we might look to the rank \(and potentially the suit, depending on the game\) to determine how to order these objects.

Once we've implemented the `Comparable` interface, we can automatically sort lists of the implementing class \(in the case, the `Card` class\).

```java
public class Card implements Comparable<Card> {
    // note the type being compared in the angled brackets above
    
    // some Card class implementation details omitted

    @Override
    public int compareTo(Card card) {
        if (this.getRank() > card.getRank()) {
            return 1;
        } else if (this.getRank() < card.getRank()) {
            return -1;
        } else {
            return 0;
        }
    }
}
```

`Card`s can now be sorted \(perhaps in a `Hand`\), since we've defined the manner in which ordering should take place.

