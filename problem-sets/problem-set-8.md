# Problem Set 8

## Summary

For this problem set, we'll be focusing on using built-in methods \(most notably, those of the `String` class\). It is also your first introduction to methods, parameters, and return statements. Each method, including the `main` method, is declared for you. It is your responsibility to implement each method, and test it thoroughly. 

## Requirements

1. Create a repository called `pset-8`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Pull down [the skeleton repository](https://github.com/ucvts/pset-8-4101) containing starter code.
4. Solve each of the exercises, placing each solution in the appropriate method.
5. Add, commit, and push your code to your `pset-8` repository.

## Exercises

The specifications for each exercise are outlined below. Your job is to write code that meets the stated requirements, and matches my output exactly. Work through these exercises on your own. Experiment, make mistakes, ask questions, and fix your mistakes. It's the only way to get good at programming.

Previously, your output was printed to the console. This time, though, you'll be using return statements. To clarify, nothing should be printed to the console and you don't need to use a `Scanner` at all. Correct answers that are printed to the console instead of returned will not be considered.

As a final note, do not modify the method signatures. You can write your code inside of the method bodies, but the names, access modifiers, return types, and parameters must not be altered.

### Exercise 1

Given two arrays of integers called `a` and `b`, return `true` if both arrays have either the same first or same last element. Otherwise, return `false`. You should also return `false` if any of the following conditions is not met.

* `a` must not be `null`.
* `b` must not be `null`.
* `a` must not be empty.
* `b` must not be empty.

Here are a few sample calls to the `common` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
common([1, 2, 3], [7, 3])    → true
common([1, 2, 3], [7, 3, 2]) → false
common([1, 2, 3], [1, 3])    → true
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 2

Given two arrays of integers called `a` and `b`, return a new array containing the middle elements from `a` and `b` \(in that order\). Return `null` if any of the following conditions is not met.

* `a` must not be `null`.
* `b` must not be `null`.
* `a` must not be empty.
* `b` must not be empty.
* `a` must have an odd length.
* `b` must have an odd length.

Here are a few sample calls to the `middleMan` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
middleMan([1, 2, 3, 4, 5], [4, 5, 6]) → [3, 5]
middleMan([7, 7, 7], [3, 3, 3])       → [7, 3]
middleMan([9, 8, 7], [6, 5, 4, 3, 2]) → [8, 4]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 3

Given two arrays of integers called `a` and `b`, return the array whose elements produce the larger sum. Empty arrays will be considered to have a sum of zero. Return `a` in the event of a tie. Return `null` if any of the following conditions is not met.

* `a` must not be `null`.
* `b` must not be `null`.

Here are a few sample calls to the `bigger` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these four.

```java
bigger([1, 2], [3, 4])       → [3, 4]
bigger([3, 4], [1, 2])       → [3, 4]
bigger([1, 1, 3], [1, 2, 2]) → [1, 1, 3]
bigger([], [1])              → [1]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 4

Given two arrays of integers called `a` and `b`, return a new array containing the two middle elements from `a` and `b` \(in that order\). Return `null` if any of the following conditions is not met.

* `a` must not be `null`.
* `b` must not be `null`.
* `a` must not be empty.
* `b` must not be empty.
* `a` must have an even length.
* `b` must have an even length.

Here are a few sample calls to the `doubleMiddle` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
doubleMiddle([1, 2, 3, 4], [1, 2])             → [2, 3, 1, 2]
doubleMiddle([7, 1, 2, 3, 4, 9], [2, 4, 6, 8]) → [2, 3, 4, 6]
doubleMiddle([1, 2], [3, 4])                   → [1, 2, 3, 4]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 5

Given an array of integers called `a`, swap the first and last elements of the array. Return the modified array. Return `null` if any of the following conditions is not met.

* `a` must not be `null`.

Here are a few sample calls to the `swapMe` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
swapMe([1, 2, 3, 4])    → [4, 2, 3, 1]
swapMe([1, 2, 3])       → [3, 2, 1]
swapMe([8, 6, 7, 9, 5]) → [5, 6, 7, 9, 8]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 6

Given an array of integers called `a`, return a new array containing the first, middle, and last element \(in that order\). Return `null` if any of the following conditions is not met.

* `a` must not be `null`.
* `a` must not be empty.
* `a` must have an odd length.

Here are a few sample calls to the `threeProng` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
threeProng([1, 2, 3, 4, 5])       → [1, 3, 5]
threeProng([1, 2, 3])             → [1, 2, 3]
threeProng([1, 2, 3, 4, 5, 6, 7]) → [1, 4, 7]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty strings are all valid inputs. Nothing is off the table.

### Exercise 7

Given an array of integers called `a`, return the largest element in the array. Return `-1` if any of the following conditions is not met.

* `a` must not be `null`.
* `a` must not be empty.
* `a` must contain only non-negative values.

Here are a few sample calls to the `headHoncho` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these two.

```java
headHoncho([1, 2, 3, 4, 5]) → 5
headHoncho([9, 8, 7, 6, 5]) → 9
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 8

Given an array of integers called `a` and an integer called `threshold`, return `true` if the sum of the elements in `a` exceeds the value of `threshold`. Otherwise, return `false`. Return `false` if any of the following conditions is not met.

* `a` must not be `null`.

Here are a few sample calls to the `tippingPoint` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these two.

```java
tippingPoint([1, 2, 3, 4, 5], 10) → true
tippingPoint([1, 2, 3], 20)       → false
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 9

Given an array of integers called `a`, return `LEFT` if the sum of elements on the left half of `a` exceeds the sum of the elements on the right half. Otherwise, return `RIGHT`. Return `null` if any of the following conditions is not met.

* `a` must not be `null`.
* `a` must not be empty.
* `a` must have an even length.

Here are a few sample calls to the `halfway` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
halfway([1, 2, 2, 1]) → "RIGHT"
halfway([2, 1])       → "LEFT"
halfway([4, 5, 9, 1]) → "LEFT"
```

Remember, your code will need to handle atypical cases, too. `null` values and empty arrays are all valid inputs. Nothing is off the table.

### Exercise 10

Given two arrays of integers called `a` and `b`, return a new array of as many of the elements from a followed by as many of the elements of b that will fit in a 3-element array. Return `null` if any of the following conditions is not met.

* `a` must not be `null`.
* `b` must not be `null`.
* `a` and `b` must have a minimum of 3 combined elements.

Here are a few sample calls to the `sequential` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
sequential([1, 2], [3])    → [1, 2, 3]
sequential([2], [3, 4])    → [2, 3, 4]
sequential([5, 6], [7, 8]) → [5, 6, 7]
```

Remember, your code will need to handle atypical cases, too. `null` values and empty strings are all valid inputs. Nothing is off the table.

## Deliverables

1. Submit your repository URL.

Your program output should match mine exactly for each of the exercises above. 

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, January 24, 2021.

