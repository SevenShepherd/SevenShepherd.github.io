---
layout: post
title: "🗺️ Fundamentals Of Digital Discipleship, Part X: Dictionaries"
date: 2023-03-09 04:00:00 -0500
categories: digital computer programming python ministry
published: true
---

<!-- <span style="font-style:Italic;font-size:32px;">Chapter Header</span>

<span style="font-style:Italic;font-size:24px;">Sub Chapter Header</span> -->

<span style="font-weight:italic;font-size:2em;">Dictionaries</span>

[Dictionaries](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict), sometimes called *“associative arrays”* in other languages, provide the only standard mapping type available to Python. Mapping objects are mutable and they map hashable values to arbitrary objects. Whereas sequences (lists, tuples, etc.) are indexed by a range of numbers, dictionaries are indexed by keys. Keys can be any immutable type (i.e. strings and numbers). It is best to think of a dictionary as a set of key: value pairs.

|Operations||
|:-:|:-:|
|`list(d)`|Return a list of all the keys used in the dictionary d.|
|`len(d)`|Return the number of items in the dictionary d.|
|`d[key]`|Return the item of d with key key. Raises a KeyError if key is not in the map.|
|`d[key] = value`|Set d[key] to value.|
|`del d[key]`|Remove d[key] from d. Raises a KeyError if key is not in the map.|
|`key in d`|Return True if d has a key key, else False.|
|`key not in d`|Equivalent to not key in d.|
|`iter(d)`|Return an iterator over the keys of the dictionary. This is a shortcut for `iter(d.keys())`.|
|`clear()`|Remove all items from the dictionary.|
|`copy()`|Return a shallow copy of the dictionary.|
|`fromkeys(iterable[, value])`|Create a new dictionary with keys from iterable and values set to value.|
|`get(key[, default])`|Return the value for key if key is in the dictionary, else default. If default is not given, it defaults to None, so that this method never raises a KeyError.|
|`items()`|Return a new view of the dictionary’s items ((key, value) pairs). See the documentation of view objects.|
|`keys()`|Return a new view of the dictionary’s keys. See the documentation of view objects.|
|`pop(key[, default])`|If key is in the dictionary, remove it and return its value, else return default. If default is not given and key is not in the dictionary, a KeyError is raised.|
|`popitem()`|Remove and return a (key, value) pair from the dictionary. Pairs are returned in LIFO order.|
|`reversed(d)`|Return a reverse iterator over the keys of the dictionary. This is a shortcut for reversed(d.keys()).|
|`setdefault(key[, default])`|If key is in the dictionary, return its value. If not, insert key with a value of default and return default. default defaults to None.|
|`update([other])`|Update the dictionary with the key/value pairs from other, overwriting existing keys. Return None.|
|`values()`|Return a new view of the dictionary’s values.|
|`d | other`|Create a new dictionary with the merged keys and values of d and other, which must both be dictionaries. The values of other take priority when d and other share keys. `{**d, **other}`|
|`d |= other`|Update the dictionary d with keys and values from other, which may be either a mapping or an iterable of key/value pairs. The values of other take priority when d and other share keys. `d = {**d, **other}`|

<span style="font-weight:italic;font-size:1.6em;">Creating Dictionaries</span>

We can create a dictionary object with the `dict()` built-in or with braces `{}`.

```py
# constructor
dict(one=1, two=2)

# with or w/o constructor
dict({'one': 1, 'two': 2})
{'one': 1, 'two': 2}

# zip 
dict(zip(['one', 'two'], [1, 2]))
dict([('one', 1), ('two', 2)])

# mixed
dict({'one': 1}, two=2)
```

<span style="font-weight:italic;font-size:1.6em;">Retrieving Values</span>

We can access the value associated with the key in one of a couple ways; the main way is to use square brackets `[]` like we do when we index or subscript a sequence, except in this instance, we would place the key name in the square brackets instead of the index or slice. This will return the value of the dictionary with the specified key. If the key does not exist in the dictionary, the attempt to access a non-existent key will raise a KeyError.

