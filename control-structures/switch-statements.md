# Switch Statements

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapter 3.8
{% endhint %}

## Switch

The `if/else if` syntax can get a little daunting, especially when you have a lot of alternative conditions and branches. The `switch` statement can be a little easier to work with, and it offers similar functionality.

{% embed url="https://www.youtube.com/watch?v=O4KGYGQvHmw" %}

You're not going to see the switch statement too much on the AP exam, but it's still an important component of the language that you'll be expected to understand.

```java
int input = /* some user input */;

switch (input) {
    case 1:
        // do something
        break;
    case 2:
        // do something
        break;
    case 3:
        // do something
        break;
    default:
        // do something
        break;
}
```

The `switch` statement compares the value of `input` \(or whatever is in the parentheses\) to each of the `case`s \(in this example, `1`, `2`, and `3`\). When it finds an exact match, it executes the code inside of that `case`. If no match is found, it moves on to the next `case` statement \(sequentially, from top to bottom\). The `default` statement acts as a catch-all, in the event that none of the `case` statements matches the `input` value.

This would be equivalent to the following `if/else if` statement.

```java
if (input == 1) {
    // do something
} else if (input == 2) {
    // do something
} else if (input == 3) {
    // do something
} else {
    // do something
}
```

Each `if` condition corresponds to a `case` in the `switch` statement, and the `else` clause corresponds to the `default` statement.

## Break Statements

You probably noticed that the `switch` statement has those weird `break` keywords, which don't exist in any of the `if` statement types. Unlike `if` statements, it's possible to execute the code for multiple `case`s. The `break` statement is how you exit the `switch` statement.

```java
System.out.print("Where do you live? ");
String state = in.nextLine();

switch (state) {
    case "Washington":
        System.out.println("Do you live in Seattle?");
        break;
    case "Oregon":
        System.out.println("Do you live in Portland?");
        break;
    case "California":
        System.out.println("Do you live in Los Angeles?");
        break;
    default:
        System.out.println("You live somewhere else.");
        break;
}
// code resumes here after hitting a break statement
```

Depending on what the user enters in response to the prompt, only a single print statement will ever be executed.

{% code title="Switch.java" %}
```java
import java.util.Scanner;

public class Switch {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        System.out.print("Where do you live? ");
        String state = in.nextLine();
        
        switch (state) {
            case "Washington":
                System.out.println("Do you live in Seattle?");
                break;
            case "Oregon":
                System.out.println("Do you live in Portland?");
                break;
            case "California":
                System.out.println("Do you live in Los Angeles?");
                break;
            default:
                System.out.println("You live somewhere else.");
                break;
        }
        
        in.close();
    }
}
```
{% endcode %}

```text
$ java Switch
Where do you live? Oregon
Do you live in Portland?
```

What if you forgot the `break` statement for the _Oregon_ `case`? Your code would still work fine for the `"Washington"` and `"California"` `case`s, as well as the `default case`. However, it would fail for the `"Oregon"` `case`.

{% code title="Switch.java" %}
```java
import java.util.Scanner;

public class Switch {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        System.out.print("Where do you live? ");
        String state = in.nextLine();
        
        switch (state) {
            case "Washington":
                System.out.println("Do you live in Seattle?");
                break;
            case "Oregon":
                System.out.println("Do you live in Portland?");
                // oops, forgot the break
            case "California":
                System.out.println("Do you live in Los Angeles?");
                break;
            default:
                System.out.println("You live somewhere else.");
                break;
        }
        
        in.close();
    }
}
```
{% endcode %}

```text
$ java Switch
Where do you live? Oregon
Do you live in Portland?
Do you live in Los Angeles?
```

See the second run, where the user entered `Oregon`? Because of the forgotten `break` statement, the program executed the code for both the `"Oregon"` `case`and the `"California"` `case`. Usually, this isn't what you want. There are times, however, where falling through is done by design. You should be careful if you choose to do this, and you should clarify your intent with a comment.

{% code title="Switch.java" %}
```java
import java.util.Scanner;

public class Switch {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        
        System.out.print("Where do you live? ");
        String state = in.nextLine();
        
        switch (state) {
            case "Washington":
            case "Oregon":
            case "California":
                System.out.println("A resident of the west coast!");
                break;
            default:
                System.out.println("You live somewhere else.");
                break;
        }
        
        in.close();
    }
}
```
{% endcode %}

```text
$ java Switch
Where do you live? Washington
A resident of the west coast!
$
$ java Switch
Where do you live? California
A resident of the west coast!
```

For all three inputs—`Washington`, `Oregon`, and `California`—the program executes the print statement associated with the `"California"` `case`. By design, the `"Washington"` and `"Oregon"` `case`s fall through to the `"California"` `case`.

## Pros and Cons

In many ways, the `switch` statement is equivalent to the `if/else if` statement. If needed, you can convert one to the other. That being said, there are times where one might be more appropriate than the other.

The `switch` statement eases your burden as a programmer when there are a lot of alternative conditions. Writing 5, 10, or 15 conditions to an `if/else if`statement quickly becomes tedious. In this instance, you should probably use a `switch` statement.

`if` statements of all kinds make it simple and straightforward to compare ranges of values.

```java
if (x >= 1 && x <= 5) {
    // A
} else if (x >= 6 && x <= 10) {
    // B
} else if (x >= 11 && x <= 15) {
    // C 
}
```

The conditions of the `if/else if` statement match values between 1 and 5, 6 and 10, and 11 and 15, respectively. This would be difficult to replicate with a `switch` statement, as you'd need to provide exact match `case`s for each value between 1 and 15.

