# More on Operators

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapter 3.8
{% endhint %}

## **Operator Precendence**

Just like we learned in middle school, different operators carry different priorities in terms of when they are executed. Maybe you were taught PEMDAS or something similar. Java has a precedence for its operators, too, and it's not all that different from what we're already familiar with from math class.

| Precedence | Operator |
| :--- | :--- |
| Highest | `(parentheses)` |
|  | `!`  `++`  `--` |
|  | `(casting)` |
|  | `*` `/` `%` |
|  | `+` `-` |
|  | `<` `<=` `>` `>=` `==` `!=` |
|  | `&&` |
| Lowest | `||` |

Remember, there might be some weirdness when it comes to prefix and postfix incrementing and decrementing. Keep that in mind when analyzing operator precedence.

{% embed url="https://www.youtube.com/watch?v=gEJEDdambGc&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## **Short Circuit**

With your newfound knowledge of conditional statements, it's important to revisit relational and logical operators. At first glance, there are some behavioral oddities that you need to understand.

Java optimizes the evaluation of compound expressions, returning as soon as a definitive answer is reached. Do you remember how the `&&` and `||` operators work?

* `&&` returns `true` if _both_ sides of the expression evaluate to `true`.
* `||` returns `true` if _either_ side of the expression evaluates to `true`.

Because these expressions are evaluated left-to-right, Java doesn't always need to evaluate the entirety of an expression. At a certain point, it can short circuit and return the answer.

If the left side of an `&&` expression is `false`, then it doesn't matter what the right side is. The entire expression is `false`.

```java
int x = 1;
int y = 2;

if (x > 5 && y == 2) { // it doesn't matter if y == 2, because x <= 5
    // do something
}
```

Because `x` is not greater than 5, the JVM does not evaluate anything to the right of the `&&` operator.

Similarly, if the left side of an `||` expression is `true`, then it doesn't matter what the right side is. The entire expression is `true`.

```java
int x = 1;
int y = 2;

if (x < 5 || y != 2) {    // it doesn't matter if y != 2, because x < 5
    // do something
}
```

Because `x` is less than 5, the JVM does not evaluate anything to the right of the `||` operator.

## **De Morgan's Laws**

De Morgan's Laws govern the ways in which the negation of complex conditional expressions behave.

{% embed url="https://www.youtube.com/watch?v=AGyjo2DLxjM&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

There are two applicable laws.

* `!(a && b)` is equivalent to `!a || !b`
* `!(a || b)` is equivalent to `!a && !b`

This works in much the same way the distributed property works in algebra to simplify polynomial expressions. The only difference is that in addition to distributing the negation, the interior operator is flipped.

```java
!(x < 3 && y > 2)       // somewhat unclear, no?
```

First, you distribute the `!` operator to both sides of the interior expression. Then, you reverse the operator.

```java
!(x < 3) || !(y > 2)    // in progress
```

Then, you can simplify each side.

```java
(x >= 3 || y <= 2)      // simplified
```

Here's the same walkthrough starting with an `OR` operator.

```java
!(x < 3 || y > 2)       // more confusion
```

Distribute and flip the operator.

```java
!(x < 3) && !(y > 2)    // in progress
```

Simplify.

```java
(x >= 3 && y <= 2)      // simplified
```

