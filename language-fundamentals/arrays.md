# Arrays

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 3.10
{% endhint %}

## Declaring Arrays

An array is an order collection of values, which you can visualize as a list. Each value is called an element, and each element is assigned a unique index \(starting at 0\). All elements in an array must have the same data type, and the array must be declared with a set data type, too.

Like any other variable we've encountered thus far, you can declare an array with a type and name.

```java
int[] numbers;      // an array of ints
double[] grades;    // an array of doubles
String[] words;     // an array of Strings
```

Each of these statements declares an array with a specific variable name \(i.e., `numbers`, `grades`, and `words`\) and data type \(i.e., `int`, `double`, and `String`\). The square brackets following the data type indicate that this variable will refer to an array of values of that type.

Occasionally, you may encounter a declaration that places the square brackets after the variable name, rather than the data type. This form is discouraged, but you should understand that it means and does the same thing.

```java
int numbers[];      // this is the same as int[] numbers;
```

In their current states, these arrays do not store any values. They've been declared, but need to be initialized with values like any other variable in Java.

{% embed url="https://www.youtube.com/watch?v=o2ARur9hs9M" %}

## Creating and Initializing Arrays

Typically, we need to create our array before we can initialize it with values. The creation step is different than the declaration step, so don't confuse the two.

When working with arrays, we need to tell the compiler how large of a list we'll need \(i.e., how many elements do we need to store\). This is often referred to as the _length_ of the array.

```java
int[] numbers;            // remember, this declares the array
numbers = new int[10];    // and this creates it with a length of 10
```

This tells the compiler that our `numbers` array needs to store up to 10 values, which instructs the virtual machine to allocate enough memory to accommodate for this.

Naturally, you can condense the declaration and creation statements into one.

```java
int[] numbers = new int[10];
```

Now that we've created our array, it's time to put some data into it. This is called initialization, and to do it we need to understand a little more about the underlying structure of an array. Remember, we can think of it as a list. This list is indexed, though, meaning it is essentially divided into numbered slots \(called _indexes_\).

![](../.gitbook/assets/array-visualization.png)

Use the name of the array along with the desired index to put a value into the array.

```java
numbers[0] = 100;    // initializes the first element
numbers[1] = 200;    // initializes the second element
numbers[2] = 300;    // initializes the third element
```

This is called bracket notation, and among other things, it is used to write data to specific indexes of an array. Later, we'll see how to use it to access data already stored in an array.

You might see programmers combining all three steps--declaring, creating, and initializing--into one.

```java
int[] numbers = {
    100, 200, 300,
    400, 500, 600,
    700, 800, 900
};
```

When using this syntax, the array is pre-initialized with the provided values. The length of the array is determined by the number of values provided.

## Getting and Setting Values

To access an element of an array, we use the same bracket notation we used to initialize.

```java
int[] numbers = {
    100, 200, 300,
    400, 500, 600,
    700, 800, 900
};
```

Using our `numbers` array, we can access any index we'd like.

```java
int x = numbers[2];    // gets the element at index 2 and stores it in x
```

Since we know that arrays are zero-indexed, the element at index 2 is the value `300`. We can print out a few elements to get a better look at how this works.

```java
System.out.println(numbers[0]);
System.out.println(numbers[1]);
System.out.println(numbers[2]);
System.out.println(numbers[3]);
System.out.println(numbers[4]);
```

This prints the values at the first five indexes of `numbers`.

```text
100
200
300
400
500
```

Although we used this notation before when initializing our array, we can also use it to modify \(or, more accurately, overwrite\) existing values in the array.



```java
int[] numbers = {
    100, 200, 300,
    400, 500, 600,
    700, 800, 800
};
```

If you look closely, I accidentally initialized `numbers` with a duplicate value. `800` is at the last two indexes. I meant to put `900` at the last index. This is a simple enough fix.

```java
numbers[8] = 900;
```

Now, the duplicate `800` has been overwritten by `900`. Since arrays are zero-indexed, the last index is always one less than the length of the array. In this example, numbers stores 9 elements \(i.e., its _length_ is 9\). However, the last index is 8.

This is important to remember. Trying to access an invalid index results in an `ArrayIndexOutOfBoundsException`. We'll dive more deeply into exceptions later in the course, but suffice it to say that this will crash your program if not handled correctly.

```java
System.out.println(numbers[10]);    // index 10 does not exist
```

Remember way back in the [Strings](strings.md) section when I promised a short video on memory management? This should hopefully clarify what's going on when we're creating all of these primitive variables, `String`s, and arrays.

{% embed url="https://www.youtube.com/watch?v=LTnp79Ke8FI&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

So, I've thrown a whole lot of information at you. And hopefully you've absorbed most of it. Some of it? I guess we're going to find out!

{% page-ref page="../problem-sets/problem-set-5.md" %}

