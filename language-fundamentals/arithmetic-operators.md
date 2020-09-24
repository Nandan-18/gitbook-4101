# Arithmetic Operators

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 3.3 and 3.4
{% endhint %}

## Simple Math

There are five simple arithmetic operators, most of which should be familiar to you.

| **Operator** | **Description** |
| :--- | :--- |
| `+` | Addition operator. |
| `-` | Subtraction operator. |
| `*` | Multiplication operator. |
| `/` | Division operator. |
| `%` | Integer remainder operator. |

{% embed url="https://youtu.be/cy5f8VGcMDg" %}

The addition operator works exactly as you might expect it to. It computes the sum of two numbers.

```java
int a = 1;
int b = 2;
int c = a + b;    // sum of a and b is computed, stored in c
```

Subtraction is equally straightforward.

```java
int a = 3;
int b = 2;
int c = a - b;    // difference between a and b is computed, and stored in c
```

Multiplication, too, is as expected. No surprises here.

```java
int a = 2;
int b = 3;
int c = a * b;    // product of a and b is computed, stored in c
```

The division operator behaves a littler differently than you might expect, depending on the operands \(or more specifically, their data types\). If either operand is a floating-point number, then the division operator performs floating-point division.

```java
double a = 3.0;
double b = 2.0;
double c = a / b;    // 1.5 is stored in c
```

However, if both operands are integers, then the division operator performs integer division. Effectively, this means any fractional component in the quotient is discarded.

```java
int a = 3;
int b = 2;
int c = a / b;    // 1 is stored in c
```

Since two integers are divided, the fraction \(0.5\) is truncated off the result. Even if you stored the result in a `double`, you still wouldn't get the fractional part of the quotient.

```java
int a = 3;
int b = 2;
double c = a / b;    // 1.0 is stored in c
```

Let's take a closer look at this, as it can easily lead a novice programmer astray.

{% embed url="https://youtu.be/crGd6jKoII8" %}

Division by zero also behaves differently depending on the data types of the operands.

{% code title="FloatingDivision.java" %}
```java
public class FloatingDivision {
    public static void main(String[] args) {
        System.out.println(1.0 / 0.0);    // floating-point division by zero
    }
}
```
{% endcode %}

Floating-point division by zero produces a value of `Infinity`.

```text
$ java FloatingPoint
Infinity
```

On the other hand, integer division by zero produces a runtime exception.

{% code title="IntegerDivision.java" %}
```java
public class IntegerDivision {
    public static void main(String[] args) {
        System.out.println(1 / 0);    // integer division by zero
    }
}
```
{% endcode %}

This code will compile just fine, but will crash when you run the program.

```text
$ java IntegerDivision
Exception in thread "main" java.lang.ArithmeticException: / by zero
    at IntegerDivision.main(IntegerDivision.java:3)
```

This is your first encounter with an exception. You've seen compile-time errors \(i.e., typographical errors that prevent the program from compiling\). A runtime error is a problem the code encounters while running.

## Shortcuts

Shortcut operators combine the assignment operator \(`=`\) with any of the simple arithmetic operators \(`+`, `-`, `*`, `/`, or `%`\).

```java
int a = 1;
int b = 2;

a += b;    // equivalent to: a = a + b (which is 3)
a -= b;    // equivalent to: a = a - b (which is 1)
a *= b;    // equivalent to: a = a * b (which is 2)
a /= b;    // equivalent to: a = a / b (which is 1)
a %= b;    // equivalent to: a = a % b (which is 1)
```

As a matter of preference, some developers choose to be explicit while others opt for the shortcut assignments. One isn't more or less correct than the other, but it makes sense to be consistent in your code.

## Increment and Decrement

Increasing or decreasing the value of a variable by one is a very common task in many programs. For that reason, Java provides a shortcut way of doing exactly that. The increment operator is `++` and the decrement operator is `--`.

In postfix notation, the operator comes after the variable.

```java
int x = 6;
x++;          // x is now 7
x--;          // x is 6 again
```

Alternatively, you might see prefix notation, where the operator comes before the variable.

```java
int x = 6;
++x;          // x is now 7
--x;          // x is 6 again
```

They seemingly do the same thing, and that's true. But it's a little more complicated. When the variables are simultaneously involved in other operations, the timing of when the variable is incremented or decremented becomes a factor.

### Prefix v. Postfix

Using postfix notation, the variable is incremented or decremented after the rest of the operation concludes.

{% code title="Postfix.java" %}
```java
public class Postfix {
    public static void main(String[] args) {
        int x = 1;
        
        System.out.println(x);
        System.out.println(x++);
        System.out.println(x);
    }
}
```
{% endcode %}

If you compile and run this program, you'll see the order in which the print statements and incrementing take place. In this example, the value of `x` is printed to the console before its value is incremented from `1` to `2`.

