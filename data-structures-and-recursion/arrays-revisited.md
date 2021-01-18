# Arrays, Revisited

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 3.10
{% endhint %}

## Refresher

We touched on arrays early on in the course, but we didn't go into much depth. That's about to change. Check out this refresher before we dive in. Oh, and there's a little on two dimensional arrays, so I'll replicate this video in the [2D Arrays](2d-arrays.md) section.

{% embed url="https://www.youtube.com/watch?v=oN\_KEbq3U14&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## Traversing an Array

We've touched on arrays lightly already. We're about to go a whole lot more in depth. If you need a quick refresher, go ahead and review the [Arrays](../language-fundamentals/arrays.md) section.

{% embed url="https://www.youtube.com/watch?v=bhKrf9gzxic&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

You'll be surprised how often you need to traverse the elements of an array. Traversal is just a fancy term for iterating over an array, and iterate is just a fancy term for looping through an array. There are a couple different ways to do this, once of which should be very familiar.

### Traditional `for` Loop

Since arrays have numeric indexes, we can use the loop counter of a `for` loop to access its elements one-by-one. And remember the _length_ of an array. Well, there's a formal `length` property we can use to make sure we don't exceed the bounds of the array.

```java
int[] numbers = {
    100, 200, 300,
    400, 500, 600,
    700, 800, 900
};
```

Let's traverse the array and print a little message for each element.

```java
for (int i = 0; i < numbers.length; i++) {
    System.out.println("Index " + i + " is " + numbers[i]);
}
```

This will print a message for each index in `numbers`.

```text
Index 0 is 100
Index 1 is 200
Index 2 is 300
Index 3 is 400
Index 4 is 500
Index 5 is 600
Index 6 is 700
Index 7 is 800
Index 8 is 900
```

### Enhanced `for` Loop

There is another type of loop that is particularly useful when working with arrays \(or lists of data in general\). It's called an enhanced `for` loop. It works very much like a traditional `for` loop, but streamlines the syntax needed.

```java
for (int value : numbers) {
    // do something with each of the values
}
```

`value` is a placeholder for each element in `numbers`. The enhanced `for` loop automatically advances to the next element in the array, so it's a convenient way to iterate over an array from start to finish.

A traditional `for` loop might be a better choice if you need more fine grained control over how the loop advances over the elements. You might want to work with every other element.

```java
for (int i = 0; i < numbers.length; i = i + 2) {
    // do something with every other element
}
```

Or, you might want to iterate backwards.

```java
for (int i = numbers.length - 1; i >= 0; i--) {
    // work backwards across the array
}
```

Both of these scenarios work well with a traditional `for` loop. An enhanced `for` loop starts at the first element and iterates one-by-one to the end of the array, so it wouldn't be a suitable choice to do something customized like this.

## Common Algorithms

There are a number of common algorithms that make use of array, and we're going to walk through a few of them together.

### Summations

A common task with arrays of numeric data is finding the sum of all of the elements. Using some basic math and a loop, this is can be done in a fairly routine manner.

```java
int[] numbers = { 2, 4, 6, 8, 1, 3, 5, 7, 9 };

int sum = 0;
for (int number : numbers) {
    sum = sum + number;
}

System.out.println("Sum: " + sum);
```

This, of course, could have been done using a traditional `for` loop \(or even a `while` loop\), too.

### Averages

Averaging a set of numbers only takes an extra step or two beyond summing them.

```java
int[] numbers = { 2, 4, 6, 8, 1, 3, 5, 7, 9 };

int sum = 0;
for (int number : numbers) {
    sum = sum + number;
}

if (numbers.length > 0) {
    double average = (double) sum / numbers.length;
    
    System.out.println("Average: " + average);
}
```

The first six lines are just the summation steps. Next comes the averaging. We check that the length of the array isn't zero \(otherwise we'd get a division by zero error\). And we also cast one of the operands to a `double`. We're working with `ints`, but we want our average to support decimal points.

### Minimums and Maximums

It's an age-old question. We have a large list of numbers. What's the smallest number? What's the largest? Let's find out.

```java
int[] numbers = { 2, 4, 6, 8, 1, 3, 5, 7, 9 };

if (numbers.length > 0) {
    int min = numbers[0];
    
    for (int number : numbers) {
        if (number < min) {
            min = number;
        }
    }
    
    System.out.println("Minimum: " + min);
}
```

Sometimes, you might be asked to find the _index_ at which the minimum \(or maximum\) value exists. In that case, you'd need to use a traditional `for` loop so you have access to array indexes as you go.

Rewriting this to support finding the maximum value requires only a couple code changes.

```java
int[] numbers = { 2, 4, 6, 8, 1, 3, 5, 7, 9 };

if (numbers.length > 0) {
    int max = numbers[0];
    
    for (int number : numbers) {
        if (number > max) {
            max = number;
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
int[] numbers = { 2, 4, 6, 8, 1, 3, 5, 7, 9 };
boolean found = false;

for (int i = 0; i < numbers.length; i++) {
    if (numbers[i] == target) {
        found = true;
        System.out.println(target + " found at index " + i);
        
        break;
    }
}

if (!found) {
    System.out.println(target + " wasn't found in the array.");
}
```

If `target` is found, we print the index at which it was found. If, after going through the entire `for` loop, `found` is still `false`, then we can assume the array did not contain `target`.

### Reversals

Another common algorithm is reversing the order of the elements of an array. We've seen a lot of code examples, so let's break up the monotony with a quick video.

{% embed url="https://www.youtube.com/watch?v=77N5qsea8qQ&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

## Adding Elements

When adding elements to an array, we'll use the familiar bracket notation. However, we need to take a couple things into account. This essentially boils down to one question: does order matter? Let's take a look at scenarios on both sides of this question.

Additionally, the number of elements in the array is something we'll want to track. To do that, we can create our own variable that tells us how many _real_ elements are in the array versus how many available indexes there are.

### Appending

If we don't care about the order of our elements, then adding to our array is trivial. We're going to append some element to the end of the list. All we really need to do is very that we have space in the array to do this.

```java
int[] numbers = new int[10];     // capacity is 10
int currentSize = 0;             // current zero elements in array

for (int i = 0; i < 5; i++) {
    numbers[i] = (i + 1) * 2;    // add element to array
    currentSize++;               // update current size
}

// later we want to add another element, but need to check if there's space

int newElement = 1234567;
if (currentSize < numbers.length) {
    numbers[currentSize] = newElement;
    currentSize++;
}
```

Since our arrays are zero-indexed, currentSize is always one greater than the index of the last appended value. To put it another way, `currentSize` is always equal to the next available index.

### Inserting

If we want to maintain the order of our array, we'll need some fancy footwork to move things around as needed. Suppose we have the following partially filled array.

```java
int[] numbers = new int[10];     // capacity is 10
int currentSize = 0;             // current zero elements in array

// add some elements

for (int i = 0; i < 5; i++) {
    numbers[i] = (i + 1) * 2;    // add element to array
    currentSize++;               // update current size
}
```

Our array now holds `[ 2, 4, 6, 8, 10, 0, 0, 0, 0, 0 ]`. All of those zeroes are the default values in the array before we give those indexes a _real_ value. Now, we're going to insert `7` between the `6` and `8`, all while maintaining the order of the existing elements.

To do this, we need to shift things to the right, starting with the `10`. It'll move one slot to the right \(overwriting one of the default values\). Next, we'll move the `8` to the right \(overwriting the previous position of the `10`\). This opens up a slot to insert the `7`.

```java
int position = 3;
int newValue = 7;

if (currentSize < numbers.length) {
    for (int i = currentSize; i > position; i--) {
        numbers[i] = numbers[i - 1];    // this shifts each number in the array
                                        // to the right, starting at the end of
                                        // the array and going up to the position
                                        // where we'll be inserting the new value
    }
    
    numbers[position] = newValue;       // insert after all shifting is done
    currentSize++;                      // update current size
}
```

The new contents of the array are `[ 2, 4, 6, 7, 8, 10, 0, 0, 0, 0 ]`.

## Removing Elements

To remove elements from an array, we're going to be using the same bracket notation we always have. We'll need to take a couple things in consideration, though. Again, the question at hand is whether or not order matters.

### Without Maintaining Order

If we don't care about maintaining the order of the array, then removing an element is pretty simple.

```java
int[] numbers = new int[10];
int currentSize = 0;

// add some elements

for (int i = 0; i < 5; i++) {
    numbers[i] = i + 1;
    currentSize++;
}
```

Our array now holds `[ 1, 2, 3, 4, 5, 0, 0, 0, 0, 0 ]`, where the trailing zeroes are empty \(i.e., default values\). Suppose we wanted to remove the `3`. Without regard for element order, we can overwrite the element with wish to remove with the last _real_ element. By _real_, I mean something that isn't a default value.

```java
int position = 2;                                // position of element to remove
numbers[position] = numbers[currentSize - 1];    // overwrite with last element

numbers[currentSize - 1] = 0;    // overwrite previous last element
currentSize--;                   // update current size
```

The new contents of the array are now `[ 1, 2, 5, 4, 0, 0, 0, 0, 0, 0 ]`.

### Maintaining Order

If we need to concern ourselves with order, then it becomes a bit trickier. Suppose we have the following partially filled array.

```java
int[] numbers = new int[10];
int currentSize = 0;

// add some elements

for (int i = 0; i < 5; i++) {
    numbers[i] = i + 1;
    currentSize++;
}
```

Our array now holds `[ 1, 2, 3, 4, 5, 0, 0, 0, 0, 0 ]`, where the trailing zeroes are empty \(i.e., default values\). Suppose we wanted to remove the `3`. If we maintain order, the array should hold `[ 1, 2, 4, 5, 0, 0, 0, 0, 0, 0 ]` when we're finished.

To do this, we need to slide some things around. We're going to shift the `4` and `5` to the left, overwriting the to-be-removed `3` in the process. Then, we'll overwrite the now-duplicated `5` with a default value.

```java
int position = 3;    // index of value we want to remove

for (int i = position; i < currentSize; i++) {
    numbers[i - 1] = numbers[i];    // shift everything to the left to
                                    // effectively overwrite the element
                                    // we want to remove
}

// at this point, the array holds [ 1, 2, 4, 5, 5, 0, 0, 0, 0, 0 ]
// we need to remove the extra 5 and update the current size

numbers[currentSize - 1] = 0;
currentSize--; 
```

The new contents of the array are now `[ 1, 2, 4, 5, 0, 0, 0, 0, 0, 0 ]`.

## Swapping Elements

At times, you'll find yourself needing to swap two elements in place in an array. Let's take a look at how we might do that. Here's a naive \(and incorrect\) solution.

```java
char[] letters = { 'A', 'B', 'D', 'C', 'F' };

// swap D and C so the array holds: [ A, B, C, D, F ]

letters[2] = letters[3];
letters[3] = letters[2];
```

Seems like a simple enough solution, right? This actually won't work. After line 5, the contents of the array will look like this: `[ A, B, C, C, F ]`. See how `D` is gone? There's no getting it back.

To correctly swap these values, we need to temporarily store a copy of one of the values so we don't lose it during the swap.

```java
char[] letters = { 'A', 'B', 'D', 'C', 'F' };

// swap D and C so the array holds: [ A, B, C, D, F ]

char temp = letters[2];     // save a copy
letters[2] = letters[3];    // overwrite copy
letters[3] = temp;          // re-insert copy
```

Now our array stores each letter as expected.

## Copy, Grow, and Trim

There are times where we might need to manipulate our original array as a whole \(rather than only manipulating the underlying elements\). Making copies, increasing the capacity of our array, or decreasing the capacity of our array are all common tasks that can be achieved with the same built-in method.

### Copying an Array

We can use the `copyOf` method, which is a static method defined in the `Arrays` class. This method takes two parameters: the array to be copied, and the length of the resulting array. It returns a new array without modifying the original.

```java
String[] names = { "Jason", "Patrick", "Stacy", "Amanda" };

String copy = Arrays.copyOf(names, names.length);
```

Because we used the length of the original array, this creates a carbon copy with the same length and contents as the original.

You can also use a similar method called `copyOfRange`, which returns a new array built from the copied values of a specified range of the original array.

### Growing an Array

Using the same copyOf method, we can _grow_ our arrays \(i.e., increase their capacity\). Essentially, we'll be copying our existing array into a larger array.

```java
String[] names = { "Jason", "Patrick", "Stacy", "Amanda" };

String biggerCopy = Arrays.copyOf(names, names.length * 2);
```

Because we've used a length twice that of the original, the `biggerCopy` array will have twice the capacity. The unused indexes are filled in with default values. For arrays of strings \(or any other objects\), the default value is `null`.

### Trimming an Array

Likewise, we can trim an array down to size using a combination of the `copyOf` method and our internally-tracked `currentSize`. Suppose we created an array with a larger-than-needed capacity.

```java
int[] numbers = new int[25];
```

Originally, I thought I'd need all 25 indexes. As it turned out, I needed far fewer.

```java
int currentSize = 0;

for (int i = 0; i < 5; i++) {
    numbers[i] = (i + 1) * (i + 1);
    currentSize++;
}

// numbers: [ 1, 4, 9, 16, 25, 0, 0, 0, 0, 0 ]
```

Once I'm sure I don't need anymore indexes in the array, I can trim it down to size to conserve memory \(or, more likely, to eliminate the possibility of another part of my code mistaking a default value for a _real_ one.

```java
numbers = numbers.copyOf(numbers, currentSize);

// numbers: [ 1, 4, 9, 16, 25 ]
```

Now, the total capacity of `numbers` matches `currentSize`, which is how many actual values I put in the array in the first place.