The other technique is to use the dictionary method `get`, which will return the dictionary value for key if the key is in the dictionary, else it will return None if the default is not given, instead of throwing a KeyError.

```py
d = {"key": "value"}
# Either will do, the first returns None
# if the key is not found. The second
# throws a KeyError that can be caught
d.get("key")
d["key"]

# Output
"value"
```

<span style="font-weight:italic;font-size:1.6em;">Assigning New Values To Existent Keys</span>

We can set a new value to an already existent key by using the `=` assignment operator just like we do when we use a simple variable.

```py
# {'secret': None}
d = dict(secret=None)

# Set / assign a new value to
# the key `secret` in the d dict
# results in {'secret': 7}
d['secret'] = 7
```

<span style="font-weight:italic;font-size:1.6em;">Deleting Dictionaries And Keys</span>

If we use `del` to delete the dictionary, the entire object will be destroyed and we will no longer have access to it because it will no longer exist; however, if we use the `clear()` method built into our dictionaries instance we will only clear the object of all key-value pairs, the object will still exist. If we apply `del` to a specific key `d[key]` we will only delete that key-value pair without destroying the object.

```py
cats  = ["🐈", "🙀", "🐾"]
verbs = ["meow", "hiss", "scratch"]

# {'🐈': 'meow', '🙀': 'hiss', '🐾': 'scratch'}
d = dict(zip(cats, verbs))

# deletes "🐾": "scratch"
# the dictionary variable is now
# {'🐈': 'meow', '🙀': 'hiss'} 
del d["🐾"]

# we can also use the clear method
# this doesn't destroy d, only {}
d.clear()

# del the dictionary object
del d
```

<span style="font-weight:italic;font-size:1.6em;">Adding New Key-Value Pairs</span>

We will start with an empty dictionary object and use the assignment operator to add new key-value pairs. Dictionary objects also have access to a method called `update` which "updates" the dictionary with the key/value pairs, overwriting existing keys and returning None.

```py
# Empty dictionary object
d = {}

# {'one': 1}
d["one"] = 1

# {'one': 1, 'two': 2, 'three': 3}
d.update({"two":2, "three":3})

# {'one': 1, 'two': 2, 'three': 3, 'four': 4, 'five': 5}
d.update(dict(four=4, five=5))
```

<span style="font-weight:italic;font-size:1.6em;">Merging Dictionaries</span>

Python also allows us to merge two independent dictionary objects. There was a technique that python programmers used to employ to achieve this, but as of Python 3.9 we have a new and clean option to achieve the same result, I will demonstrate.

```py
d1 = {'one'  : 1, 'two' : 2}
d2 = {'three': 3, 'four': 4}

# the old technique
# {'one': 1, 'two': 2, 'three': 3, 'four': 4}
{**d1, **d2}

# the old technique w/ assignment
# d is now {'one': 1, 'two': 2, 'three': 3, 'four': 4}
d = {**d1, **d2}

# the new technique
# {'one': 1, 'two': 2, 'three': 3, 'four': 4}
d1 | d2

# the new technique w/ assignment
# d is now {'one': 1, 'two': 2, 'three': 3, 'four': 4}
d = d1 | d2

# the new technique w/ compound assignment
# d1 is now {'one': 1, 'two': 2, 'three': 3, 'four': 4}
# d2 is now {'three': 3, 'four': 4}
d1 |= d2
```

<span style="font-weight:italic;font-size:1.6em;">Membership</span>

We can test if a dictionary has a key in it the same way we do when we test for membership in lists.

```py
# create new dictionary object 'd'
# with {'one': 1, 'two': 2} key-value pairs
d = dict(one=1, two=2)

# test to see if 'three' is a member of d
# returns False since d has no key 'three'
'three' in d
```