```text
$ java Postfix
1
1
2
```

On the other hand, the variable is incremented or decremented before the operation when using prefix notation.

{% code title="Prefix.java" %}
```java
public class Prefix {
    public static void main(String[] args) {
        int x = 1;
        
        System.out.println(x);
        System.out.println(++x);
        System.out.println(x);
    }
}
```
{% endcode %}

Now, try compiling and running this program. See the difference in when the value of `x` is changed? It is incremented from `1` to `2`, and then it is printed to the console.

```text
$ java Prefix
1
2
2
```

Make sure you understand why each of these examples behaves in the way that they do.

## Conversions and Casting

There are several instances in which values are implicitly or explicitly converted from one data type to another. When dealing with binary operators \(i.e., any of the simple arithmetic operators\), the operands may or may not be implicitly converted.

* If either operand is a `double`, the other one is converted to a `double`.
* If either operand is a `float`, the other one is converted to a `float`.
* If either operand is a `long`, the other one is converted to a `long`.
* Otherwise, both operands are converted to `int`s.

These implicit conversions do not affect the contents of any variables. The operands are converted only for the duration of the arithmetic operations.

### Casting

In other circumstances, you may need to explicitly convert values to other data types. This is called casting. Suppose you wanted to truncate a number \(i.e., retain only the whole number\).

```java
double decimalValue = 7.654;
int truncatedValue = (int) value;
```

`(int)` tells the compiler to convert `decimalValue` to an `int` before storing it in `truncatedValue`. Now, the final result will be `7`.

You can go in the other direction, too, in the event you wanted to treat an integer value as a real number.

```java
int integerValue = 3;
double decimalValue = (double) integerValue;
```

`integerValue`, of course, doesn't have a decimal component; however, the `(double)` cast imposes one. After this conversion, `decimalValue` will be `3.0`.

### Possible Dangers

You need to be careful when casting, though. Since some data types cannot accommodate the same size or degree of precision, there is the potential for information loss. These are all safe conversions without the risk for any information loss. They are called widening conversions.

* `byte` ⟶ `short`, `int`, `long`, `float`, or `double`
* `short` ⟶ `int`, `long`, `float`, or `double`
* `char` ⟶ `int`, `long`, `float`, or `double`
* `int` ⟶ `long`, `float`, or `double`
* `long` ⟶ `float` or `double`
* `float` ⟶ `double`

These, however, are not. They carry the very real risk for information loss. They're called narrowing conversions.

* `short` ⟶ `byte` or `char`
* `char` ⟶ `byte` or `short`
* `int` ⟶ `byte`, `short`, or `char`
* `long` ⟶ `byte`, `short`, `char`, or `int`
* `float` ⟶ `byte`, `short`, `char`, `int`, or `long`
* `double` ⟶ `byte`, `short`, `char`, `int`, `long`, or `float`

Go review the storage size and value ranges of the primitive data types if you're unsure why some casts are safe and some are unsafe.

{% embed url="https://www.youtube.com/watch?v=hTShKthSARE&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## Methods and Constants

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
| `Math.abs` | Computes the absolute value of a number. | `Math.abs(-5.5);   // 5.5` |
| `Math.cbrt` | Computes the cube root of a value. | `Math.cbrt(125);   // 5.0` |
| `Math.ceil` | Forcibly rounds a value up. | `Math.ceil(6.1);   // 7.0` |
| `Math.floor` | Forcibly rounds a value down. | `Math.floor(7.9);  // 7.0` |
| `Math.hypot` | Computes the hypotenuse given two side lengths. | `Math.hypot(3, 4); // 5.0` |
| `Math.max` | Determines the maximum of two values. | `Math.max(1, 2);   // 2` |
| `Math.min` | Determines the minimum of two values. | `Math.min(1, 2);   // 1` |
| `Math.pow` | Computes the value of one number raised to the power of another. | `Math.pow(2, 3);   // 8.0` |
| `Math.random` | Generates a random number in the range \[0.0, 1.0\). | `Math.random();    // 0.58961...` |
| `Math.round` | Rounds a number up or down. | `Math.round(4.3);  // 4` |
| `Math.sqrt` | Computes the square root of a value. | `Math.sqrt(25);    // 5.0` |

Check out the [full documentation](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Math.html) of the `Math` class for all available methods. This video walks through a few of the more popular ones.

{% embed url="https://www.youtube.com/watch?v=IGVOjx9ufMw&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

And as a bonus, here's a video on generating random numbers using the Math class. As odd as it might sounds, random numbers are a pretty popular choice of questions on AP exams.

{% embed url="https://www.youtube.com/watch?v=Q9LIxVENfLU&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

And it might come in handy for an assignment or two, as well. Hint, hint...

