# Problem Set 6

## **Summary**

Solve each exercise so that your output matches the expected output. Each exercise should be written in the `main` method of its own class. Follow a file naming convention of `ExerciseX.java`, where `X` is 1 through 10, for each class file.

## Requirements

1. Create a new repository called `pset-6`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Solve each of the exercises, placing each solution in its own file.
4. Add, commit, and push your code to the `pset-6` repository.

## Exercises

The specifications for each exercise are outlined below. Your job is to write code that meets the stated requirements, and matches my output exactly. Work through these exercises on your own. Experiment, make mistakes, ask questions, and fix your mistakes. It's the only way to get good at programming.

### Exercise 1

Prompt the user to enter two integers. The first is a lower bound, and the second is an upper bound. Compute the sum of all even integers between these bounds, inclusive.

* Accept all values in the range of an `int`.
* Restrict the upper bound to values greater than or equal to the lower bound, continuously re-prompting the user until this requirement is satisfied.
* Format the sum with separating commas, as needed.

```text
Lower bound: 1
Upper bound: -1
Lower bound: 0
Upper bound: 100

2,550.
```

### Exercise 2

Prompt the user to enter a positive integer, and print the digits of this integer in reverse order.

* Accept only positive values in the range of an `int`, continuously re-prompting the user until this requirement is satisfied.

```text
Enter an integer: -1
Enter an integer: 0
Enter an integer: 207414

4, 1, 4, 7, 0, 2.
```

### Exercise 3

Prompt the user to enter a positive integer. Compute the sum of all of the odd digits in the integer.

* Accept only positive values in the range of an `int`, continuously re-prompting the user until this requirement is satisfied.
* Format the sum with separating commas, as needed.

```text
Enter an integer: -1
Enter an integer: 0
Enter an integer: 929409

27.
```

### Exercise 4

Prompt the user to enter a series of non-negative integers. When the user enters a negative integer, you can assume he or she is done entering values. Compute the average of the values entered. There are two possible outputs.

* `#,###.##.`
* `Error: division by zero.`

It is unacceptable for your program to crash because you mistakenly divided by zero.

* Accept only non-negative values in the range of an `int`.
* Display exactly two decimal places.
* Format the average with separating commas, as needed.

```text
Enter an integer: 20702
Enter an integer: 41414
Enter an integer: 92929
Enter an integer: 40904
Enter an integer: -1

48,987.25
```

### Exercise 5

Prompt the user to enter a non-negative integer, and determine its primality. There are two possible outputs.

* `Prime.`
* `Not prime.`

There is more than one way to do this, and some solutions are more elegant than others.

* Accept only non-negative values in the range of an `int`, continuously re-prompting the user until this requirement is satisfied.

```text
Enter an integer: -1
Enter an integer: 997

Prime.
```

### Exercise 6

Prompt the user to enter a non-negative integer. If the integer the user enters is called `n`, determine the `n`th Fibonacci number.

* Accept all non-negative integer values in the range `[1, 92]`, continuously re-prompting the user until this requirement is satisfied.
* Format the number with separating commas, as needed.

```text
Enter an integer: -1
Enter an integer: 93
Enter an integer: 11

55.
```

### Exercise 7

Prompt the user to enter a positive integer, and list its factors.

* Accept only positive values in the range of an `int`, continuously re-prompting the user until this requirement is satisfied.
* Print each pair of factors only once.
* List the factors in order ascending order by the first factor in the pair.

```text
Enter an integer: -1
Enter an integer: 0
Enter an integer: 20

1, 20, 2, 10, 4, 5.
```

### Exercise 8

Prompt the user to enter an integer, and print a Super Mario-style half-pyramid of the specified height.

* Accept only positive values in the range `[1, 24]`, continuously re-prompting the user until this requirement is satisfied.

```text
Height: 25
Height: 0
Height: 7

      ##
     ###
    ####
   #####
  ######
 #######
########
```

### Exercise 9

Prompt the user to enter an integer, and print a Super Mario-style full pyramid of the specified height.

* Accept only positive values in the range `[1, 24]`, continuously re-prompting the user until this requirement is satisfied.
* Print exactly two spaces between the left and right halves of the pyramid.

```text
Height: 25
Height: 0
Height: 7

      ##  ##
     ###  ###
    ####  ####
   #####  #####
  ######  ######
 #######  #######
########  ########
```

### Exercise 10

Prompt the user to enter a credit card number \(not a real one!\). Using [Luhn's algorithm](https://en.wikipedia.org/wiki/Luhn_algorithm), determine the type of credit card the user entered. There are four possible outputs.

* `American Express.`
* `Mastercard.`
* `Visa.`
* `Invalid.`

Luhn's algorithm works as follows.

1. Multiply every other digit of the card number by two, starting with the second-to-last digit.
2. Add the products of those digits.
3. Add the digits that were not initially multiplied by two.
4. Add the sums from steps two and three.
5. If the last digit of the sum from step four is a zero, then the card number is valid.

* American Express uses 15-digit numbers, starting with `34` or `37`.
* Mastercard uses 16-digit numbers, starting with `51`, `52`, `53`, `54`, or `55`.
* Visa uses 13- or 16-digit numbers, starting with `4`.

Here's an example using an American Express card number: `378282246310005`.

First, you should identify the digits to be multiplied: every other digit, starting with the second-to-last digit \(marked with asterisks\).

```text
3 *7* 8 *2* 8 *2* 2 *4* 6 *3* 1 *0* 0 *0* 5
```

Now, multiply these digits by two.

```text
7 x 2, 2 x 2, 2 x 2, 4 x 2, 3 x 2, 0 x 2, and 0 x 2
```

Now, you have the products.

```text
14, 4, 4, 8, 6, 0, and 0
```

You need to add the digits of these products \(not the products themselves\).

```text
1 + 4 + 4 + 4 + 8 + 6 + 0 + 0 = 27
```

Next, add that sum \(i.e., 27\) to the sum of the digits that weren't multiplied by two.

```text
27 + 3 + 8 + 8 + 2 + 6 + 1 + 0 + 5 = 60
```

Since the checksum ends in in a zero, then the card number is valid. Because the original number is 15 digits and starts with a 37, it is an `American Express`.

Here a few examples you can use for testing.

* `378282246310005` and `371449635398431` should verify as `American Express.`
* `5555555555554444` and `5105105105105100` should verify as `Mastercard.`
* `4111111111111111` and `4012888888881881` should verify as `Visa.`

```text
Enter credit card number: 4012888888881881

Visa.
```

## Deliverables

1. Submit your repository URL.

Your program output should match mine exactly for each of the exercises above.

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, October 18, 2020.