<span style="font-weight:italic;font-size:1.6em;">Looping & Iteration</span>

Looping and iteration are referring to the same thing. Here are a few ways we can iterate or loop through a dictionary object.

```py
words    = ["one", "two", "three", "four", "five"]
numbers  = list(range(1,5+1))

# {'one': 1, 'two': 2, 'three': 3, 'four': 4, 'five': 5}
combined = dict(zip(words, numbers))

# loop through key-value pairs (one at a time)
for key, value in combined.items():
    print(key, value)

'''
one 1
two 2
three 3
four 4
five 5
'''

# loop through keys (one at a time)
for key in combined.keys():
    print(key)

'''
one
two
three
four
five
'''

# loop through values (one at a time)
for value in combined.values():
    print(value)

'''
1
2
3
4
5
'''
```

An extra example with some fancy formatting. We search for the longest word in the words list using the max built-in tweaked with a lambda expression that instructs it what we are measures as max. The longest word *'three'* is returned, we then measure the length and place it within formatted literal string's (f-string) format specification (format_spec) in order to forces the words field to be left-aligned. All this for the sake of cleanliness.

```py
words    = ["one", "two", "three", "four", "five"]
numbers  = list(range(1,5+1))
combined = dict(zip(words, numbers))
longest  = max(words, key=lambda x: len(x))
length   = len(longest)

for key, value in combined.items():
    print(f"{key:<{length}}: {value}")

'''
one  : 1
two  : 2
three: 3
four : 4
five : 5
'''
```

We can also use the `reversed()` built-in to reverse the loop.

```py
for key, value in reversed(combined.items()):
    print(f"{key:<{length}}: {value}")

'''
five : 5
four : 4
three: 3
two  : 2
one  : 1
'''
```

<span style="font-weight:italic;font-size:1.6em;">Dictionary Comprehensions</span>

Dictionary comprehensions and [list comprehensions](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions) are a very cool feature of Python, enabling us to achieve a lot in a very small and succinct amount of space. <!--We can also use the map builtin to achieve similar results.-->

```py
words    = ["one", "two", "three", "four", "five"]
numbers  = list(range(1,5+1))

# {'one': 1, 'two': 2, 'three': 3, 'four': 4, 'five': 5}
{key:value for key, value in zip(words, numbers)}

# {'one': 100, 'two': 400, 'three': 900, 'four': 1600, 'five': 2500}
{key:(value*10)**2 for key, value in zip(words, numbers)}

# {'one': 1, 'two': 2, 'four': 4, 'five': 5}
{key:value for key, value in zip(words, numbers) if value != 3}
```

<span style="font-weight:italic;font-size:1.6em;">Converting View Objects To Lists</span>

You'll eventually notice that the objects returned by dict.keys(), dict.values() and dict.items() are view objects. This can provide some confusion if you thought you were going to get a list back with all it's common and mutable sequence operations, only to find out that you do not have those abilites. While view objects provide a dynamic view on the dictionary’s entries, it lacks that extra functionality you'd get with a list.

```py
# {'one': 1, 'two': 2, 'three': 3, 'four': 4, 'five': 5}
d = {
    "one"  : 1, 
    "two"  : 2, 
    "three": 3,
    "four" : 4,
    "five" : 5
}

``` items ```

# dict_items([('one', 1), ('two', 2), ('three', 3), ('four', 4), ('five', 5)])
d.items()

# [('one', 1), ('two', 2), ('three', 3), ('four', 4), ('five', 5)]
list(d.items())

``` keys ```

# dict_keys(['one', 'two', 'three', 'four', 'five'])
d.keys()

# list(d) is shorthand for list(d.keys())
# ['one', 'two', 'three', 'four', 'five']
list(d)

``` values ```

# dict_values([1, 2, 3, 4, 5])
d.values()

# values doesn't have a shorthand equivalent
# [1, 2, 3, 4, 5]
list(d.values())
```