# ArrayLists

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapters 9.1 and 9.2
{% endhint %}

## `List` Interface

We're going to dive into interfaces in a couple sections, so we'll keep the description of an interface short and sweet. We'll spend the bulk of our time on a concrete implementation of the `List` interface.

An interface is a defined set of behaviors that any implementing classes must support. The `List` interface defines these behaviors for classes that store a sequence of elements. That definition looks like this.

* Elements can be inserted or accessed by their position in the list using zero-based indexes.
* A list may contain duplicate elements.
* All lists take on \(by extension, which we'll cover later\) the functionality of a `Collection`.
* In addition to these inherited methods, the `List` interface defines the following methods of its own.

The List interface provides a host of methods that concrete classes must implement.

## `ArrayList`

There are four classes that implement the `List` interface.

* `ArrayList`
* `LinkedList`
* `Vector`
* `Stack`

We're going to focus on the `ArrayList` implementation. An `ArrayList` is a built-in class in the Java programming language that functions much like an array.

{% embed url="https://www.youtube.com/watch?v=oyEnR-AGQx4&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

It resizes itself automatically when more elements are added or inserted, while also maintaining order. The same is true of removals; order is maintained.

### Declaration

We can declare an `ArrayList` like we would any other variable: with a data type and a name. The data type is, of course, `ArrayList`. However, like an array, we also need to specify the data type of the elements that will be stored in our `ArrayList`.

```java
ArrayList<Integer> numbers;
ArrayList<Double> reals;
ArrayList<String> words;
```

We can't store primitive values in an `ArrayList`, so we need to use wrapper classes.

#### Wrapper Classes

There are wrapper classes for each of the primitive data types we might want to store in an `ArrayList`.

* `Character`
* `Boolean`
* `Byte`
* `Short`
* `Integer`
* `Long`
* `Float`
* `Double`

These classes come with some methods that you may or may not find useful. You can check them out in the [JDK Documentation](https://docs.oracle.com/en/java/javase/11/docs/api/index.html). Just search for the class you need.

{% embed url="https://www.youtube.com/watch?v=CxZSyNYOgHw&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

For the purposes of `ArrayList`s, though, we only care that these classes can represent primitive data types in object form.

### Initialization

To initialize an `ArrayList`, we need to use the `new` operator. We're calling a constructor similar to what we've done with `String`s and `Scanner`s, so it looks like a method call \(because it is\).

```java
ArrayList<Integer> numbers;
numbers = new ArrayList<Integer>();

// or in one line

ArrayList<Double> reals = new ArrayList<Double>();

// alternatively, newer versions of the JDK allow for the omission of the
// right-hand type parameter

ArrayList<Integer> numbers = new ArrayList<>();    // Integer is implied
```

The syntax is a little odd because the constructor's parentheses come after the angled brackets indicated the data type.

### Getting

With arrays, we used bracket notation to access values in the array. With `ArrayList`s, we use the built-in `get` method. We pass in an index just like we did with arrays.

```java
ArrayList<Integer> evens = new ArrayList<>();

// assume evens is populated with all even numbers
// in the range [2, 100) in increasing order

int a = evens.get(0);
int b = evens.get(1);
int c = evens.get(2);

// a, b, and c hold 2, 4, and 6, respectively
```

### Adding, Inserting, and Setting

Like `get`, there are built-in methods to add, insert, and set elements. When we add an element to a list, we're appending it to the end. Inserting elements means we're plugging them in somewhere that is not the end of the list. Setting means we're overwriting one element with another.

#### Adding and Inserting

The confusing part, though, is that we use the `add` method to achieve both adding and inserting.

* `add(Object obj)`
* `add(int index, Object obj)`

To append an element, we pass only the element to be added to the `add` method.

```java
ArrayList<String> fruits = new ArrayList<>();

fruits.add("apple");
fruits.add("banana");
fruits.add("cherry");

// fruits now contains: "apple", "banana", "cherry"
```

Suppose we have that same list we just populated. Now, we want to insert `blueberry` between `banana` and `cherry`. We use the `add` method, but we give it an index, too.

```java
fruits.add(2, "blueberry");

// now fruits contains: "apple", "banana", "blueberry", "cherry"
```

Make sure you know what you're trying to do and use `add` appropriately!

#### Setting

There's another way to add an element to a list. This time, though, we'll be overwriting one element with another. To do this, we use the `set` method.

* `set(int index, Object obj)`

Using this method will overwrite the element at `index` with `obj`. Remember our list of fruits? We're going to overwrite `banana` with `apricot`.

```java
// fruits contains: apple, banana, blueberry, cherry

fruits.set(1, "apricot");    // overwrite index 1 with "apricot"

// now fruits contains: "apple", "apricot", "blueberry", "cherry"
```

#### Autoboxing and Unboxing

Java takes care of conversions between primitive data types and their object wrapper equivalents. This is called autoboxing \(converting from a primitive to a wrapper class\) and unboxing \(converting from a wrapper class to a primitive\).

An example will probably do this explanation the most justice.

```java
ArrayList<Integer> numbers = new ArrayList<>();

int x = 7;
numbers.add(x);            // autoboxing! x is converted to an Integer

int y = numbers.get(0);    // unboxing! returned value is converted to an int
```

### Removing

Removing is pretty straightforward, but there are two ways to do it.

* `remove(int index)`
* `remove(Object obj)`

If we know the index of the element we want to remove, then we'll use the remove method that accepts an index as a parameter.

```java
ArrayList<String> words = new ArrayList<>();

words.add("apple");
words.add("bark");
words.add("caterpillar");

// now let's remove the word at index 1 (i.e., "bark")

String removed = words.remove(1);

// removed now equals "bark"
// words now contains "apple", "caterpillar"
```

As you saw, this particular `remove` method returns the element it removed.

We can also search for a specific element and remove that. We pass an object to the `remove` method and, if it exists in the list, the first occurrence will be removed.

```java
ArrayList<String> words = new ArrayList<>();

words.add("apple");
words.add("bark");
words.add("caterpillar");
words.add("dog");

// now let's remove the word "caterpillar"

boolean removed = words.remove("caterpillar");

// removed is true
// words now contains "apple", "bark", "dog" 
```

This time, the `remove` methods returns true if the element was found and removed \(or false if it was not\).

### Iterating

Just like arrays, you'll find the need to traverse the contents of your `ArrayList`s. There are a number of ways you can do this.

{% embed url="https://www.youtube.com/watch?v=r5VavXQd3pc&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

#### Using a Traditional `for` Loop

To use a traditional `for` loop, we need to know how many elements are in the list. Arrays had a `length` property. ArrayLists have a `size` method.

```java
ArrayList<Integer> odds = new ArrayList<>();

// populate list with odd numbers

for (int i = 0; i < odds.size(); i++) {
    int num = odds.get(i);
    
    // do something with num
}
```

#### Using an Enhanced `for` Loop

You can use an enhanced `for` loop in the same way you did with arrays.

```java
ArrayList<Integer> odds = new ArrayList<>();

// populate list with odd numbers

for (int num : odds) {
    // do something with num
}
```

#### Using a `ListIterator`

This one's new and it's specific to `ArrayList`s \(or classes that implement the `List` interface\). Once we get an instance of our `ListIterator`, we can use it to traverse the `ArrayList` in either direction.

```java
ArrayList<String> words = new ArrayList<>();

words.add("always");
words.add("brother");
words.add("color");
words.add("dangerous");

ListIterator iter = words.listIterator();
```

There are `hasNext` and `hasPrevious` methods that let us move forward and backward along the list without going too far.

```java
while (iter.hasNext()) {
    String word = iter.next();
    System.out.println(word);
}

// prints:
//   always
//   brother
//   color
//   dangerous

while (iter.hasPrevious()) {
    String word = iter.previous();
    System.out.println(word);
}

// prints:
//   dangerous
//   color
//   brother
//   always
```

Check out the documentation for all of the `ListIterator` capabilities and methods.

