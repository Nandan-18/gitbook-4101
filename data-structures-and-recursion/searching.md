# Searching

{% hint style="info" %}
* [Searching Algorithms](https://www.geeksforgeeks.org/searching-algorithms/)
{% endhint %}

## Finding a Target

There are two general categories of searching algorithms: sequential and binary. We're going to focus on the former, which is often the slower \(or least performant\) of the two.

{% embed url="https://www.youtube.com/watch?v=aqFTmGbKajI&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

A sequential, or binary, search is a rudimentary means by which we can traverse a list in search of a specific target element. We begin at the beginning of the list, and check each element one-by-one. If our target element is near the beginning of the list, we'll find it rather quickly. However, if it is near the end \(or not in the list at all\), it might take a bit more time.

![](../.gitbook/assets/linear-search.png)

Let's take a look at a pseudocode implementation. Later, we'll reveal a Java implementation.

```text
for i = 1 through the end of the list
    if the element at index i = the target
        return i
    else
        increase i by 1
    end if
end for

if the element was not found
    return -1
end if
```

Pretty straightforward, right? Let's take a look at a more performant solution.

## A Faster Search

A binary search is much faster than a linear search, but there is one caveat: the list must be in sorted order for a binary search to work.

{% embed url="https://www.youtube.com/watch?v=hKI93hOfeIk&list=PLmpmyPywZ443PFI8YF3ZMmoEcRfxXckdH" %}

The algorithm works by repeatedly cutting the list in half. It checks the element in the middle of the list, and proceeds to check the left- or righthand sublist from there. This reduces the number of iterations needed to find an element significantly.

![](../.gitbook/assets/binary-search.png)

Let's take a look at a pseudocode implementation. Later, we'll check out a Java implementation.

```text
start = 0
end = last index in list
middle = 0

while start <= end
    middle = (start + end ) / 2
    
    if element at index middle < target
        shift start up to (middle + 1) to exclude left half of list
    else if element at index middle > target
        shift end back to (middle - 1) to exclude right half of list
    else
        element is located at index middle, so return middle
    end if
end while

return -1 if element was not found in list
```

This is a simple, non-recursive implementation of a binary search. It's assumed the list contains numbers and we're searching for a number, but the same could be done for non-numeric data.

## Performance

When discussing the performance of an algorithm, computer scientists using something called Big-O notation. Big-O is simple a mathematical way in which to describe the limiting behavior of a function. For programmers, it tells us how much _work_ our algorithm needs to do to produce an output. More work \(or more steps\) means less efficient.

Let's take a look at our two search algorithms.

* A linear search algorithm has a complexity of `O(n)`.

This means that for a list of _n_ elements, the worst-case scenario \(where the target element is the last element in the list or not in the list at all\), the algorithm would need to make _n_ comparisons to reach its conclusion.

* A binary search algorithm as a complexity of `O(log n)`.

The binary search algorithm is logarithmic, since we're repeatedly halving the list. The power in such an implementation really shows as we increase the size of the list.

Consider a list that has 1,000 elements in it. A linear search requires up to 1,000 comparisons, whereas a binary search requires roughly 10. Let's double the size of the list to 2,000. Now, a linear search requires up to 2,000 comparisons. It's workload doubled! However, a binary search requires about 11.

Every time you double the size of the input list, a binary search algorithm needs only one additional comparison to do the job.

### How to Choose

How should you choose which algorithm to use? Well, that's easy. If your list is sorted, use a binary search algorithm. It's faster and far more efficient as your dataset increases. If your list isn't sorted, then you'll need to use a linear \(or sequential\) search.

## Java Implementations

We've seen the pseudocode, and discussed the performance implications. Now, let's take a look at how this would be written in Java.

### Linear Search

```java
public int linearSearch(int[] list, int target) {
    for (int i = 0; i < list.length; i++) {
        if (list[i] == target) {
            return i;    // return index at which target was found
        }
    }
    
    return -1;    // return -1 if target was not found
}
```

### Binary Search

```java
public int binarySearch(int[] list, int target) {
    int left = 0;
    int right = list.length - 1;
    
    while (left <= right) {
        int middle = left + (right - left) / 2;
        
        if (list[middle] == target) {          // check if target is at middle
            return middle;
        } else if (list[middle] < target) {    // discard left half of list
            left = middle + 1;
        } else {                               // discard right half of list
            right = middle - 1;
        }
    }
    
    return -1;    // return -1 if target was not found
}
```

