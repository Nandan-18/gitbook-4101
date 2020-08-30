# Wrapper Classes

{% hint style="info" %}
* [Character Documentation](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Character.html)
* [Integer Documentation](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Integer.html)
* [Double Documentation](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Double.html)
{% endhint %}

## Character

The `Character` class serves as a wrapper for the primitive `char` type. It provides several convenient methods for working with and manipulating characters.

### Methods

There are many methods available to the `Character` class. These will likely be the most useful to you.

* `isAlphabetic(int codePoint)`

The `isAlphabetic` method determines if the specified character is an alphabet. It accepts an `int` parameter, which is a Unicode code point.

```java
char alpha = 'A';
char numeric = '3';

Character.isAlphabetic(alpha);      // true
Character.isAlphabetic(numeric);    // false
```

There is a variation of this method that accepts a `char` as a parameter.

* `isDigit(int codePoint)`

The `isDigit` methods determines if the specified character is a digit. It accepts an `int` parameter, which is a Unicode code point.

```java
char letter = 'A';
char number = '7';

Character.isDigit(letter);    // false
Character.isDigit(number);    // true
```

There is a variation of this method that accepts a `char` as a parameter.

* `isLetter(int codePoint)`

The `isLetter` method determines if the specified character is a letter. It accepts an `int` parameter, which is a Unicode code point.

```java
char letter = 'A';
char number = '7';

Character.isLetter(letter);    // true
Character.isLetter(number);    // false
```

There is a variation of this method that accepts a `char` as a parameter.

* `isLetterOrDigit(int codePoint)`

The `isLetterOrDigit` method determines if the specified character is either a letter or a digit. It accepts an `int` parameter, which is a Unicode code point.

```java
char letter = 'A';
char digit = '7';
char special = '$';

Character.isLetterOrDigit(letter);     // true
Character.isLetterOrDigit(digit);      // true
Character.isLetterOrDigit(special);    // false
```

There is a variation of this method that accepts a `char` as a parameter.

* `isLowerCase(int codePoint)`

The `isLowerCase` method determines if the specified character is a lowercase character. It accepts an `int` parameter, which is a Unicode code point.

```java
char lower = 'a';
char upper = 'A';

Character.isLowerCase(lower);    // true
Character.isLowerCase(upper);    // false
```

There is a variation of this method that accepts a `char` as a parameter.

* `isSpaceChar(int codePoint)`

The `isSpaceChar` method determines if the specified character is a space character. It accepts an `int` parameter, which is a Unicode code point.

```java
char space = ' ';
char newline = '\n';
char tab = '\t';

Character.isSpaceChar(space);      // true
Character.isSpaceChar(newline);    // false
Character.isSpaceChar(tab);        // false
```

There is a variation of this method that accepts a `char` as a parameter.

* `isUpperCase(int codePoint)`

The `isUpperCase` method determines if the specified character is an uppercase character. It accepts an `int` parameter, which is a Unicode code point.

```java
char lower = 'a';
char upper = 'A';

Character.isLowerCase(lower);    // false
Character.isLowerCase(upper);    // true
```

There is a variation of this method that accepts a `char` as a parameter.

* `isWhitespace(int codePoint)`

The `isWhitespace` method determines if the specified character is a whitespace character \(by Java's definition of whitespace\). It accepts an `int` parameter, which is a Unicode code point.

```java
char space = ' ';
char newline = '\n';
char tab = '\t';

Character.isWhiteSpace(space);      // true
Character.isWhiteSpace(newline);    // true
Character.isWhiteSpace(tab);        // true
```

There is a variation of this method that accepts a `char` as a parameter.

You can check out all of the available methods and fields in the [full documentation](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/lang/Character.html).

## Integer

The `Integer` class serves as a wrapper for the primitive type `int`. It provides several convenient methods and constants for working with integers, and converting them to and from `String`s.

### Fields

There are two fields you should be familiar with, though more are available.

* `MAX_VALUE`

The `MAX_VALUE` field represents the largest value that an `int` can have.

```java
int largestValue = Integer.MAX_VALUE;
```

* `MIN_VALUE`

The `MIN_VALUE` field represents the smallest value that an `int` can have.

```java
int smallestValue = Integer.MIN_VALUE;
```

### Methods

While there are many methods, here are the two that you'll find yourself using most frequently.

* `toString(int i)`

The `toString` method returns the `String` representation of the integer value.

```java
Integer.toString(7);           // "7" (static call)
```

* `valueOf(String s)`

The `valueOf` method returns an `Integer` object of the specified `String`.

```java
Integer i = Integer.valueOf("12");    // wraps int 12
```

You can check out all of the available methods and fields in the [full documentation](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/lang/Integer.html).

## Double

The `Double` class serves as a wrapper for the primitive type `double`. It provides several convenient methods and constants for working with floating-point values, and converting them to and from `String`s.

### Fields

There are seven fields you should be familiar with, though more are available.

* `MAX_EXPONENT`

The `MAX_EXPONENT` field represents the maximum exponent a finite `double` can have.

```java
int maxExponent = Double.MAX_EXPONENT;
```

* `MAX_VALUE`

The `MAX_VALUE` field represents the largest value that a `double` can have.

```java
double max = Double.MAX_VALUE;
```

* `MIN_VALUE`

The `MIN_VALUE` field represents the smallest value that a `double` can have.

```java
double min = Double.MIN_VALUE;
```

* `NaN`

The `NaN` field represents not a number, which can be the result of certain undefined arithmetic operations.

```java
double quotient = 0.0 / 0;             // Double.NaN
```

* `NEGATIVE_INFINITY`

The `NEGATIVE_INFINITY` field represents -∞, which can be the result of certain undefined arithmetic operations.

```java
double negativeInfinity = -1 / 0.0;    // Double.NEGATIVE_INFINITY
```

* `POSITIVE_INFINITY`

The `POSITIVE_INFINITY` field represents ∞, which can be the result of certain undefined arithmetic operations.

```java
double positiveInfinity = 1 / 0.0;     // Double.POSITIVE_INFINITY
```

### Methods

While there are many methods, here are the two that you'll find yourself using most frequently.

* `isFinite(double d)`

The `isFinite` method returns `true` if the specified value is a finite floating-point value. It returns `false` otherwise, including `NaN` and infinity values.

```java
boolean a = Double.isFinite(7.32);         // true
boolean b = Double.isFinite(1 / 0.0);      // false
```

* `isInfinite(double v)`

The `isInfinite` method returns `true` if the specified value is infinitely large. It returns `false` otherwise.

```java
boolean a = Double.isInfinite(7.32);       // false
boolean b = Double.isInfinite(1 / 0.0);    // true
```

* `isNaN(double v)`

The `isNaN` method returns `true` if the specified value is not a number.

```java
boolean a = Double.isNaN(0.0 / 0);         // true
```

* `toString(double d)`

The `toString` method returns the `String` representation of the `double` value.

```java
Double.toString(7.0);           // "7.0" (static call)
```

* `valueOf(String s)`

The `valueOf` method returns a `Double` object of the specified `String`.

```java
Double d = Double.valueOf("12.0");    // wraps double 12.0
```

You can check out all of the available methods and fields in the [full documentation](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/lang/Double.html).

