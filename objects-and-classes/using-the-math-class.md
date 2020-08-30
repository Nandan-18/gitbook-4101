# Using the Math Class

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 3.5
{% endhint %}

## Functions and Constants

The built-in `Math` class provides a host of useful methods and constants for mathematical equations. To use these methods or fields, you need to reference the name of the class followed by the method or constant.

There are only two constants: 𝜋 and _e_.

* `Math.PI`
* `Math.E`

There are many more methods. I'll highlight some of the more common ones. Remember, though, the `Math` class is a little bit different than some of the others we've seen.

The `String` methods all required a `String` object on which to call the method.

```java
String s = "example";
int lenght = s.length();    // note the method is called on the object
```

Since the Math methods are static, there is no object. The methods are called on the class itself, and operator on values provided as parameters.

```java
Math.abs(-5.5);    // note the lack of any Math object, just the class
```

There are many methods, so I'll highlight some of the more common ones.

| **Method** | **Description** | **Usage** |
| :--- | :--- | :--- |
| `Math.abs` | Computes the absolute value of a number. | `Math.abs(-5.5);    // 5.5` |
| `Math.cbrt` | Computes the cube root of a value. | `Math.cbrt(125);    // 5.0` |
| `Math.ceil` | Forcibly rounds a value up. | `Math.ceil(6.1);    // 7.0` |
| `Math.floor` | Forcibly rounds a value down. | `Math.floor(7.9);   // 7.0` |
| `Math.hypot` | Computes the hypotenuse given two side lengths. | `Math.hypot(3, 4);  // 5.0` |
| `Math.max` | Determines the maximum of two values. | `Math.max(1, 2);    // 2` |
| `Math.min` | Determines the minimum of two values. | `Math.min(1, 2);    // 1` |
| `Math.pow` | Computes the value of one number raised to the power of another. | `Math.pow(2, 3);    // 8.0` |
| `Math.random` | Generates a random number in the range \[0.0, 1.0\). | `Math.random();     // 0.58961...` |
| `Math.round` | Rounds a number up or down. | `Math.round(4.3);   // 4` |
| `Math.sqrt` | Computes the square root of a value. | `Math.sqrt(25);     // 5.0` |

Check out the [full documentation](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html) of the `Math` class for all available methods. This video walks through a few of the more popular ones.

{% embed url="https://www.youtube.com/watch?v=IGVOjx9ufMw&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

And as a bonus, here's a video on generating random numbers using the Math class. As odd as it might sounds, random numbers are a pretty popular choice of questions on AP exams.

{% embed url="https://www.youtube.com/watch?v=Q9LIxVENfLU&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

And it might come in handy for an assignment or two, as well. Hint, hint...

