# Abstract and Final Classes

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 5.1 and 5.2
{% endhint %}

## Abstract Classes

An abstract class is a special type of class that outlines common behavior that all subclasses will have, as well as functionality that subclasses must implement. An abstract class cannot be instantiated, which means you cannot create an instance of an abstract class. You can, though, create an instance of a child class that extends an abstract class.

{% embed url="https://www.youtube.com/watch?v=\_KvtWtBnsqE&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

Note the usage of the `abstract` keyword when defining the class.

```java
public abstract class Shape {
    public void setColor(Color color) {
        this.color = color;
    }

    abstract double getArea();
    abstract double getPerimeter();
}
```

Now, any class that extends the `Shape` class will inherit certain built-in behavior \(i.e., setting the color of the shape\). Additionally, all subclasses _must_ implement the `getArea` and `getPerimeter` methods.

As we discussed earlier, abstract classes _cannot_ be instantiated. To clarify, programmers _cannot_ do this:

```java
Shape s = new Shape();   // this will not compile
```

However, a child class of the `Shape` class can be instantiated.

```java
public class Square extends Shape {
    private double side;

    public Square(double side) {
        this.side = side;
    }

    public double getArea() {
        return side * side;
    }

    public double getPerimeter() {
        return side * 4;
    }
}
```

Now, we can instantiate the `Square` class like so:

```java
Square sq = new Square(10);
```

## Final Classes

A final class is one where a special `final` modifier has been applied to its definition. It prevents another class from extending, and thereby modifying, the original class. If you want to prevent another programmer from extending your class, you can add the `final` keyword.

```java
public final class MyFinalClass {
    // implementation details here
    
    // this class cannot be extended
}
```

The built-in `String` class is a `final` class, and therefore cannot be subclassed.

