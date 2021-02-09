# Problem Set 11

## Summary

For this problem set, we'll be focusing on using a new `Object` type: `ArrayList`s! Each method, with the exception of the `main` method, is declared for you. It is your responsibility to implement each method, and test it thoroughly.

## Requirements

1. Create a repository called `pset-11`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Pull down [the skeleton repository](https://github.com/ucvts/pset-11-4101) containing starter code.
4. Solve each of the exercises, placing each solution in the appropriate method.
5. Add, commit, and push your code to your `pset-11` repository.

## Exercises

The specifications for each exercise are outlined below. Your job is to write code that meets the stated requirements, and matches my output exactly. Work through these exercises on your own. Experiment, make mistakes, ask questions, and fix your mistakes. It's the only way to get good at programming.

Previously, your output was printed to the console. This time, though, you'll be using return statements. To clarify, nothing should be printed to the console and you don't need to use a `Scanner` at all. Correct answers that are printed to the console instead of returned will not be considered.

As a final note, do not modify the method signatures. You can write your code inside of the method bodies, but the names, access modifiers, return types, and parameters must not be altered.

You've already demonstrated \(or at least you should have!\) that you understand the logic behind implementing these solutions. This problem set is more about understanding the syntax and usage of `ArrayList`s \(and how they differ from arrays\) than anything else.

### Exercise 1

Consider a series of numbers in the range `[start, end)`. Return a new `ArrayList` containing the string form of these numbers \(i.e., `1` would be `"1"`\). There are a couple of exceptions. For multiples of `3`, translate the number to `"Fizz"`; for of `5`, use `"Buzz"`; and, for multiples of both `3` and `5`, use `"FizzBuzz"`. Return `null` if any of the following conditions is not met.

* `start` is greater than or equal to `end`.

Here are a few sample calls to the `fizzBuzz` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
fizzBuzz(1, 6)  → { "1", "2", "Fizz", "4", "Buzz" }
fizzBuzz(1, 8)  → { "1", "2", "Fizz", "4", "Buzz", "Fizz", "7" }
fizzBuzz(1, 11) → { "1", "2", "Fizz", "4", "Buzz", "Fizz", "7", "8", "Fizz", "Buzz" }
```

### Exercise 2

Consider the leftmost and rightmost appearances of a value in an `ArrayList`. The _span_ is the number of elements between the two, inclusive. A single value has a span of `1`, and an empty `ArrayList` would have a span of `0`. Return the largest span found in the given `ArrayList`. Return `-1` if any of the following conditions is not met.

* The `ArrayList` must not be `null`.

Here are a few sample calls to the `maxSpan` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
maxSpan({ 1, 2, 1, 1, 3 })       → 4
maxSpan({ 1, 4, 2, 1, 4, 1, 4 }) → 6
maxSpan({ 1, 4, 2, 1, 4, 4, 4 }) → 6
```

### Exercise 3

Return an `ArrayList` that contains exactly the same numbers as the given `ArrayList`, but rearranged so that every `3` is immediately followed by a `4`. You are permitted to move every number, except the `3`s. Return `null` if any of the following conditions is not met.

* The `ArrayList` must not be `null`.
* There must be an equal number of `3`s and `4`s in the `ArrayList`.
* At least one `3` must appear in the `ArrayList` before the first `4`.
* Every `3` has a number after it that is not a `4`.

Here are a few sample calls to the `fix34` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
fix34({ 1, 3, 1, 4 })          → { 1, 3, 4, 1 }
fix34({ 1, 3, 1, 4, 4, 3, 1 }) → { 1, 3, 4, 1, 1, 3, 4 }
fix34({ 3, 2, 2, 4 })          → { 3, 4, 2, 2 }
```

### Exercise 4

Return an `ArrayList` that contains exactly the same numbers as the given `ArrayList`, but rearranged so that every `4` is immediately followed by a `5`. You are permitted to move every number, except the `4`s. Return `null` if any of the following conditions is not met.

* The `ArrayList` must not be `null`.
* There must be an equal number of `4`s and `5`s in the `ArrayList`.
* Every `4` has a number after it that is not a `4`.

Here are a few sample calls to the `fix45` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
fix45({ 5, 4, 9, 4, 9, 5 })    → { 9, 4, 5, 4, 5, 9 }
fix45({ 1, 4, 1, 5 })          → { 1, 4, 5, 1 }
fix45({ 1, 4, 1, 5, 5, 4, 1 }) → { 1, 4, 5, 1, 1, 4, 5 }
```

### Exercise 5

Given an `ArrayList`, return `true` if there is a place to split the `ArrayList` so that the sum of the numbers on one side is equal to the sum of the numbers on the other side. Return `false` if this is not possible, or if any of the following conditions is not met.

* The `ArrayList` must not be `null`.
* The `ArrayList` must be non-empty.

Here are a few sample calls to the `canBalance` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
canBalance({ 1, 1, 1, 2, 1 }) → true
canBalance({ 2, 1, 1, 2, 1 }) → false
canBalance({ 10, 10 })        → true
```

### Exercise 6

Given two `ArrayList`s of integers, `outer` and `inner`, return `true` if all of the numbers in `inner` appear in `outer`. An optimal solution would make only a single, linear pass of both `ArrayList`s. Return false if this is not the case, or if any of the following conditions is not met.

* `outer` and `inner` must not be `null`.
* `outer` and `inner` must be non-empty.
* `outer` and `inner` must be sorted in increasing order.

Here are a few sample calls to the `linearIn` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
linearIn({ 1, 2, 4, 6 }, { 2, 4} )    → true
linearIn({ 1, 2, 4, 6 }, { 2, 3, 4 }) → false
linearIn({ 1, 2, 4, 4, 6 }, { 2, 4 }) → true
```

### Exercise 7

Given an integer, `n`, create an `ArrayList` whose length is `n * n` with the following pattern \(shown here for `n = 3`\): `{ 0, 0, 1,     0, 2, 1,     3, 2, 1 }` \(spaces added to emphasize the three groups\). Return `null` if any of the following conditions is not met.

* `n` must be greater than or equal to `0`.

Here are a few sample calls to the `squareUp` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
squareUp(3) → { 0, 0, 1, 0, 2, 1, 3, 2, 1 }
squareUp(2) → { 0, 1, 2, 1 }
squareUp(4) → { 0, 0, 0, 1, 0, 0, 2, 1, 0, 3, 2, 1, 4, 3, 2, 1 }
```

### Exercise 8

Given an integer, `n`, create an `ArrayList` with the following pattern: `{ 1,     1, 2,     1, 2, 3,     ...     1, 2, 3, ...n }` \(spaces added to emphasize the grouping\). The length of the array will be `1 + 2 + 3 + ... + n`. Return `null` if any of the following conditions is not met.

* `n` must be greater than or equal to `0`.

Here are a few sample calls to the `seriesUp` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
seriesUp(3) → { 1, 1, 2, 1, 2, 3 }
seriesUp(4) → { 1, 1, 2, 1, 2, 3, 1, 2, 3, 4 }
seriesUp(2) → { 1, 1, 2 }
```

### Exercise 9

A _mirror_ section in an `ArrayList` is a group of contiguous elements such that somewhere in the `ArrayList`, the same group appears in reverse order. For example, the largest mirror section in `{ 1, 2, 3, 8, 9, 3, 2, 1 }` has a length of `3` \(i.e., the `{ 1, 2, 3 }` segment\). Return the size of the largest mirror section found in the given `ArrayList`. Return `-1` if any of the following conditions is not met.

* The `ArrayList` must not be `null`.

Here are a few sample calls to the `maxMirror` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
maxMirror({ 1, 2, 3, 8, 9, 3, 2, 1 }) → 3
maxMirror({ 1, 2, 1, 4 })             → 3
maxMirror({ 7, 1, 2, 9, 7, 2, 1 })    → 2
```

### Exercise 10

A _clump_ in an `ArrayList` is a series of two or more adjacent elements of the same value. Return the number of _clumps_ in the given `ArrayList`. Return `-1` if any of the following conditions is not met.

* The `ArrayList` must not be `null`.

Here are a few sample calls to the `countClumps` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
countClumps({ 1, 2, 2, 3, 4, 4 }) → 2
countClumps({ 1, 1, 2, 1, 1 })    → 2
countClumps({ 1, 1, 1, 1, 1 })    → 1
```

## Deliverables

1. Submit your repository URL.

Your program output should meet each of the requirements, and should account for test cases above and beyond those provided in the sample executions.

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, February 21, 2021.

