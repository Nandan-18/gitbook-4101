# Problem Set 12

## Summary

For this problem set, we'll be focusing on recursive problems and solutions. Each method, with the exception of the `main` method, is declared for you. It is your responsibility to implement each method, and test it thoroughly.

## Requirements

1. Create a repository called `pset-12`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Pull down [the skeleton repository](https://github.com/ucvts/pset-12-4101) containing starter code.
4. Solve each of the exercises, placing each solution in the appropriate method.
5. Add, commit, and push your code to your `pset-12` repository.

## Exercises

The specifications for each exercise are outlined below. Your job is to write code that meets the stated requirements, and matches my output exactly. Work through these exercises on your own. Experiment, make mistakes, ask questions, and fix your mistakes. It's the only way to get good at programming.

Previously, your output was printed to the console. This time, though, you'll be using return statements. To clarify, nothing should be printed to the console and you don't need to use a `Scanner` at all. Correct answers that are printed to the console instead of returned will not be considered.

As a final note, do not modify the method signatures. You can write your code inside of the method bodies, but the names, access modifiers, return types, and parameters must not be altered.

To be clear, it is possible to craft solutions to each of these problems using iteration. There are also certain built-in methods that may perform the computations for you. Neither of those are the purpose of this problem set. You **must** use recursion for each of your solutions!

### Exercise 1

Given an integer, `n`, compute and return the factorial of `n` \(i.e., `n!`\). Return `-1` if any of the following conditions is not met.

* `n` must be greater than `0`.

Here are a few sample calls to the `factorial` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
factorial(1) → 1
factorial(2) → 2
factorial(3) → 6
```

### Exercise 2

The Fibonacci sequence is a famous bit of mathematics, and it happens to have a recursive definition. The first two values in the sequence are `0` and `1`, which are essentially the two base cases. Each subsequent value is the sum of the previous two, so the sequence looks like this: `0, 1, 1, 2, 3, 5, 8`, and so on. Compute and return the `n`_th_ Fibonacci number, with `n = 0` representing the start of the sequence. Return `-1` if any of the following conditions is not met.

* `n` must be greater than or equal to `0`.

Here are a few sample calls to the `fibonacci` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
fibonacci(0) → 0
fibonacci(1) → 1
fibonacci(2) → 1
```

### Exercise 3

Consider a triangle made of blocks. The topmost row has `1` block; the next row down has `2` blocks; the next row down has `3` blocks; and so on, and so forth. Compute the total number of blocks in a triangle with a specified number of `rows`. Return `-1` if any of the following conditions is not met.

* `rows` must be greater than or equal to `0`.

Here are a few sample calls to the `triangle` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
triangle(0) → 0
triangle(1) → 1
triangle(2) → 3
```

### Exercise 4

Given a non-negative integer, `n`, return the sum of its digits. Return `-1` if any of the following conditions is not met.

* `n` must be a non-negative integer.

Here are a few sample calls to the `sumDigits` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
sumDigits(126) → 9
sumDigits(49)  → 13
sumDigits(12)  → 3
```

### Exercise 5

Given a base and exponent, compute the value of base raised to the power of exponent. Return -1 if any of the following conditions is not met.

* `base` must be greater than or equal to `1`.
* `exponent` must be greater than or equal to `1`.

Here are a few sample calls to the `powerN` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
powerN(3, 1) → 3
powerN(3, 2) → 9
powerN(3, 3) → 27
```

### Exercise 6

Given a string, `text`, build a new string where all of the lowercase `x` characters are changed to lowercase `y` characters. Return `null` if any of the following conditions is not met.

* `text` must not be `null`.

Here are a few sample calls to the `changeXY` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
changeXY("codex")   → "codey"
changeXY("xxhixx")  → "yyhiyy"
changeXY("xhixhix") → "yhiyhiy"
```

### Exercise 7

Given an array of integer values, `data`, compute the number of times the value `11` appears in the array. We'll use the convention of considering only the part of the array that begins at the given `index` and continues through the end of the array. Return `-1` if any of the following conditions is not met.

* `data` must not be `null`.
* `index` must be greater than or equal to `0`.
* `index` must not exceed the bounds of the array.

Here are a few sample calls to the `array11` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
array11([1, 2, 11], 0)   → 1
array11([11, 11], 0)     → 2
array11([1, 2, 3, 4], 0) → 0
```

### Exercise 8

Given a string, `text`, and a non-empty substring, `sub`, compute the number of times that `sub` appears in `text` without instances of `sub` overlapping each other. Return -1 if any of the following conditions is not met.

* `text` must not be `null`.
* `sub` must not be `null`.
* `sub` must be non-empty.

Here are a few sample calls to the `strCount` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
strCount("catcowcat", "cat") → 2
strCount("catcowcat", "cow") → 1
strCount("catcowcat", "dog") → 0
```

### Exercise 9

Given a string, `text`, and non-empty substring, `sub`, determine whether or not at least `n` copies of `sub` appear in `text`, allowing for the possibility that instances of `sub` may overlap each other. Return `false` if any of the following conditions is not met.

* `text` must not be `null`.
* `sub` must not be `null`.
* `sub` must be non-empty.
* `n` must be greater than or equal to `0`.

Here are a few sample calls to the `strCopies` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
strCopies("catcowcat", "cat", 2) → true
strCopies("catcowcat", "cow", 2) → false
strCopies("catcowcat", "cow", 1) → true
```

### Exercise 10

Given a string, `text`, and a non-empty substring, `sub`, return the length of the largest substring that starts and ends with `sub`. Return `-1` if any of the following conditions is not met.

* `text` must not be `null`.
* `sub` must not be `null`.
* `sub` must be non-empty.

Here are a few sample calls to the `strDist` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
strDist("catcowcat", "cat")     → 9
strDist("catcowcat", "cow")     → 3
strDist("cccatcowcatxx", "cat") → 9
```

## Deliverables

1. Submit your repository URL.

Your program output should meet each of the requirements, and should account for test cases above and beyond those provided in the sample executions.

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, March 7, 2021.

