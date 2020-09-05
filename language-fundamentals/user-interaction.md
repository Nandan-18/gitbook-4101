# User Interaction

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapter 3.7
{% endhint %}

## Reading Input

Your programs would get pretty dull pretty quickly without a little user interaction. First, the focus will be on textual input via the console. Later, that focus will shift towards creating graphical interfaces with Java.

### Importing and Initializing

To read user input from the keyboard, you're going to use something called a `Scanner`. This is one of several built-in classes that allows you to interact with users via the console. Although it is built into the language, you need to inform the compiler that you'll be using this class \(and also where it is located\). This is true of most built-in classes you'll use \(more specifically, any class not defined in the `java.lang` package\).

```java
import java.util.Scanner;    // this is called an import statement
```

Import statements go at the top of the source file, above the class declaration. You can always Google a Java class to find its import statement. Once imported, you can declare and initialize a variable whose data type is `Scanner`.

{% code title="UserInput.java" %}
```java
import java.util.Scanner;

public class UserInput {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
    }
}
```
{% endcode %}

The declaration piece follows the same `dataType variableName` convention you've seen. The initialization piece looks a little different, and is reminiscent of the `String` constructor \(i.e., it uses the `new` operator\). Every class has a constructor designed to create instances of it, and `Scanner` is no exception.

To create an instance of a `Scanner`, you need to supply a single piece of information: the source of the input to be read. In this example, the goal is to read from the standard system input \(i.e., the keyboard\). Java knows this as `System.in`, so that's what you put inside the parentheses of the constructor.

{% embed url="https://www.youtube.com/watch?v=1n-\_ZNM5SLc" %}

### Available Methods

Like the `String` class, there are a number of methods available on your `Scanner` object. For now, you should focus on the `next` methods, which will wait for the user to enter a value of a certain data type.

| **Method** | **Description** | **Usage** |
| :--- | :--- | :--- |
| `nextByte` | Scans the next token of the input as a `byte`. | `byte digit = in.nextByte();` |
| `nextShort` | Scans the next token of the input as a `short`. | `short grade = in.nextShort();` |
| `nextInt` | Scans the next token of the input as an `int`. | `int age = in.nextInt();` |
| `nextLong` | Scans the next token of the input as a `long`. | `long population = in.nextLong();` |
| `nextFloat` | Scans the next token of the input as a `float`. | `float cost = in.nextFloat();` |
| `nextDouble` | Scans the next token of the input as a `double`. | `double price = in.nextDouble();` |
| `nextBoolean` | Scans the next token of the input as a `boolean`. | `boolean valid = in.nextBoolean();` |
| `next` | Finds and returns the next complete token from this scanner. | `String word = in.next();` |
| `nextLine` | Advances this scanner past the current line and returns the line that was skipped. | `String line = in.nextLine();` |

You're probably wondering what the repeated references to _token_ are. The `Scanner` breaks up user input into chunks called tokens. By default, a token is everything between two whitespace characters \(i.e., all the words in a sentence are individual tokens because they're separated by spaces\).

The descriptions for `next` and `nextLine` can be a bit confusing. These come directly from the Oracle documentation, so they are a bit technical. Let's see if we can simplify it a bit. Consider the following text.

```text
"Welcome to AP Computer Science A!"
```

If you used `next` to read this line, it would return `"Welcome"`. It just grabs the next word, where a word is defined as a sequence of characters. The end of the word is whenever the `Scanner` encounters whitespace \(a space, tab, line break, etc.\). The `nextLine` method would grab everything — `"Welcome to AP Computer Science A!"`. The end of a line is whenever the `Scanner` encounters a line break.

Now, you can add some prompts and start to work your way towards more interactive programs.

{% code title="UserInput.java" %}
```java
import java.util.Scanner;

public class UserInput {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        System.out.println("How old are you?");
        int age = in.nextInt();
        System.out.println("You are " + age + " year(s) old.");
        
        in.close();
    }
}
```
{% endcode %}

This program will ask the user to enter his or her age, then print a message using the value entered. Go ahead and give it a try.

```text
$ java UserInput
How old are you?
17
You are 17 year(s) old.
```

When you're done using a `Scanner`, it's important that you close it \(see the call to `close` on _Line 11_?\). The JVM manages your program's memory, but not its resources. You must release those manually.

_Line 8_ makes a call to `nextInt` and stores its result in an `int`. This is fine for now, but you really can't assume that users will enter the correct and expected data type. A mismatch in data types here would crash our program.

