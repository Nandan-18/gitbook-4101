# Strings, Revisited

{% hint style="info" %}
* _Core Java: Volume I—Fundamentals_
  * Chapter 3.6
* [String Documentation](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html)
{% endhint %}

## Java Standard Library

The Java standard library is a set of classes that are built into the language. Java programs can load these classes at runtime, and use them during execution.

## String

The `String` class is built into the Java programming language, and you can use `String`s and their methods out-of-the-box. You've already learned and read all about `String`s, but didn't dive too deeply into the API.  There are over 50 different methods \(many more if you consider that most methods accept numerous sets of input types\), but these are likely the most useful to you in this course.

### Methods

* `charAt(int index)`

The `charAt` method returns the character at the specified index.

```java
String word = "hello";          // remember, Strings are 0-indexed
char letter = str.charAt(1);    // letter is 'e'
```

* `compareTo(String anotherString)`

The `compareTo` method compares two `String`s lexicographically. The method returns a negative value for lesser `String`s \(i.e., those that would appear closer to the beginning of a lexicographical ordering\), a positive value for greater `String`s, and 0 for equivalent `String`s.

```java
String first = "apple";
String second = "banana";

int a = first.compareTo(second);    // negative, usually -1
int b = second.compareTo(first);    // positive, usually 1
int c = first.compareTo(first);     // 0
```

There is a similar method called `compareToIgnoreCase`, which does the same thing while ignoring differences in capitalization.

* `concat(String str)`

The `concat` method concatenates two `String`s together, returning a new `String` entirely.

```java
String one = "fire";
String two = "truck";
String three = one.concat(two);    // firetruck
```

* `contains(CharSequence s)`

The `contains` method returns `true` if the `String` contains the specified sequence. Don't pay too much attention to `CharSequence`. This method works with `String`s, and that's probably all you'll need to know.

```java
String word = "alphabetical";
boolean doesContain = word.contains("bet");    // true
```

* `endsWith(String suffix)`

The `endsWith` method returns `true` if the `String` ends with the specified suffix.

```java
String word = "happily";
String suffix = "ly";
boolean ends = word.endsWith(suffix);    // true
```

* `equals(Object anObject)`

The `equals` method returns `true` if both objects are `String`s, and their contents are equivalent.

```java
String a = "abc";
String b = "xyz";
boolean isEqual = a.equals(b);    // false
```

There is a similar method called `equalsIgnoreCase`, which does the same thing while ignoring differences in capitalization.

* `indexOf(String str)`

The `indexOf` method returns the index within a `String` of the first occurrence of the specified substring.

```java
String sentence = "This sentence has five words.";
int index = sentence.indexOf("s");                    // 3 (it finds the
                                                      // first "s" in the
                                                      // sentence)
```

There are several other variations of the `indexOf` method. Check out [the API ](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/lang/String.html)for more on these.

* `isEmpty()`

The `isEmpty` method returns `true` if the `String` has a length of 0.

```java
String str = "";
boolean empty = str.isEmpty();    // true
```

There is a similar method called `isBlank`, which returns `true` if the `String` is made up entirely of whitespace.

* `lastIndexOf(String str)`

The `lastIndexOf` method behaves in much the same way as the `indexOf` method, expect it finds the last occurrence rather than the first occurrence.

```java
String sentence = "This sentence has five words.";
int index = sentence.lastIndexOf("s");                // 27 (it finds the
                                                      // last "s" in the
                                                      // sentence)
```

Again, like `indexOf`, there are other variations of the `lastIndexOf` method. Check out [the API ](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/lang/String.html) for more on these.

* `length()`

Returns the number of characters in the `String`.

```java
String str = "abcd";
int length = str.length();    // 4
```

* `replace(CharSequence target, CharSequence replacement)`

The `replace` method replaces each occurrence of the target substring with the replacement substring.

```java
String first = "ababa";
String second = first.replace("a", "x");    // "xbxbx"
```

There are other variations of `replace`, as well as a similar method called `replaceAll`. Check out [the API ](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/lang/String.html)for more on these.

* `startsWith(String prefix)`

The `startsWith` method returns `true` if the `String` begins with the specified prefix.

```java
String word = "antithesis";
boolean starts = word.startsWith("anti");    // true
```

* `strip()`

The `strip` method trims the leading and trailing whitespace from a `String`.

```java
String raw = "  some text  ";
String clean = raw.strip();      // "some text"
```

There are similar methods called `stripLeading` and `stripTrailing`, which trim only the leading or trailing whitespace, respectively. There's also an outdated method called `trim`. `strip` is the Unicode-aware upgraded version, which uses a newer definition of whitespace.

* `substring(int beginIndex, int endIndex)`

The `substring` method returns a substring composed of characters between specified starting and ending indices. The starting index is inclusive, but the ending index is not.

```java
String original = "The String class is built into Java.";
String substring = original.substring(11, 16);               // "class"
```

There is another version of `substring` that uses only a starting index. The implied ending index is the end of the `String`.

* `toLowerCase()`

The `toLowerCase` method converts a `String` to lowercase characters. Characters that cannot be converted \(i.e., numbers\) are left unchanged.

```java
String str = "ABC123XYZ";
String lower = str.toLowerCase();    // "abc123xyz"
```

* `toUpperCase()`

The `toUpperCase` method converts a `String` to uppercase characters. Characters that cannot be converted \(i.e., numbers\) are left unchanged.

```java
String str = "abc123xyz";
String upper = str.toUpperCase();    // "ABC123XYZ"
```

* `valueOf(int i)`

The `valueOf` method returns a `String` representation of its input.

```java
int x = 123;
String str = String.valueOf(x);    // "123" (a String)
```

Pay attention to how `valueOf` is used. It's a little different than how most of the other `String` methods are used. There are variations of this method for many data types.

You should take a look at the [full documentation](https://docs.oracle.com/en/java/javase/12/docs/api/java.base/java/lang/String.html) for more details on these and all of the available methods in the `String` class.

