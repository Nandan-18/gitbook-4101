# Scope

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapter 3.8
{% endhint %}

## Variable Scope

A block consists of one or more lines of code surrounded by a pair of curly braces. Blocks define the scope in which your variables are accessible.

{% embed url="https://www.youtube.com/watch?v=rbup-baLBlI&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

We'll revisit this topic as we start to discuss methods and classes later in the course. For now, it is sufficient to understand scope only within the context of control structures \(like `if` statements and `for` loops, for example\) and the `main` method we've all come to know and love.

{% code title="Scope.java" %}
```java
public class Scope {
    public static void main(String[] args) {
        String state = "NY";    // accessible everywhere inside the main
                                // method

        if (state.equals("NY")) {
            long population = 8623000L;    // only available inside the if
                                           // statement
        }
        // population is no longer accessible here
    }
}
```
{% endcode %}

It's important to remember where you declare your variables, because that is the scope in which they will be available.

{% code title="Scope.java" %}
```java
public class Scope {
    public static void main(String[] args) {
        String state = "NY";    // accessible everywhere inside the main
                                // method

        if (state.equals("NY")) {
            long population = 8623000L;    // only available inside the if
                                           // statement
            
            System.out.printf("The population of %s is %d.\n", state,
              population);
        }
        // population is no longer accessible here
        
        System.out.println(state + " is still in scope.");
        System.out.println("But " + population + " is out of scope.");
    }
}
```
{% endcode %}

Trying to access a variable out of scope results in a compilation error.

```text
$ javac Scope.java
Scope.java:13: error: cannot find symbol
        System.out.println("But " + population + " is out of scope.");
                                    ^
  symbol:   variable population
  location: class Scope
1 error
```

From the compiler's perspective, the `population` variable does not exist at moment that it's referenced. See the error in the stack trace? It says it `cannot find symbol`, and points the `population` variable.

