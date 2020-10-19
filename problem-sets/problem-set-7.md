# Problem Set 7

## Summary

For this problem set, we'll be focusing on using built-in methods \(most notably, those of the `String` class\). It is also your first introduction to methods, parameters, and return statements. Each method, including the `main` method, is declared for you. It is your responsibility to implement each method, and test it thoroughly. 

## Requirements

1. Create a repository called `pset-7`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Pull down [the skeleton repository](https://github.com/ucvts/pset-7-4101) containing starter code.
4. Solve each of the exercises, placing each solution in the appropriate method.
5. Add, commit, and push your code to your `pset-7` repository.

## Exercises

The specifications for each exercise are outlined below. Your job is to write code that meets the stated requirements, and matches my output exactly. Work through these exercises on your own. Experiment, make mistakes, ask questions, and fix your mistakes. It's the only way to get good at programming.

Previously, your output was printed to the console. This time, though, you'll be using return statements. To clarify, nothing should be printed to the console and you don't need to use a `Scanner` at all. Correct answers that are printed to the console instead of returned will not be considered.

As a final note, do not modify the method signatures. You can write your code inside of the method bodies, but the names, access modifiers, return types, and parameters must not be altered.

### Exercise 1

Given two strings, return a new string built by surrounding `in` with the first and last two characters of `out`. Return `in` unchanged if any of the following requirements are not met.

* `in` must not be `null`.
* `out` must not be `null`.
* `out` must be exactly 4 characters.

Here are a few sample calls to the `surroundMe` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these four.

```java
surroundMe("cde", "abfg") → "abcdefg"
surroundMe(null, "####")  → null
surroundMe("abc", null)   → "abc"
surroundMe("abc", "123")  → "abc"
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

### Exercise 2

Given a string and an integer, return a new string that represents the first and last `n` characters of `text` \(overlapping, as needed\). Return `text` unchanged if any of the following requirements are not met.

* `text` must not be `null`.
* `text` must have a length between 1 and 10 \(inclusive\).
* `n` must be a positive integer between 1 and the length of `text` \(inclusive\).

Here are a few sample calls to the `endsMeet` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these four.

```java
endsMeet("abcdefg", 2) → "abfg"
endsMeet(null, 2)      → null
endsMeet("", 2)        → ""
endsMeet("abc", -1)    → "abc"
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, special characters \(e.g., escape sequences\), and negative numbers are all valid inputs. Nothing is off the table.

### Exercise 3

Given a string, return a new string using the middle three characters of `text`. Return `text` unchanged if any of the following requirements are not met.

* `text` must not be `null`.
* `text` must have an odd length of at least 3 characters.

Here are a few sample calls to the `middleMan` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these four.

```java
middleMan("abcdefg") → "cde"
middleMan(null)      → null
middleMan("12")      → "12"
middleMan("a")       → "a"
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

### Exercise 4

Given two strings, determine whether or not `target` is equivalent to the middle three characters of `text`. Return `false` if any of the following requirements are not met.

* `text` must not be `null`.
* `text` must have an odd length of at least 3 characters.
* `target` must not be `null`.
* `target` must be exactly 3 characters.

Here are a few sample calls to the `isCentered` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these six.

```java
isCentered("abcdefg", "cde") → true
isCentered("abcdefg", "abc") → false
isCentered(null, "abc")      → false
isCentered("abcd", "abc")    → false
isCentered("abc", null)      → false
isCentered("abcdefg", "cd")  → false
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

### Exercise 5

Given a string and a character, compute the number of words that end in `suffix`. Return `-1` if any of the following requirements are not met.

* `text` must not be `null`.
* `suffix` must be a character in the English alphabet.

Treat the `suffix` case-sensitively. A word is defined as a sequence of characters that starts and ends in a single space. The only exception to this is if the word is either the first or last word in the string. There will never be more than one consecutive space in the string, and no other whitespace characters will appear in the string.

Here are a few sample calls to the `countMe` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
countMe("I am an example sentence", 'e') → 2
countMe(null, 'a')                       → -1
countMe("abc$ def$", '$')                → -1
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

### Exercise 6

Given a string, compute the number of triplets in `text`. Return `-1` if any of the following requirements are not met.

* `text` must not be `null`.

A triplet is defined as the appearance of three consecutive characters \(e.g., `"aaa"`\). Triplets are case-sensitive, meaning `"aaa"` is not the same as `"AAA"`.

Here are a few sample calls to the `triplets` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these four.

```java
triplets("aaabbbccc") → 3
triplets("aaaa")      → 2
triplets("abc")       → 0
triplets(null)        → -1
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

### Exercise 7

Given a string, compute the sum of the digits in `text`. Return `-1` if any of the following requirements are not met.

* `text` must not be `null`.

Ignore characters that are not digits. All digits are assumed to be positive.

Here are a few sample calls to the `addMe` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
addMe("123 abc 123") → 12
addMe("abcdefghijk") → 0
addMe(null)          → -1
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

### Exercise 8

Given a string, compute the length of the longest sequence. Return `-1` if any of the following requirements are not met.

* `text` must not be `null`.

A sequence is defined as one or more consecutive characters. These characters must be identical, and are case-sensitive.

Here are a few sample calls to the `sequence` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these four.

```java
sequence("abbcccdddd") → 4
sequence("aAabBbBb")   → 1
sequence("")           → 0
sequence(null)         → -1
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

### Exercise 9

Given two strings, return a new string built by intertwining each of the characters of `a` and `b`. Return `null` if any of the following requirements are not met.

* `a` must not be `null`.
* `b` must not be `null`.

Here are a few sample calls to the `intertwine` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these five.

```java
intertwine("aceg", "bdfh") → "abcdefgh"
intertwine("abc", "12345") → "a1b2c345"
intertwine(null, "abcd")   → null
intertwine("abcd", null)   → null
intertwine(null, null)     → null
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

### Exercise 10

Given a string, determine whether or not it is a palindrome. Return `false` if any of the following requirements are not met.

* `text` must not be `null`.

A palindrome is case-sensitive sequence that is spelled identically forwards and backwards. Use of the `StringBuilder` or `StringBuffer` classes is strictly prohibited.

Here are a few sample calls to the `isPalindrome` method, along with their expected outputs. It is your responsibility to make sure your code works as expected for **all** possible inputs, not just these three.

```java
isPalindrome("racecar") → true
isPalindrome("Madam")   → false
isPalindrome(null)      → false
```

Remember, your code will need to handle atypical cases, too. `null` values, empty strings, and special characters \(e.g., escape sequences\) are all valid inputs. Nothing is off the table.

## Deliverables

1. Submit your repository URL.

Your program output should match mine exactly for each of the exercises above. 

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, October 25, 2020.

