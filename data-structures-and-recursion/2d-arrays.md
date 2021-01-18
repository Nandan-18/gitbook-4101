# 2D Arrays

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 3.10
{% endhint %}

## Declaring 2D Arrays

There are a few different ways to think of a 2D array. Some people like to think of it as a matrix, a grid, or an array of arrays \(which it is\). However you choose to visualize it is up to you, but let's talk about how to declare one.

Just like an array of one dimension, you declare its data type and name. For the data type, we'll use a primitive or object type followed by two sets of brackets.

```java
int[][] numbers;      // an array of arrays of ints
double[][] grades;    // an array of arrays of doubles
String[][] words;     // an array of arrays of Strings
```

Each of these statements declares an array with a specific variable name \(i.e., `numbers`, `grades`, and `words`\) and data type \(i.e., `int`, `double`, and `String`\). The two sets of square brackets following the data type indicate that this variable will refer to an array of arrays of values of that type.

In their current states, these arrays do not store any values. They've been declared, but need to be initialized with values like any other variable in Java.

{% embed url="https://www.youtube.com/watch?v=oN\_KEbq3U14&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## Creating and Initializing 2D Arrays

Typically, we need to create our array of arrays before we can initialize it with values. The creation step is different than the declaration step, so don't confuse the two.

When working with arrays, we need to tell the compiler how large of a list we'll need \(i.e., how many subarrays and how many elements do we need to store in each subarray\). This is often referred to as the _length_ of the array.

```java
int[][] numbers;           // remember, this declares the array of arrays
numbers = new int[5][5];   // and this creates it with 5 subarrays of length 5
```

This tells the compiler that our `numbers` array needs to store up to 5 subarrays, each of which can store up to 5 values. This instructs the virtual machine to allocate enough memory to accommodate for this.

Naturally, you can condense the declaration and creation statements into one.

```java
int[][] numbers = new int[5][5];
```

Now that we've created our array, it's time to put some data into it. This is called initialization, and to do it we need to understand a little more about the underlying structure of an array. Remember, we can think of it as a list. This list is indexed, though, meaning it is essentially divided into numbered slots \(called _indexes_\).

Use the name of the array along with the desired index to put a value into the array.

```java
numbers[0] = new int[] { 1, 2, 3, 4, 5 };    // initializes the first subarray
numbers[1] = new int[] { 5, 4, 3, 2, 1 };    // initializes the second subarray
```

This is called bracket notation, and among other things, it is used to write data to specific indexes of an array. The first bracket references a specific subarray \(sometimes called a row\). The second bracket references a specific element in that subarray \(sometimes called a column\).

A visualization of this 2D array might look something like this.

```java
[
    [ 1, 2, 3, 4, 5 ],
    [ 5, 4, 3, 2, 1 ],
    [ 0, 0, 0, 0, 0 ],
    [ 0, 0, 0, 0, 0 ],
    [ 0, 0, 0, 0, 0 ]
]
```

The outer brackets represent the main array, while the inner brackets represent each subarray. Remember, only the first two subarrays were initializes with values. The remaining three store only the default values \(all zeroes\).

## Getting and Setting Values

To access an element of an array, we use the same bracket notation we used to initialize.

```java
numbers[0] = new int[] { 1, 2, 3, 4, 5 };    // initializes the first subarray
numbers[1] = new int[] { 5, 4, 3, 2, 1 };    // initializes the second subarray
```

Using our `numbers` array, we can access any index we'd like.

```java
int x = numbers[1][2];    // gets the element at row 1, column 2

// row 1 is the subarray at index 1, and column 2 is the index in that subarray
// this refers to the value 4, which is stored in x

// remember how our 2D array was initialized?

numbers[1] = new int[] { 5, 4, 3, 2, 1 };    // initializes the second subarray
//                          ^
//                   row 1, column 2
```

We can also visualize this using our grid representation of the 2D array.

```java
[[ 1, 2, 3, 4, 5 ],    // row 0
 [ 5, 4, 3, 2, 1 ],    // row 1
 [ 0, 0, 0, 0, 0 ],    // row 2
 [ 0, 0, 0, 0, 0 ],    // row 3
 [ 0, 0, 0, 0, 0 ]]    // row 4
//    ^
// column 2

// individual cells are referenced like grid coordinates (row, column)
```

Just like regular arrays, both the rows and columns are zero-indexed. An invalid row or column \(either a negative value or one that exceeds the bounds\) will result in an `ArrayIndexOutOfBoundsException`. The last available index is always one less than the length of the array \(or subarray\).

## Traversing a 2D Array

Array traversals are simple enough. We just need to add another layer to traverse a 2D array. Nested loops come into play when working with arrays of more than one dimension.

{% embed url="https://www.youtube.com/watch?v=zZWZNSeys\_4&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

### Traditional `for` Loop

Since arrays have numeric indexes, we can use the loop counter of a `for` loop to access its elements one-by-one. And remember the _length_ of an array. Well, there's a formal `length` property we can use to make sure we don't exceed the bounds of the array.

```java
for (int i = 0; i < numbers.length; i++) {           // rows
    for (int j = 0; j < numbers[i].length; j++) {    // columns in row
        System.out.println("Row " + i + ", Col " + j + ": " + numbers[i][j]);
    }
}
```

This will print a message for each value in `numbers`. It will start with the first row and print every value in that subarray, before moving on the to second row. This continues until the nested `for` loop prints each value of each subarray.

### Enhanced `for` Loop

There is another type of loop that is particularly useful when working with arrays. It's called an enhanced `for` loop. It works very much like a traditional `for` loop, but streamlines the syntax needed.

```java
for (int[] list : numbers) {
    for (int value : list) {
        // value represents each value in each subarray in numbers
    }
}
```

`value` is a placeholder for each element in `numbers`. The enhanced `for` loop automatically advances to the next element in the array, so it's a convenient way to iterate over an array from start to finish.

## Common Algorithms

There are a number of common algorithms that make use of 2D arrays, and they're not all that different than those we discussed in reference to ordinary arrays.

### Summations

A common task with arrays of numeric data is finding the sum of all of the elements. Using some basic math and a loop, this is can be done in a fairly routine manner.

```java
int[][] matrix = {
    { 2, 4, 6, 8 },
    { 1, 3, 7, 9 }
};

int sum = 0;
for (int[] list : matrix) {
    for (int number : list) {
        sum = sum + number;
    }
}

System.out.println("Sum: " + sum);
```

This, of course, could have been done using a traditional `for` loop \(or even a `while` loop\), too.

### Averages

Averaging a set of numbers only takes an extra step or two beyond summing them.

```java
int[][] matrix = {
    { 2, 4, 6, 8 },
    { 1, 3, 7, 9 }
};

int sum = 0;
int count = 0;

for (int[] list : matrix) {
    for (int number : list) {
        sum = sum + number;
        count++;
    }
}

if (count > 0) {
    double average = (double) sum / count;
    
    System.out.println("Average: " + average);
}
```

The first 14 lines are just the summation steps. Next comes the averaging. We check that the list wasn't empty and we summed at least one number \(otherwise we'd get a division by zero error\). And we also cast one of the operands to a `double`. We're working with `ints`, but we want our average to support decimal points.

### Minimums and Maximums

It's an age-old question. We have a large list of numbers. What's the smallest number? What's the largest? Let's find out.

```java
int[][] matrix = {
    { 2, 4, 6, 8 },
    { 1, 3, 7, 9 }
};

if (matrix.length > 0 && matrix[0].length > 0) {
    int min = matrix[0][0];
    
    for (int[] list : matrix) {
        for (int number : list) {
            if (number < min) {
                min = number;
            }
        }
    }
    
    System.out.println("Minimum: " + min);
}
```

Sometimes, you might be asked to find the _index_ at which the minimum \(or maximum\) value exists. In that case, you'd need to use a traditional `for` loop so you have access to array indexes as you go.

Rewriting this to support finding the maximum value requires only a couple code changes.

```java
int[][] matrix = {
    { 2, 4, 6, 8 },
    { 1, 3, 7, 9 }
};

if (matrix.length > 0 && matrix[0].length > 0) {
    int max = matrix[0][0];
    
    for (int[] list : matrix) {
        for (int number : list) {
            if (number > max) {
                max = number;
            }
        }
    }
    
    System.out.println("Maximum: " + max);
}
```

We're setting up our initial minimum and maximum value as the first element in the array, because we need to guarantee that our answer will be a value in the array.

A more naive solution might've used an arbitrarily small or large value as the starting minimum or maximum. However, it's possible that _all_ the array values are smaller or larger than this starting value, which would make your algorithm incorrect.

### Searches

We're going to dive much more deeply into searching \(and sorting\) in the next unit, but let's take a look at a simple example.

We have a large list of unknown numbers \(pretend they're unknown\). We want to know the index at which a certain target value exists \(if it exists at all\).

```java
int target = 7;
int[][] matrix = {
    { 2, 4, 6, 8 },
    { 1, 3, 7, 9 }
};
boolean found = false;

for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        if (matrix[i][j] == target) {
            found = true;
            System.out.println(target + " found at (" + i + ", " + j + ")");
            
            break;
        } 
    }
}

if (!found) {
    System.out.println(target + " wasn't found in the 2D array.");
}
```

If `target` is found, we print the row and column indexes at which it was found. If, after going through the entire `for` loop, `found` is still `false`, then we can assume the 2D array did not contain `target`.

