# For Loops

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapter 3.8
{% endhint %}

## For Loop

Unlike the `while` and `do/while` loops before, a determinate loop is one where the number of iterations is predefined. The most traditional example, and the only one you'll need to concern yourself with for now, is called a `for` loop. Its syntax is a bit more complicate than what you've seen so far.

```java
for (initialize; test; update) {
    // do stuff here
}
```

A for loop comes with a built-in counter, which it updates and checks to determine when to terminate. The `initialize` segment is where this counter is declared and initialized, the loop continues to execute as long as the `test` segment passes, and the `update` segment updates the counter variable with each iteration of the loop.

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

This code snippet prints the numbers 0 through 4 \(on separate lines\). You don't need to manually increment the value of `i` in the loop body. Instead, it's handled inside of the parentheses in the `update` section.

{% embed url="https://www.youtube.com/watch?v=by3YNCeEOuE&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

Let's look at an example of our own.

{% code title="PrintNumbers.java" %}
```java
public class PrintNumbers {
    public static void main(String[] args) {
        for (int i = 0; i < 5; i++) {
            System.out.println(i);
        }
    }
}
```
{% endcode %}

```text
$ java PrintNumbers
0
1
2
3
4
```

### Scope

Again, variables declared inside of a for loop are only accessible in that same loop. This includes the counter variable that is initialized in the parentheses. The scope of the counter variable is the for loop itself, and can be referenced within the body.

```java
for (int x = 5; x > 0; x--) {
    // x is accessible here
}
// but not here
```

## Choosing a Loop

If you really wanted to, you could re-implement identical solutions using a `while`, `do/while`, or `for` loop. But each has its pros and cons, and there are situations that are more appropriate for one versus the others.

* You should use a `for` loop if your loop needs to execute a finite number of times.
* You should use a `while` loop if your loop needs to execute as long as some condition is met.
* You should use a `do/while` loop if your loop needs to execute as long as some condition is met, but _at least_ once.

Remember, `do/while` loops are less common, and many developers still would opt for a `while` loop even if the code needed to execute at least once.

## Common Errors

There are a few common errors that new programmers tend to make when using loops.

* Off-by-one error
* Infinite loop
* Equals v. assignment
* Logical AND v. OR

Let's take a look at each one.

### Off-by-one

An off-by-one error typically occurs when you confuse a relational operator \(i.e., `<` instead of `<=`\). Suppose you wanted to print every integer from 1 to 5 \(inclusive\).

```java
for (int i = 1; i < 5; i++) {
    System.out.println(i);
}
```

Although seemingly correct, this code actually prints 1 through 4. It doesn't print 5 because the test condition fails when `i` is 5. To remedy this, you'd need to use the `<=` operator instead of the &lt; operator.

```java
for (int i = 1; i <= 5; i++) {    // see the correct operator?
    System.out.println(i);
}
```

The example depicts this scenario with a `for` loop, but the same could happen with `while` and `do/while` loops.

### Infinite Loop

An infinite loop condition occurs when you aren't making progress towards loop termination. It can occur with any of the three loops.

```java
int x = 1;
while (x < 5) {
    System.out.println(x);
}
```

This loop will never end because `x` is never incremented. The only way for the loop to terminate is for `x` to become greater than or equal to 5, which you'd need to do in the body of the loop. Adding `x++` inside the body of the loop would solve this problem.

### Equality v. Assignment

If you mistakenly use assignment instead equality in the condition of a loop, you might find yourself in an infinite loop. Remember, the `==` sign is for testing equality \(of primitives\) and the `=` sign is for assigning values.

```java
int x = 1;
int y = 1;

while (x = y) {
    System.out.println("x and y are equal.");
    x++;
}
```

At first glance, this code should only run once. `x` and `y` are initially equal. In the body of the loop, `x` is incremented by 1 and `y` is not. On the second pass, the condition should evaluate to `false`. However, if you compile and run this code, you'll see that it prints `x and y are equal.` infinitely.

In the condition of the loop, you should use `==` to test for the equality of `x` and `y`. Instead, a single `=` sign is used. In this case, the value of `y` is assigned to `x`. Because variable assignments always evaluate to `true`, this causes an infinite loop.

### Logical AND v. OR

Things can get a little tricky when using `&&` and `||` in the condition of a loop, often leading to unintended consequences. Suppose you want your loop to exit when `x` is either 1 or 2.

```java
int x = /* user input */;

do {
    // do something here
} while (!(x == 1) || !(x == 2));
```

In order for the condition to be met, both `x == 1` and `x == 2` would need to be `true`. Clearly, this can never be the case so the condition is always `true`. To correct this code, you'd need to swap the `||` operator for an `&&` operator.

```java
int x = /* user input */;

do {
    // do something here
} while (!(x == 1) && !(x == 2));
```

{% page-ref page="../problem-sets/problem-set-6.md" %}

