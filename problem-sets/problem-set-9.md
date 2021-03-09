# Problem Set 9

## Summary

For this problem set, we'll be focusing on using another built-in data type: arrays! Each method, with the exception of the `main` method, is declared for you. It is your responsibility to implement each method, and test it thoroughly. 

## Requirements

1. Create a repository called `pset-9`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Pull down [the skeleton repository](https://github.com/ucvts/pset-9-4101) containing starter code.
4. Solve each of the exercises, placing each solution in the appropriate method.
5. Add, commit, and push your code to your `pset-9` repository.

## Exercises

The specifications for each exercise are outlined below. Your job is to write code that meets the stated requirements, and matches my output exactly. Work through these exercises on your own. Experiment, make mistakes, ask questions, and fix your mistakes. It's the only way to get good at programming.

Previously, your output was printed to the console. This time, though, you'll be using return statements. To clarify, nothing should be printed to the console and you don't need to use a `Scanner` at all. Correct answers that are printed to the console instead of returned will not be considered.

As a final note, do not modify the method signatures. You can write your code inside of the method bodies, but the names, access modifiers, return types, and parameters must not be altered.

### Exercise 1

Given an array of integers called `arr`, return an array with the same number of elements. Rearrange the given values so that all of the even numbers come before the odd ones. There is no ordering requirement within the even and odd subsets. Return null if any of the following conditions is not met.

* `arr` must not be `null`.

Here are a few sample calls to the `evenOdd` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these two.

```java
evenOdd([1, 2, 3, 4, 5])    → [2, 4, 1, 3, 5]
evenOdd([1, 2, 3, 3, 2, 1]) → [2, 2, 1, 1, 3, 3]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 2

An array element is considered to be _alone_ if there are values before and after it, but those values are different from it. Return a version of the given array, `arr`, where every instance of the given `alone` value is replaced by the larger of its left or right neighbors. Return null if any of the following conditions is not met.

* `arr` must not be `null`.
* `arr` must not be empty.

Here are a few sample calls to the `notAlone` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these two.

```java
notAlone([1, 2, 3], 2)          → [1, 3, 3]
notAlone([1, 2, 3, 2, 5, 2], 2) → [1, 3, 3, 5, 5, 2]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 3

Given an array of integers called `arr`, return an array that is left-shifted by one element. Return `null` if any of the following conditions is not met.

* `arr` must not be `null`.

Here are a few sample calls to the `shiftLeft` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these two.

```java
shiftLeft([6, 2, 5, 3]) → [2, 5, 3, 6]
shiftLeft([1, 2])       → [2, 1]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 4

Given two integers, `start` and `end`, return a new array with the sequence of integers in `[start, end)`. Return `null` if any of the following conditions is not met.

* `start` must be less than or equal to `end`.

Here are a few sample calls to the `fillIn` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
fillIn(5, 10) → [5, 6, 7, 8, 9]
fillIn(1, 2) → [1]
fillIn(1, 1)  → []
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 5

Given an array of integers called `arr`, return `true` if the value `3` appears in `arr` exactly three times. Otherwise, return `false`. Return `false` if any of the following conditions is not met.

* `arr` must not be `null`.

Here are a few sample calls to the `triple` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these two.

```java
triple([1, 3, 1, 3, 1, 3]) → true
triple([1, 2, 3, 1, 2, 3]) → false
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 6

Given two arrays called `a` and `b`, consider corresponding pairs elements in `a` and `b` \(at the same index\). Return the number of times that the two elements differ by fewer than three, but are not equal. Return `-1` if any of the following conditions is not met.

* `a` must not be `null`.
* `b` must not be `null`.
* `a` and `b` must have the same length.

Here are a few sample calls to the `pairs` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
pairs([1, 2, 3], [2, 3, 9]) → 2
pairs([1, 2, 3], [2, 3, 5]) → 3
pairs([1, 2, 3], [1, 2, 3]) → 0
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 7

Given an array of integers call `arr`, return `true` if the array contains a 2 next to a 2 or a 4 next to a 4, but not both. Otherwise, return `false`. Return `false` if any of the following conditions is not met.

* `a` must not be `null`.

Here are a few sample calls to the `twentyFour` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
twentyFour([1, 2, 2])       → true
twentyFour([4, 4, 1])       → true
twentyFour([4, 4, 1, 2, 2]) → false
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 8

Given an array of integers called `arr`, return `true` if every element is either a 1 or a 4. Otherwise, return `false`. Return `false` if any of the following conditions is not met.

* `arr` must not be `null`.

Here are a few sample calls to the `fourteen` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these two.

```java
fourteen([1, 2, 3, 4, 5]) → false
fourteen([1, 1, 1])       → true
fourteen([1, 4, 4, 1])    → true 
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 9

The _centered average_ is the average of all elements in an array, with the exception of the largest and smallest values. Given an array of integers called `arr`, return the centered average of the array. Return `-1` if any of the following conditions is not met.

* `arr` must not be `null`.
* `arr` must have a length of at least 3.

Here are a few sample calls to the `centeredAverage` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
centeredAverage([1, 2, 3, 4, 100])        → 3
centeredAverage([1, 1, 5, 5, 10, 8, 7])   → 5
centeredAverage([-10, -4, -2, -4, -2, 0]) → -3
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 10

Given an array called `arr`, return the difference between the largest and smallest values in the array. Return `-1` if any of the following conditions is not met.

* `arr` must not be `null`.
* `arr` must have a length of at least 1.

Here are a few sample calls to the `outliers` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
outliers([10, 3, 5, 6]) → 7
outliers([7, 2, 10, 9]) → 8
outliers([2, 10, 7, 2]) → 8
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

## Deliverables

1. Submit your repository URL.

Your program output should match mine exactly for each of the exercises above. 

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, January 24, 2021.

