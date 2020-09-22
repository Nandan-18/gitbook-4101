# Ternary Operator

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapter 3.8
{% endhint %}

## Syntax

The ternary operator is another conditional control structure, often used to selectively assign one of two values to a variable at runtime. It functions as a condensed version of an `if/else` statement, while also returning a value.

{% embed url="https://www.youtube.com/watch?v=ln\_vMXXXeDI" %}

The syntax behind the ternary operators is little unfamiliar.

```java
(condition) ? expression1 : expression2;
```

First, the `contion` is evaluated. If it is `true`, then `expression1` is returned. Otherwise, `expression2` is returned. Typically, the result of `expression1` or `expression2` is conditionally assigned to a variable.

## Usage

If you wanted to print a sentence that states how many apples are left in a supermarket's inventory, a ternary operator might be helpful in getting the verb conjugation and pluralization right. The lazy way would look like this.

```java
int apples = /* read from a database */;

// remaining apples might be 0, 1, or greater
System.out.println("There is (are) " + apples + " apple(s) in stock.");

// prints: There is (are) X apple(s) in stock.
```

The sentence will be grammatically correct, but not the most elegant. What if you wanted to clean it up?

```java
int apples = /* read from a database */;
String status = (apples == 1)
  ? "is " + apples + " apple"
  : "are " + apples + " apples";

System.out.println("There " + status + " in stock.");

// prints: There is 1 apple in stock.
//         There are 0 apples in stock.
//         There are X apples in stock. (where X is greater than 1)
```

Now, the ternary operator will assign `"is 1 apple"` or `"are X apples"` to the `status` variable. If the value of `apples` is 1, then the ternary operator returns `"is 1 apple"`. If the value of `apples` is 0 or greater than 1, then the ternary operator returns `"are X apples"`, where `"X"` is the value of `apples`.

## Nesting Ternary Operators

Like anything else, you can nest ternary operators. However, this can become messy and hard to read. For shorter expressions, it's acceptable to put the entire ternary operator \(condition, and two expressions\) on a single line.

```java
double bonusRate = (experience > 10) ? 0.15 : 0.05;
```

However, for longer or nested expressions, it's helpful to break this out across several lines. The condition should go on the first line \(along with the variable assignment\), then each expression should be placed on its own line.

```java
String accessLevel = role.equals("manager")
    ? "elevated"
    : "standard";

// if role is manager, accessLevel = elevated
// if role is not manager, accessLevel = standard
```

This isn't the longest expression, but it makes the point. Simplify your code for those who may read it. The variable assignment and condition go on the first line, the `?` and the first expression go on the second line, and the `:` and the second expression go on the third line.

You should probably do the same for any nested statements, regardless of length.

```java
double bonusRate = role.equals("manager")
    ? experience > 10 ? 0.20 : 0.10
    : experience > 10 ? 0.10 : 0.05;

// if role is manager and experience > 10, bonusRate = 0.2
// if role is manager and experience <= 10, bonusRate = 0.1
// if role is not manager and experience > 10, bonusRate = 0.1
// if role is not manager and experience <= 10, bonusRate = 0.05
```

Again, the expressions are rather short. The top-level ternary operator is broken out across three lines as detailed earlier. The nested ternary operators, provided they aren't too long, can go on a single line.

{% page-ref page="../problem-sets/problem-set-5.md" %}

