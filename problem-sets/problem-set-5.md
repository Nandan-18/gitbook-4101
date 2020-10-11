# Problem Set 5

## **Summary**

Solve each exercise so that your output matches the expected output. Each exercise should be written in the `main` method of its own class. Follow a file naming convention of `ExerciseX.java`, where `X` is 1 through 10, for each class file.

## Requirements

1. Create a new repository called `pset-5`.
2. Mark your repository as private, and add me as a collaborator \(`ryanjwilson`\).
3. Solve each of the exercises, placing each solution in its own file.
4. Add, commit, and push your code to the `pset-5` repository.

## Exercises

The specifications for each exercise are outlined below. Your job is to write code that meets the stated requirements, and matches my output exactly. Work through these exercises on your own. Experiment, make mistakes, ask questions, and fix your mistakes. It's the only way to get good at programming.

### Exercise 1

Prompt the user to enter an integer, and determine whether it is positive, negative, or zero. There are three possible outputs.

* `Positive.`
* `Negative.`
* `Zero.`

Remember, capitalization and punctuation count!

* Accept all values in the range of an `int`.

```text
Enter an integer: 12

Positive.
```

### Exercise 2

Prompt the user to enter an integer, and determine whether it is even or odd. There are two possible outputs.

* `Even.`
* `Odd.`

Remember, zero is an even number. And capitalization and punctuation count!

* Accept all values in the range of an `int`.

```text
Enter an integer: 3

Odd.
```

### Exercise 3

Prompt the user to enter three integers, and determine their relative ordering. There are six possible outputs.

* Strictly increasing., where each integer is greater than the previous one.
* Increasing., where each integer is greater than or equal to the previous one.
* Same., where all three integers are equal to one another.
* Decreasing., where each integer is less than or equal to the previous one.
* Strictly decreasing., where each integer is lass than the previous one.
* Unordered., where none of the above applies.

Remember, capitalization and punctuation count!

* Accept all values in the range of an `int`.

```text
Enter three integers.

Enter integer: 1
Enter integer: 3
Enter integer: 7

Strictly increasing.
```

### Exercise 4

Prompt the user to enter a letter grade, and determine the corresponding GPA. There are two possible outputs.

* `Your GPA is #.##.`
* `That's not a valid letter grade.`

Letter grades are given the following numeric equivalents.

* `A` is worth `4.00` points.
* `B` is worth `3.00` points.
* `C` is worth `2.00` points.
* `D` is worth `1.00` points.
* `F` is worth `0.00` points.

Letter grades may or may not be suffixed with a `+` or `-`. With a few exceptions, a `+` adds `0.33` points to the baseline value of that letter, while a `-` subtracts `0.33` points.

* `F-` is not a valid letter grade.
* `F+` is not a valid letter grade.
* `4.00` is the maximum grade point.

Remember, capitalization and punctuation count!

* Accept capital and lowercase letters.

```text
Enter a letter grade: B+

Your GPA is 3.33.
```

### Exercise 5

Prompt the user to enter a numeric grade, and determine the corresponding letter grade. There are four possible outputs.

* `You received a X.`
* `You received an X.`
* `Grades above 100 are invalid.`
* `Grades below 0 are invalid.`

The grading policy is defined as follows.

* `90` to `100` constitutes an `A`.
* `80` to `89` constitutes a `B`.
* `70` to `79` constitutes a `C`.
* `60` to `69` constitutes a `D`.
* `0` to `59` constitutes an `F`.

All other grades are invalid.

* Accept fractional values, but round them to the nearest whole number.

```text
Enter a grade: 79.7

You received a B.
```

### Exercise 6

Prompt the user to enter a playing card, and determine which card was entered. There are four possible suits.

* `Clubs`
* `Diamonds`
* `Hearts`
* `Spades`

And there are 13 possible ranks.

* `Two`
* `Three`
* `Four`
* `Five`
* `Six`
* `Seven`
* `Eight`
* `Nine`
* `Ten`
* `Jack`
* `Queen`
* `King`
* `Ace`

Possible inputs will be a combination of ranks and suits, where ranks are written as `2-9`, `T`, `J`, `Q`, `K`, or `A`, and suits are written as `C`, `D`, `H`, or `S`. There are four possible outputs.

* `Rank of Suit.`
* `That's not a valid suit.`
* `That's not a valid rank.`
* `That's not a valid card.`

You should check that the input can be processed as a possible card first \(i.e., the input must be exactly two characters\). Next, you should check the rank, and print the associated error message \(and only that error message\) if applicable. Finally, you should check the suit and print the error message associated with invalid suits.

Remember, capitalization and punctuation count!

* Accept capital and lowercase letters.

```text
Enter a playing card: AS

Ace of Spades.
```

### Exercise 7

Prompt the user to enter a year, and determine whether or not it is a leap year. There are two possible outputs.

* `X is a leap year.`
* `X is not a leap year.`

You'll have to figure out the logic for determining leap years.

* Accept all non-negative values in the range of an `int`.

```text
Enter a year: 2020

2020 is a leap year.
```

### Exercise 8

Prompt the user to enter a temperature, and determine if water is a solid, liquid, or gas at that temperature. There are four possible outputs.

* `Solid.`
* `Liquid.`
* `Gas.`
* `That's not a valid scale.`

Your code must support Celsius and Fahrenheit temperatures, which are designated by the scale \(`C` for Celsius, and `F` for Fahrenheit\) following the temperature value.

Remember, capitalization and punctuation count! Oh, and you might want to look into how to convert a `String` to a number...

* Accept whole numbers or fractional values.
* Accept capital and lowercase letters.

```text
Enter a temperature: 211 F

Liquid.
```

### Exercise 9

Prompt the user to enter a month, and determine how many days are in that month. There are four possible outputs.

* `28 or 29 days.`
* `30 days.`
* `31 days.`
* `That's not a valid month.`

Remember, capitalization and punctuation count!

* Accept months that are written in their entirety, abbreviated to the first three, or abbreviated to the first four letters.
* Accept capital and lowercase letters.

```text
Enter a month: February

28 or 29 days.
```

### Exercise 10

Prompt the user to enter a wage and a number of hours worked, and determine how much money will be made. There are three possible outputs.

* `You'll make $#,###.## this week.`
* `Your wage must be greater than or equal to $0.00/hour.`
* `Your hours must be greater than or equal to 0.0.`

You may assume that the first 40 hours are paid at the regular rate, whereas any hours in excess of 40 are paid at time-and-a-half \(i.e., 1.5 times the regular rate\).

* Display exactly two decimal places.
* Format the money earned with separating commas, as needed.

```text
Enter wage: 17.75
Enter hours worked: 52

You'll make $1,029.50 this week.
```

## Deliverables

1. Submit your repository URL.

Your program output should match mine exactly for each of the exercises above.

## Deadline

All submissions are due on Canvas by 11:59pm on Sunday, October 11, 2020.

