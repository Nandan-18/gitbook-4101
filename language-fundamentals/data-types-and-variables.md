# Data Types and Variables

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 3.3 and 3.4
{% endhint %}

## Types

Java is known as what is called a strongly-typed language, which means that every variable must be assigned a specific data type. We, as programmers, are only allowed to store information that matches this given type. There are eight primitive data types built into Java.

* `byte`
* `short`
* `int`
* `long`
* `float`
* `double`
* `char`
* `boolean`

Each data type handles data of varying sizes and categorizations. Let's walk through each one individually. It's important that you understand their purposes and what makes each one different from the others.

{% embed url="https://www.youtube.com/watch?v=2SDFvqt6mkk&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

### Integer Types

Java provides four data types that are tasked with storing numbers without fractional components \(i.e., integers\).

| **Type** | **Storage** | **Range of Values** |
| :--- | :--- | :--- |
| `byte` | 1 byte | -128 to 127 |
| `short` | 2 bytes | -32,768 to 32,767 |
| `int` | 4 bytes | -2,147,483,648 to 2,147,483,647 |
| `long` | 8 bytes | -9,223,372,036,854,755,808 to 9,223,372,036,854,755,807 |

The AP exam focuses primarily on the `int` type. You should, of course, understand when and why something other than an `int` might be needed or appropriate.

### Number Types

If you need to store fractional values, Java provides two data types that fit the bill.

| **Type** | **Storage** | **Range of Values** |
| :--- | :--- | :--- |
| `float` | 4 bytes | Approximately ±3.40282347E+38F \(6-7 significant decimal digits\) |
| `double` | 8 bytes | Approximately ±1.79769313486231570E+308 \(15 significant decimal digits\) |

The AP exam focuses primarily on the `double` type. Again, it's important you understand when and why a `double` might not be the best choice for a floating-point value.

### Unicode Characters

To simplify things, Java provides a single data type to deal with characters. It is called a `char` and it stores only a single character \(not zero, or two, or anything else\). There's another data type for sequences of characters, which you'll learn all about in the [Strings](strings.md) section.

| **Type** | **Storage** | **Range of Values** |
| :--- | :--- | :--- |
| `char` | 2 bytes | 0 to 65,536 \(unsigned\) |

Unicode was developed in the late 1980s, at a time when two bytes were more than enough to encode every character in every supported language. It has since outgrown two bytes with the addition of ideographs for Chinese, Japanese, and Korean languages, as well as emojis.

A `char` in Java, while it once represented a single character, now describes a code unit in the UTF-16 encoding scheme. Essentially, this means that a `char`can represent Unicode values provided those values can be represented with 16 bits \(`'\u0000'` to `'\uFFFF'`\).

Some have argued that `char`s are outdated and should be avoided. Unless you are manipulating UTF-16 code units or need to strictly limit memory consumption, there's no reason you couldn't or shouldn't opt for a `String` over a `char`.

### Booleans

A `boolean` can have one of two possible values: `true` or `false`. Java provides a single data type for storing such values.

| **Type** | **Storage** | **Range of Values** |
| :--- | :--- | :--- |
| `boolean` | Undefined | Either `true` or `false` |

A `boolean` is used for evaluating logical conditions. Unlike other languages \(like JavaScript or C++\), there is no implicit conversion to a `boolean`.

## Variables

You can think of a variable as a container that holds information—this might be data entered by the user, or something internal to your application. Either way, a variable must be declared with a data type and name. It can only store information that matches its declared type, and you can reference it \(i.e., use its value\) by its name.

### Declaring Variables

To declare a variable, you define a data type and a name.

```java
dataType variableName;
```

Following this declaration format, you can declare variables of each of the primitive data types.

```java
byte digit;
short grade;
int age;
long population;
float cost;
double price;
char letter;
boolean valid;
```

I've chosen arbitrary names here. Logically, though, the implied contents of each variable fit the supported range of values. For example, it wouldn't make sense to use a `byte` for the `population` variable because a `byte` isn't capable of storing integers that large.

### Initializing Variables

Declaring a variable informs the compiler of its existence, but you can't actually use it until you initialize it. This is just a fancy way of saying you need to provide an initial value for a variable. To do so, we need to use the `=` operator.

You can declare and initialize variables in a single statement.

```java
int year = 2020;    // declare and initialize
```

Alternatively, you can separate this process into two statements. In most cases, this is a matter of preference. There are times, though, where you need to declare a variable in order to set it up for later use.

```java
int year;       // declare
year = 2020;    // initialize
```

Once you've initialized a variable, you can modify its value in the same manner.

```java
int year = 2020;    // initialize and declare
year = 2021;        // re-assign its value
```

A numeric literal is a raw number \(i.e., a value not stored in a variable\). By default, Java treats integer literals as `int`s and floating-point literals as `double`s.

```java
System.out.println(9876543210);    // treated as an int
System.out.println(1.23456789);    // treated as a double
```

To instruct the compiler to treat these values as a `long` or `float`, you need to add the appropriate suffices.

```java
System.out.println(9876543210L);    // explicitly treated as a long
System.out.println(1.23456789f);    // explicitly treated as a float
```

You suffix `long`s with an `L` and `float`s with an `f`. Although, the capitalization doesn't matter, it is conventional to use a capital `L` and a lowercase `f`. A lowercase `l` is more likely to be mistaken for a `1` \(the number\).

A `char` has special symbol you need to use during initialization or assignment. All character literals are surrounding by single-quotes. This is important. Wrapping a value in double-quotes, instead, creates a completely separate data type, which you'll see later in the [Strings](strings.md) section.

```java
char letter = 'A';    // note the use of single-quotes
```

And lastly, `boolean`s use the keywords `true` and `false` during initialization or assignment.

```java
boolean valid = true;
boolean invalid = false;
```

### Constants

If you need to create a variable that holds a constant value \(i.e., a variable whose value will not change after initially being set\), you can use the `final`keyword.

```java
final int DAYS_PER_WEEK = 7;    // this value cannot be changed
```

The `final` non-access modifier precedes the data type. By convention, `final` variables are written in all capital letters to make it immediately obvious to those reading or working with the source code that the value is a constant.

{% embed url="https://www.youtube.com/watch?v=EbxbE4CpdF4&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## Naming Conventions

A variable name should begin with a lowercase letter \(the lone exception being constants\). It should adhere to camel casing, which means that subsequent words after the first are individually capitalized.

```java
int elapsedTimeInDays;
```

Take note of the words in the variable: _elapsed_, _time_, _in_, and _days_. Elapsed is all lowercase, and each subsequent word has its first letter capitalized.

Constants, of course, are different. All words are capitalized, but are separated with underscores.

### Revealing Intent

Either way, though, the variable name should convey meaning.

```java
int x;    // elapsed time in days
```

The variable name, `x`, offers nothing in terms of intent or meaning. A much cleaner name would communicate the purpose of the variable and its contents.

```java
int elapsedTimeInDays;
```

Sometimes a compiler might complain about using the same variable. Once you declare a variable, you cannot reuse that name for another variable in the same scope. It can be tempting to alter the variable names in an arbitrary way to satisfy the compiler. Consider the following example.

```java
int distance1;    // in inches
int distance2;    // in centimeters
```

You have two different variables. So, you should have two different names that convey two different meanings. A better decision would be to clarify the intent.

```java
int distanceInInches;
int distanceInCentimeters;
```

Now, you won't be confused if you encounter these variables hundreds of lines of code later. Their purpose and the values they hold will be abundantly clear.

### Pronounceable and Searchable

Favor variable names that are human-readable and pronounceable.

```java
int cmperhr;    // centimeters per hour
```

Maybe you can figure out the intention behind this name, but it certainly would take a second or two. Cut out the ambiguity and potential misinterpretation.

```java
int centimetersPerHour;
```

You should also choose variable names that are easily searchable in a potentially large codebase.

```java
double i;    // test score
```

If you need to find a variable, you can use `Ctrl+F` or `Cmd+F` to make your life easier. However, a variable like `i` will likely show up in a number of phrases other than the variable itself. Choose a more distinct and search-friendly name.

```java
double testScore;
```

## Comments

Comments serve to clarify the meaning behind one or more lines of code. Like whitespace, comments are ignored by the compiler and they have no effect on the execution of the program. They're strictly for human consumption. There are two types of clarification comments: single-line comments, and multi-line comments.

### Single-line Comments

A single-line comment is typically used for concise descriptions. Single-line comments begin with the `//` compound symbol.

```java
// this is a single-line comment
```

Of course, you can use consecutive single-line comments to span multiple lines.

```java
// now this is a multi-line comment
// made from two single-line comments
```

Perfectly valid, but there's already a multi-line comment for that purpose.

### Multi-line Comments

A multi-line comment is typically used for longer descriptions of more complex segments of code. Unlike a single-line comment that has just an opening marker, multi-line comments have both opening and closing markers. It starts with `/*` and ends with `*/`.

```java
/*
 * this comment spans
 * multiple lines
 */
```

Some software developers have argued that good code is self-documenting, and to some extent that is true. Poorly written code is often unclear or cluttered, while high quality code doesn't require an abundance of comments occupying the vertical real estate. If it's written well, its meaning will be clear. Comments do, however, add value when used appropriately. If the code itself documents the _how_, then the comments help to communicate the _why_. Sample usages, expected inputs and outputs, possible future improvements, and implementation-specific tradeoffs are all great examples of informative and clarifying comments.

## Documentation

In addition to clarifying code segments, Java provides a third type of comment for documenting your code. These are called Javadoc comments, and they're designed to communicate to other developers _how_ to use your code \(rather than specifics of the implementation\). A Javadoc comment starts with `/**` and ends with `*/`.

```java
/**
 * This is a Javadoc comment.
 */
```

Javadoc comments autogenerate HTML-formatted documentation that is intended to be published. Typically, you'll see such documentation when reading through application programmer interfaces \(APIs\) like the ones you'll see for built-in Java classes later in the course.

### Tags

Javadoc comments support several tags to convey specific information, such as who wrote the code, what parameters a method requires as input, and what data a method produces as output.

Here's a complete list of supported Javadoc comment tags.

| **Tag** | **Description** | **Usage** |
| :--- | :--- | :--- |
| `@author` | Denotes the author of the class. | `@author name` |
| `{@code}` | Displays the text in code font without interpreting it as HTML markup. | `{@code text}` |
| `@deprecated` | Indicates that the API should no longer be used. | `@deprecated text` |
| `{@docRoot}` | Represents a relative path to the document's root directory. | `{@docRoot}` |
| `@exception` | Identical to the `@throws` tag. | `@exception class description` |
| `{@inheritDoc}` | Copies documentation from the nearest inheritable class or implementable interface. | `{@inheritDoc}` |
| `{@link}` | Inserts an inline link to another package, class, or member. | `{@link pkg.class#member label}` |
| `{@linkplain}` | Identical to `{@link}` minus the code font formatting. | `{@linkplain pkg.class#member label}` |
| `{@literal}` | Displays the text without interpreting it as HTML markup. | `{@literal text}` |
| `@param` | Adds a parameter with a name and description to the Parameters section. | `@param name` _``_`description` |
| `@return` | Adds a Return section with the description text. | `@return description` |
| `@see` | Adds a See Also section with an entry pointing to a reference. | `@see reference` |
| `@serial` | Used in the documentation comment for a default serializable field. | `@serial description | incl | excl` |
| `@serialData` | Uses the data description value to document the types and order of data. | `@serialData description` |
| `@serialField` | Documents a serialization descriptor. | `@serialField field type description` |
| `@since` | Adds a Since heading, indicating the version of the Java platform API specification. | `@since version` |
| `@throws` | Indicates that a certain exception may be thrown. | `@throws class description` |
| `{@value}` | Displays constant values. | `{@value pkg.class#field}` |
| `@version` | Adds a Version heading, indicating the current release. | `@version version` |

Most of these aren't relevant to the course; however, the AP Computer Science A exam uses the `@param` and `@return` tags to document method behavior. At a minimum, you'll need to know how to interpret these.

