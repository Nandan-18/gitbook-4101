# Problem Set 13

## Summary

For this problem set, we'll be focusing on recursive problems and solutions. Each method, with the exception of the `main` method, is declared for you. It is your responsibility to implement each method, and test it thoroughly.

## Requirements

1. Create a repository called `pset-13`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Pull down [the skeleton repository](https://github.com/ucvts/pset-13-4101) containing starter code.
4. Solve each of the exercises, placing each solution in the appropriate method.
5. Add, commit, and push your code to your `pset-13` repository.

## Exercises

The specifications for each exercise are outlined below. Your job is to write code that meets the stated requirements, and matches my output exactly. Work through these exercises on your own. Experiment, make mistakes, ask questions, and fix your mistakes. It's the only way to get good at programming.

Previously, your output was printed to the console. This time, though, you'll be using return statements. To clarify, nothing should be printed to the console and you don't need to use a `Scanner` at all. Correct answers that are printed to the console instead of returned will not be considered.

As a final note, do not modify the method signatures. You can write your code inside of the method bodies, but the names, access modifiers, return types, and parameters must not be altered.

To be clear, it is possible to craft solutions to each of these problems using iteration. There are also certain built-in methods that may perform the computations for you. Neither of those are the purpose of this problem set. You **must** use recursion for each of your solutions!

### Exercise 1

Given an array of integers, is it possible to choose a subset of these integers, such that the group's sum is equal to a given `target`? This is a classic backtracking recursion problem. Rather than focusing on the entire array, the convention here will be to look at the subsection of the array starting at `start` and continuing to the end of the array.

You may make the following assumptions.

* `start` will always be greater than or equal to `0`.
* `start` will never exceed the maximum valid index of `numbers`.

Here are a few sample calls to the `groupSum` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
groupSum(0, [2, 4, 8], 10) → true
groupSum(0, [2, 4, 8], 14) → true
groupSum(0, [2, 4, 8], 9)  → false
```

### Exercise 2

Given an array of integers, is it possible to choose a subset of these integers, such that the group's sum is equal to a given `target`? This is a lot like the last one, with one added constraint: every `6` in `numbers` must be included in your chosen group.

You may make the following assumptions.

* `start` will always be greater than or equal to `0`.
* `start` will never exceed the maximum valid index of `numbers`.

Here are a few sample calls to the `groupSum6` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
groupSum6(0, [5, 6, 2], 8) → true
groupSum6(0, [5, 6, 2], 9) → false
groupSum6(0, [5, 6, 2], 7) → false
```

### Exercise 3

Given an array of integers, is it possible to choose a subset of these integers, such that the group's su, is equal to a given `target`? This is a lot like the first one, with one added constraint: if a value in `numbers` is chosen to be in the group, the value immediately following it in `numbers` cannot be chosen.

You may make the following assumptions.

* `start` will always be greater than or equal to `0`.
* `start` will never exceed the maximum valid index of `numbers`.

Here are a few sample calls to the `groupNoAdj` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
groupNoAdj(0, [2, 5, 10, 4], 12) → true
groupNoAdj(0, [2, 5, 10, 4], 14) → false
groupNoAdj(0, [2, 5, 10, 4], 7)  → false
```

### Exercise 4

Given an array of integers, is it possible to choose a subset of these integers, such that the group's sum is equal to a given `target`? Again, a lot like the first one, with two added constraints: 1\) all multiples of `5` that are present in `numbers` must be included in the group, and 2\) if the value immediately following a multiple of `5` in `numbers` is a `1`, it cannot be chosen.

You may make the following assumptions.

* `start` will always be greater than or equal to `0`.
* `start` will never exceed the maximum valid index of `numbers`.

Here are a few sample calls to the `groupSum5` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
groupSum5(0, [2, 5, 10, 4], 19) → true
groupSum5(0, [2, 5, 10, 4], 17) → true
groupSum5(0, [2, 5, 10, 4], 12) → false
```

### Exercise 5

Given an array of integers, it is possible to choose a subset of these integers, such that the group's su, is equal to a given `target`? You guessed it, another added constraint to the first exercise: if there are identical values in `numbers` that are adjacent to one another, they either must all be chosen, or none can be chosen. Consider the following example arrays.

```java
{ 1, 2, 3, 3, 3, 4, 5 }   // either all 3s must be chosen, or none can be chosen
{ 7, 7, 7, 3, 1, 3, 7 }   // either all of the leading 7s must be chosen, or none can be chosen
```

You may make the following assumptions.

* `start` will always be greater than or equal to `0`.
* `start` will never exceed the maximum valid index of `numbers`.

Here are a few sample calls to the `groupSumClump` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
groupSumClump(0, [2, 4, 8], 10)       → true
groupSumClump(0, [1, 2, 4, 8, 1], 14) → true
groupSumClump(0, [2, 4, 4, 8], 14)    → false
```

### Exercise 6

Given an array of integers, is it possible to divide the integers into two groups, such that the sums of the two groups are equal? Every value must be in either one group or other. It might be useful to write a recursive helper method for this.

You may make the following assumptions.

* `numbers` will never be `null`.
* It is possible to split an empty array in the manner requested.
* It is not possible to split a single-element array in the manner requested.

Here are a few sample calls to the `splitArray` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
splitArray([2, 2])    → true
splitArray([2, 3])    → false
splitArray([5, 2, 3]) → true
```

### Exercise 7

Given an array of integers, is it possible to divide the integers into two groups, such that the sum of one group is a multiple of `10` and the sum of the other group is odd? Every value must be in either one group or the other. It might be useful to write a recursive helper method for this.

You may make the following assumptions.

* `numbers` will never be `null`.
* It is not possible to split an empty array in the manner requested.
* It is possible to split a single-element array in the manner requested.

Here are a few sample calls to the `splitOdd10` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
splitOdd10([5, 5, 5])    → true
splitOdd10([5, 5, 6])    → false
splitOdd10([5, 5, 6, 1]) → true
```

## Deliverables

1. Submit your repository URL.

Your program output should meet each of the requirements, and should account for test cases above and beyond those provided in the sample executions.

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, March 14, 2021.