```text
$ java UserInput
How old are you?
APCS
Exception in thread "main" java.util.InputMismatchException
    at java.base/java.util.Scanner.throwFor(Scanner.java:939)
    at java.base/java.util.Scanner.next(Scanner.java:1594)
    at java.base/java.util.Scanner.nextInt(Scanner.java:2258)
    at java.base/java.util.Scanner.nextInt(Scanner.java:2212)
    at UserInput.main(UserInput.java:8)
```

### Special Cases

There is no method for reading a `char`. To do that, you need to use a combination of `Scanner` and `String` methods. First, read in a single token using the `next` method. Then, use the `charAt` method to grab the first character.

```java
String word = in.next();
char letter = word.charAt(0);    // get the first character (indexes start
                                 // at 0, remember?)
```

You can also chain methods together to keep this on one line.

```java
String word = in.next().charAt(0);    // same as above
```

`Scanner`s can behave oddly when switching between `nextLine`, and `next` or `next<DataType>` methods. The `newLine` method consumes the line break \(called a newline in Java\) at the end of the input, but the `next` and `next<DataType>` methods do not.

When switching between these methods, it can sometimes appear that the `Scanner` is skipping over some input entirely. The `Scanner` is actually encountering the dangling newline left behind by the `next` or `next<DataType>` methods, and thinks it has reached the end of the input.

{% code title="UserInput.java" %}
```java
import java.util.Scanner;

public class UserInput {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        System.out.println("How old are you?");
        int age = in.nextInt();
        
        System.out.println("What's your name?");
        String name = in.nextLine();
        
        System.out.println(name + " is " + age + " year(s) old.");
        in.close();
    }
}
```
{% endcode %}

The program seems correct at first glance, but try running it. You might be surprised by the output.

```text
$ java UserInput
How old are you?
17
What is your name?
 is 17 year(s) old.
```

There's a dangling newline left from the call to `nextInt` that interferes with the second prompt. We can add a call to `nextLine` to consume it and fix the problem.

{% code title="UserInput.java" %}
```java
import java.util.Scanner;

public class UserInput {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        System.out.println("How old are you?");
        int age = in.nextInt();
        in.nextLine();    // consume dangling newline
        
        System.out.println("What's your name?");
        String name = in.nextLine();
        
        System.out.println(name + " is " + age + " year(s) old.");
        in.close();
    }
}
```
{% endcode %}

Re-compile and re-run the program. All is well now.

```text
$ java UserInput
How old are you?
17
What is your name?
Anthony
Anthony is 17 year(s) old.
```

## Formatting Output

You've done some printing already, and each time you've used `println`. This prints the text to the console, and then advances the cursor to the next line. There is an equivalent method called `print` that prints text, but does not advance the cursor to the next line. This time, the focus will be on a third variant: `printf`. This allows you to print text, while also adding custom formatting.

### Specifiers

There are a number of format specifiers that can be used to alter how text is printed to the console. Here's why this might be needed.

```java
double x = 10000.0 / 3.0;
System.out.print(x);
```

Because Java prints the maximum number of non-zero digits for that data type, this will print the following.

```java
3333.3333333333335
```

What if you're trying to work with currencies? You'd want to limit the number to two decimal places.

```java
System.out.printf("%.2f", x);
```

This tells the `printf` method to limit the width of the entire value to 8 characters \(which, in this example, would include the decimal point\), and allow for only two digits after the decimal point. Now, it neatly prints `3333.33`. As a small aside, there are better ways to work with currencies than using `double`s. We'll cover those in the Bank Account Walkthrough.

There are a host of format specifiers available to us. Here are the more commonly used ones.

| **Conversion Character** | **Type** |
| :--- | :--- |
| `d` | Decimal integer. |
| `f` | Fixed-point floating point number. |
| `s` | String. |
| `c` | Character. |
| `b` | Boolean. |
| `%` | The percent symbol. |
| `n` | Platform-depending line separator. |

### Flags

In addition to format specifiers, you can use flags to further customize the output. Remember the original example? You were able to format the number from `3333.3333333333335` to `3333.33`. You can take this even further.

```java
System.out.printf("%,.2f", x);    // see the added comma after the % sign?
```

Now, you're asking `printf` to format the number with separating commas. It results in `3,333.33`.

Again, there are several flag options available to us.

| **Flag** | **Purpose** |
| :--- | :--- |
| `+` | Prints a sign for positive and negative numbers. |
| `space` | Adds a space before positive numbers. |
| `0` | Adds leading zeroes. |
| `-` | Left-justifies the field. |
| `(` | Encloses negative numbers in parentheses. |
| `,` | Adds group separators. |
| `#` | Always includes a decimal point. |

Hopefully you're starting to pick up on the pattern. You're going to do a lot of programming in this course!

{% page-ref page="../problem-sets/problem-set-3.md" %}

