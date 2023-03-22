---
layout: post
title: "🔢 Fundamentals Of Digital Discipleship, Part IX: Sets"
date: 2023-03-09 03:42:42 -0500
categories: digital computer programming python ministry
published: true
---

<span style="font-weight:italic;font-size:2em;color:Black;">Sets & Frozensets</span>

A [set](https://docs.python.org/3/library/stdtypes.html#set-types-set-frozenset) object is a mutable, unordered collection of distinct hashable objects **with no duplicate entries**. Sets do not record element position or order of insertion and since they're an unordered collection, sets do not support indexing, slicing, or other sequence-like behavior. There're only two built-in set types, set and frozenset, the latter of which is immutable.

|||
|:-:|:-:|
|**Mutable**|list, set, dict, bytearray|
|Immutable|int, float, complex, str, bool, bytes, tuple, range, frozenset|
|Ordered|list, tuple, str, dict|
|**Unordered**|set, frozenset|
|**Hashable**|str, int, float, complex, bool, bytes, ranges, frozensets, functions, classes, both [built-in](https://docs.python.org/3/library/functions.html) and user-defined|
|Unhashable|list, dict, set, bytearray|

Intersection, union, difference, and symmetric difference, are the main reasons why I would use a set over other container types like a list for instance. If you haven't gone through our [lists & tuples](http://bit.ly/3JOvG8L) lesson, you may want to complete that understanding first.

<!-- Non-empty sets (not frozensets) can be created by placing a comma-separated list of elements within braces, for example: {'jack', 'sjoerd'}, in addition to the set constructor. -->


<span style="font-weight:italic;font-size:1.6em;">Creating Sets</span>

We can create a set, simply, with either the built-in function `set()`, or with curly braces `{}` much like when we create a dictionary. Since dictionaries can be thought of as a set of key-value pairs, we must be careful to remember that when creating an empty set you have to use `set()`, not `{}`; the latter creates an empty dictionary. I will demonstrate:

```py
# an empty dictionary
empty_dict    = {}
equivalent_to = dict()

# an empty set
empty_set = set()

# set filled with numbers
set_of_ints = {1, 2, 3}
set_of_ints = set([1, 2, 3])

# dictionary of key-value pairs
d = {"one": 1, "two": 2}

# sets have no duplicate entries
# results in {1, 2, 3}
set_of_ints = {1, 1, 2, 2, 3, 3}
```

<span style="font-weight:italic;font-size:1.6em;">Testing For Membership</span>

In very much the same way that we can test for membership in other container types such as lists, tuples, and dictionaries, we can test for membership using the following membership operators.

|Membership||
|:-:|:-:|
|`x in s`|Test x for membership in s.|
|`x not in s`|Test x for non-membership in s.|

```py
# set of literary genres
set_of_genres = {"fantasy", "science fiction", "mystery"}

# result is False
"romance" in set_of_genres

# result is False
"fantasy" not in set_of_genres

# result is True
"fantasy" in set_of_genres
```

<span style="font-weight:italic;font-size:1.6em;">Nothing In Common</span>

|Disjoint||
|:-:|:-:|
|`isdisjoint(other)`|Return True if the set has no elements in common with other. Sets are disjoint if and only if their intersection is the empty set.|

```py
s     = {1, 2, 3}
other = {4, 5, 6}
empty = set()

# results in True
s.isdisjoint(other)

# results in True
s.isdisjoint(empty)
```

<span style="font-weight:italic;font-size:1.6em;">Subset</span>

We can also test to see if our set appears in its entirety within another set. When we say `s < other` it is important to note that this is equivalent to `s <= other and s != other` which is to say that it is a 'proper' subset.

|Subset||
|:-:|:-:|
|`issubset(other)`<br>`set <= other`|Test whether every element in the set is in other.|
|`set < other`|Test whether the set is a proper subset of other, that is, `set <= other and set != other`.|

```py
s      = {1, 2, 3}
same   = {1, 2, 3}
supers = {0, 1, 2, 3, 4}

# results in True
s.issubset(same)
s <= same

# results in True
s.issubset(supers)
s <= supers
s < supers

# results in False
# s <= same and s != same
s < same
```

<span style="font-weight:italic;font-size:1.6em;">Superset</span>

The superset is the exact opposite to the subset, but otherwise works in the same way inversely. 

|Superset||
|:-:|:-:|
|`issuperset(other)`<br>`set >= other`|Test whether every element in other is in the set.|
|`set > other`|Test whether the set is a proper superset of other, that is, set >= other and set != other.|

```py
s      = {0, 1, 2, 3, 4}
same   = {0, 1, 2, 3, 4}
subset = {1, 2, 3}

# results in True
s.issuperset(same)
s >= same

# results in True
s.issuperset(subset)
s >= subset
s > subset

# results in False
# s >= same and s != same
s > same
```

<span style="font-weight:italic;font-size:1.6em;">Union</span>

The union of two sets should be reminiscent of concatenation in some ways, while they are different in the way that sets are not appending anything, we are essentially combining two sets.

|Union||
|:-:|:-:|
|`union(*others)`<br>`set | other | ...`|Return a new set with elements from the set and all others.|

```py
s1 = {1, 2}
s2 = {3, 4}
s3 = {5, 6}

# results in {1, 2, 3, 4}
s1.union(s2)
s2.union(s1)
s1 | s2
s2 | s1

# results in {1, 2, 3, 4, 5, 6}
s1.union(s2, s3)
s1 | s2 | s3
```

⚠️ **The following operations are available only to the mutable set and not the immutable frozenset.**

|Union||
|:-:|:-:|
|`update(*others)`<br>`set |= other | ...`|Update the set, adding elements from all others.|

```py
s1 = {1, 2}
s2 = {3, 4}

# s1 becomes the union
# s1 is assigned {1, 2, 3, 4}
s1.update(s2)
s1 |= s2
```

<span style="font-weight:italic;font-size:1.6em;">Intersection</span>

The intersection of two sets creates a new set from the elements that intersect, or that they have in common.

|Intersection||
|:-:|:-:|
|`intersection(*others)`<br>`set & other & ...`|Return a new set with elements common to the set and all others.|

```py
s1 = {1, 2, 3, 4}
s2 = {3, 4, 5, 6}

# results in {3, 4}
s1.intersection(s2)
s2.intersection(s1)
s1 & s2
s2 & s1
```

⚠️ **The following operations are available only to the mutable set and not the immutable frozenset.**

|Intersection||
|:-:|:-:|
|set &= other & ...`|Update the set, keeping only elements found in it and all others.|

```py
s1 = {1, 2, 3, 4}
s2 = {3, 4, 5, 6}

# s1 becomes the intersect
# s1 is assigned {3, 4}
s1.intersection_update(s2)
s1 &= s2
```

<span style="font-weight:italic;font-size:1.6em;">Difference</span>

Whereas the intersection creates a new set from the common elements of two sets, the difference gives us a new set where they do not intersect; however, only the elements in the first set that differ from the elements in the second.

|Difference||
|:-:|:-:|
|`difference(*others)`<br>`set - other - ...`|Return a new set with elements in the set that are not in the others.|

```py
s1 = {1, 2, 3, 4}
s2 = {3, 4, 5, 6}

# results in {1, 2}
s1.difference(s2)
s1 - s2

# results in {5, 6}
s2.difference(s1)
s2 - s1
```

⚠️ **The following operations are available only to the mutable set and not the immutable frozenset.**

|Difference||
|:-:|:-:|
|`set -= other | ...`|Update the set, removing elements found in others.|

```py
s1 = {1, 2, 3, 4}
s2 = {3, 4, 5, 6}

# s1 is becomes the difference
# s1 is assigned {1, 2}
s1.difference_update(s2)
s1 -= s2

# s2 becomes the difference
# s2 is assigned {5, 6}
s2.difference_update(s1)
s2 -= s1
```

<span style="font-weight:italic;font-size:1.6em;">Symmetric Difference</span>

Whereas difference creates a new set of elements that appear in the first set and are not in the second, the symmetric difference gives us a new set where both differences are used to build a new set.

|Symmetric||
|:-:|:-:|
|`set ^ other`|Return a new set with elements in either the set or other but not both.|

<!-- |`copy()`|Return a shallow copy of the set.| -->

```py
s1 = {1, 2, 3, 4}
s2 = {3, 4, 5, 6}

# results in {1, 2, 5, 6}
s1.symmetric_difference(s2)
s2.symmetric_difference(s1)
s1 ^ s2
s2 ^ s1
```

⚠️ **The following operations are available only to the mutable set and not the immutable frozenset.**

|Symmetric|Result|
|:-:|:-:|
|`set ^= other`|Update the set, keeping only elements found in either set, but not in both.|

```py
s1 = {1, 2, 3, 4}
s2 = {3, 4, 5, 6}

# s1 becomes the symmetric difference
# s1 is assigned {1, 2, 5, 6}
s1.symmetric_difference_update(s2)
s1 ^= s2
```

<span style="font-weight:italic;font-size:2em;color:Black;">Mutable Sets Only</span>

Like the update methods, the following operations are available only to the mutable set and not the immutable frozenset. Note that copy() is available to both.

<!-- |Operation|Result|
|:-:|:-:|
|`update(*others)`<br>`set |= other | ...`|Update the set, adding elements from all others.|
|`intersection_update(*others)`<br>`set &= other & ...`|Update the set, keeping only elements found in it and all others.|
|`difference_update(*others)`<br>`set -= other | ...`|Update the set, removing elements found in others.|
|`symmetric_difference_update(other)`<br>`set ^= other`|Update the set, keeping only elements found in either set, but not in both.| -->

|Operation|Result|
|:-:|:-:|
|`add(elem)`|Add element elem to the set.|
|`remove(elem)`|Remove element elem from the set. Raises KeyError if elem is not contained in the set.|
|`discard(elem)`|Remove element elem from the set if it is present.|
|`pop()`|Remove and return an arbitrary element from the set. Raises KeyError if the set is empty.|
|`clear()`|Remove all elements from the set.|

```py
# empty set
s = set()

# add items to set using iteration
# {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
for i in range(1, 10+1):
    s.add(i)

# remove an element
# {1, 2, 3, 4, 5, 7, 8, 9, 10}
s.remove(6)

# discard an element if present
# without throwing an exception
s.discard(100)

# remove and return arbitrary element
s.pop()

# remove all elements from set
s.clear()

# destroy set object
del s
```

<!-- |Operation|Result|
|:-:|:-:|
|`len(s)`|length of s|
|`min(s)`|smallest item of s|
|`max(s)`|largest item of s| -->

<!-- <span style="font-weight:italic;font-size:2em;color:Black;">Mutable Sequence Operations</span>

|Operation|Result|
|:-:|:-:|
|`s.clear()`|removes all items from s (same as `del s[:]`)|
|`s.copy()`|creates a shallow copy of s (same as `s[:]`)|
|`s *= n`|updates s with its contents repeated n times|
|`s.pop()` or `s.pop(i)`|retrieves the item at i and also removes it from s|
|`s.remove(x)`|remove the first item from s where `s[i]` is equal to x|
|`s.reverse()`|reverses the items of s in place| -->