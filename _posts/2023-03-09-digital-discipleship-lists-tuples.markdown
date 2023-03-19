---
layout: post
title: "🔢 Fundamentals Of Digital Discipleship, Part IV: Lists & Tuples"
date: 2023-03-09 02:10:00 -0500
categories: digital computer programming python ministry
published: true
---

<!-- <span style="font-style:Italic;font-size:32px;">Chapter Header</span>

<span style="font-style:Italic;font-size:24px;">Sub Chapter Header</span> -->

<span style="font-weight:italic;font-size:2em;color:Black;">Lists</span>

A [list](https://docs.python.org/3/library/stdtypes.html#lists) is an ordered mutable sequence of values enclosed in square brackets, and one of the four collection data types in the Python programming language, including tuples, sets, and dictionaries. Most sequence types share the [common sequence operations](https://docs.python.org/3/library/stdtypes.html#common-sequence-operations).

|Operation|Result|
|:-:|:-:|
|`x in s`|True if an item of s is equal to x, else False|
|`x not in s`|False if an item of s is equal to x, else True|
|`s + t`|the concatenation of s and t|
|`s * n` or `n * s`|equivalent to adding s to itself n times|
|`s[i]`|ith item of s, origin 0|
|`s[i:j]`|slice of s from i to j|
|`s[i:j:k]`|slice of s from i to j with step k|
|`len(s)`|length of s|
|`min(s)`|smallest item of s|
|`max(s)`|largest item of s|
|`s.index(x[, i[, j]])`|index of the first occurrence of x in s (at or after index i and before index j)|
|`s.count(x)`|total number of occurrences of x in s|

<span style="font-size:1.6em;">Testing For Membership</span>

One of the common sequence operations available to lists is the ability to test an item for membership. For instance, if we wanted to see if the "Hacker Cat" 🐱‍💻 emoji is in our list of cat emojis, we could us `in` to test for membership.

```py
cat_emojis = ["🐈", "🐱‍🚀", "🐱‍💻", "🐱‍👤", "🐱‍🐉", "🐱‍👓", "🐱‍🏍", "🐱", "😿", "🙀", "😾", "😹", "😼", "😺", "😽", "😸", "🐈‍⬛", "😻", "🐾"]

"🐱‍💻" in cat_emojis
True

if "🐱‍💻" in cat_emojis:
    print("Hacker Cat is present.")
```

We could also use `not in` to make sure we are not missing an item from a list, or that a list is not missing an item we would expect to see, in very much the same way as the last example.

```py
cat_emojis = ["🐈", "🐱‍🚀", "🐱‍👤", "🐱‍🐉", "🐱‍👓", "🐱‍🏍", "🐱", "😿", "🙀", "😾", "😹", "😼", "😺", "😽", "😸", "🐈‍⬛", "😻", "🐾"]

"🐱‍💻" not in cat_emojis
True

if "🐱‍💻" not in cat_emojis:
    print("Uh oh, hacker cat is missing!")
```

<span style="font-size:1.6em;">Concatenation</span>

Lists can also be concatenated, which is to say, that they can be joined together or combined to make one cohesive list. For instance, we can combine or concatenate our list of domestic cats with our list of big cats, to create one larger list of felines using the `+` arithmetic operator.

```py
domestic = ["🐈", "😸"]
big_cats = ["🦁", "🐯", "🐅", "🐆"]

# ['🐈', '😸', '🦁', '🐯', '🐅', '🐆']
feline   = domestic + big_cats
```

We can also `import random` to `shuffle` our new list in-line so that the items are more evenly distributed. This is not required understanding for this lesson, and was only added as a fun example.

```py
import random

domestic = ["🐈", "😸"]
big_cats = ["🦁", "🐯", "🐅", "🐆"]

# ['🐅', '😸', '🐆', '🦁', '🐯', '🐈']
feline   = domestic + big_cats
random.shuffle(feline)
```

We can also add and <sup>n<sup>th</sup></sup> amount to itself by switching the `+` operator over to the `*` arithmetic operator. Essentially going from addition to multiplication.

```py
string_of_cats = "🐈"
list_of_cats   = ["😹"]

# '🐈🐈🐈🐈🐈'
string_of_cats * 5

# ['😹', '😹', '😹', '😹', '😹']
list_of_cats   * 5
```

<span style="font-size:1.6em;">Indexing & Slicing Lists</span>

Indexing (subscripting) and slicing work the same way as with lists as they do with strings, because they are common sequence operations available to text sequences, as well as binary sequences alike. So this section is equally applicable to str, bytearray, and list. Let's start with indexing:

```py
# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
list_of_ints = list(range(1, 10+1))
# alternately
list_of_ints = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# The zeroth-element or index is the 1st item
list_of_ints[0]
1
```

You can also use negative numbers as indices, which begins counting from the right. So an index of `[-1]` would be the last element in the sequence. It should be noted that because -0 is the same as 0, negative indices must start from -1. 

```py
# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
list_of_ints = list(range(1, 10+1))

list_of_ints[-1]
10
```

Slicing lists with *slice notation* can provide a convenient way to extract a specific range of items in a list. You'll notice, in the example below, that `[5:8+1]` is equivalent to `[5:]` and that is because `8+1` happens to be the last item at the very end of the list, and so encapsulated the same range as `8+1` because `[5:]` starts at an index of 5 which is included and omits the excluded end index. This tells the interpreter to slice from 5 to the end instead of from 5 to 8+1. The outcome is exactly the same in this example.

```py
# ['Hello,', 'nice', 'to', 'meet', 'you.', 'My', 'name', 'is', 'Shepherd.']
# By default the split method uses a " " as the delimiter, so you get a list of words
list_of_strings = "Hello, nice to meet you. My name is Shepherd.".split()
# alternatively
list_of_strings = ['Hello,', 'nice', 'to', 'meet', 'you.', 'My', 'name', 'is', 'Shepherd.']

# Slice notation
# ['My', 'name', 'is', 'Shepherd.']
list_of_strings[5:8+1]

# ['My', 'name', 'is', 'Shepherd.']
list_of_strings[5:]

# Extra credit
' '.join(list_of_strings[0:1] + list_of_strings[5:] + list_of_strings[1:4+1])
```

A potential gotcha of *slice notation* is that the position specified on the left side of the semicolon is included in the slice, while the position on the right hand side of the semicolon is excluded. There's also a way to skip elements while employing slice notation. We can omit the start and ending index.

```py
list_of_ints = [1, 'a', 2, 'b', 3]
list_of_ints[::2]

[1, 2, 3]
```

Perhaps our target range we want to apply a skip upon is nested within other items? Here we have an example following from that which was before, except we have placed our target within hyphen punctuation marks. We can see that this range, once accounting for the offset, begins at an index of 3 (the 4th item), and ends at an index of 7, which because the ending index is excluded we make it 7+1. So what we end up with is a sliced range between 3 and 7+1 with a skip of 2.

```py
list_of_ints = ['-', '-', '-', 1, 'a', 2, 'b', 3, '-', '-', '-']
list_of_ints[3:7+1:2]

[1, 2, 3]
```

<span style="font-size:1.6em;">Measuring Lists</span>

The `len()`, `min()`, `max()` built-ins provide useful functionality for measuring lists. 

```py

# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
list_one = list(range(1, 10+1))

# [1, 2, 3, 4, 5, 6, 7, ... 100]
list_two = list(range(1, 100+1))

# 100
len(list_two)

if len(list_two) == 100:
    print("perfect score")
```

The `min()` and `max()` built-in functions are useful for comparing two different lists and returning the one you need to work on, based on the size of the list.

```py
# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
list_one = list(range(1, 10+1))

# [1, 2, 3, 4, 5, 6, 7, ... 100]
list_two = list(range(1, 100+1))

# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
min(list_one, list_two)

# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100]
max(list_one, list_two)
```

Lists implement all of the [mutable sequence operations](https://docs.python.org/3/library/stdtypes.html#mutable-sequence-types) in addition to the common sequence operations. Lists also provide the additional [`sort()`](https://docs.python.org/3/library/stdtypes.html#list.sort) method.

|Operation|Result|
|:-:|:-:|
|`s[i] = x`|item i of s is replaced by x|
|`s[i:j] = t`|slice of s from i to j is replaced by the contents of the iterable t|
|`del s[i:j]`|same as `s[i:j] = []`|
|`s[i:j:k] = t`|the elements of `s[i:j:k]` are replaced by those of t|
|`del s[i:j:k]`|removes the elements of `s[i:j:k]` from the list|
|`s.append(x)`|appends x to the end of the sequence (same as `s[len(s):len(s)] = [x]`)|
|`s.clear()`|removes all items from s (same as `del s[:]`)|
|`s.copy()`|creates a shallow copy of s (same as `s[:]`)|
|`s.extend(t)` or `s += t`|extends s with the contents of t (for the most part the same as `s[len(s):len(s)] = t`)|
|`s *= n`|updates s with its contents repeated n times|
|`s.insert(i, x)`|inserts x into s at the index given by i (same as `s[i:i] = [x]`)|
|`s.pop()` or `s.pop(i)`|retrieves the item at i and also removes it from s|
|`s.remove(x)`|remove the first item from s where `s[i]` is equal to x|
|`s.reverse()`|reverses the items of s in place|


<span style="font-size:1.6em;">Replacing An Element By Index</span>

This works like assignment, because that is what it essentially is, except you are selecting an individual element by index to be replaced or assigned to.

```py
list_I    = [1, 2, 3]

# Replacement is not assignment
list_I[1] = "replaced"

# [1, 'replaced', 3]
list_I
```

<span style="font-size:1.6em;">Replacing A Range With Slice Notation</span>

We can also use slice notation to replace a range within a list.

```py
slice_this_list        = ['-', '-', '-', 1, 2, 3, '-', '-', '-']
slice_this_list[3:5+1] = [100, 200, 300]

print(slice_this_list)
['-', '-', '-', 100, 200, 300, '-', '-', '-']
```

<span style="font-size:1.6em;">Removing A Range With Slice Notation</span>

Slice notation performed upon a list with the goal of deleting a subset of the list can be performed either by replacing via assignment or by using the `del` keyword. The latter of which makes use of another feature of python so I do advocate using it when the opportunity arises, but it is by no means mandatory.

```py
slice_this_list        = ['-', '-', '-', 1, 2, 3, '-', '-', '-']

# deleting the slice by replacing it via assignment
slice_this_list[3:5+1] = []

# alternatively we can also achieve the same by
# deleting the slice with the del keyword
del slice_this_list[3:5+1]

print(slice_this_list)
['-', '-', '-', '-', '-', '-']
```

<span style="font-size:1.6em;">Slice Notation And Skipping</span>

Again, like with previous examples applying slice notation to sequences, we can employ the skip feature to hone in on a very specific subset of elements.

```py
slice_this_list        = ['-', '-', '-', 1, 'a', 2, 'b', 3, '-', '-', '-']

# [1, 'a', 2, 'b', 3]
slice_this_list[3:7+1]

# [1, 2, 3]
slice_this_list[3:7+1:2]
```

<span style="font-size:1.6em;">Deleting w/ Slice Notation And Skipping</span>

As before, slice notation can be used to remove or delete a subset, and this time we will utilize a skip for example. The one difference you might notice is that assigning an empty list to the slice will not delete it when there is a skip involved and so we have to rely on the `del` keyword to get the job done. Another reason to stick with del for muscle memory.

```py
slice_this_list          = ['-', '-', '-', 1, 'a', 2, 'b', 3, '-', '-', '-']

# ['-', '-', '-', 100, 'a', 200, 'b', 300, '-', '-', '-']
slice_this_list[3:7+1:2] = [100, 200, 300]

del slice_this_list[3:7+1:2]

print(slice_this_list)
['-', '-', '-', 'a', 'b', '-', '-', '-']
```

<span style="font-size:1.6em;">Appending & Reversing</span>

```py
# creates an empty list
plant_growth = []

# append 1 item to the end of the list
plant_growth.append("seed")

# extending more then 1 item
plant_growth.extend(["sprout", "seedling", "vegetative", "budding", "flowering", "ripening"])

# reverse ordered list (in-line)
# alternatively reversed(plant_growth) (not in-line)
# ['ripening', 'flowering', 'budding', 'vegetative', 'seedling', 'sprout', 'seed']
plant_growth.reverse()
```

<span style="font-size:1.6em;">Removal And Deletion</span>

If we want to remove or delete a specific element without using an integer or slice as an index, we will have to use the remove method. From the fruit of a ripened tree comes the seed from which all other trees will ripen and produce seeds which bare their own trees and their own fruit ad infinitum. In a never ending display of recursion and mathematical harmony.

```py
# ['flowering', 'budding', 'vegetative', 'seedling', 'sprout', 'seed']
plant_growth.remove('ripening')

# delete every item up to, but not including the last item in the list
# this is the same as plant_growth[:len(plant_growth)-1]
# this is also the same as plant_growth[:4+1] or [0:4+1]
del plant_growth[:-1]
print(plant_growth)
['seed']
```

We can also clear the entire list with the `clear()` method. After calling the method, the list will return empty `[]`.

```py
ten_thousand = list(range(1,10000+1))
ten_thousand.clear()
```

<span style="font-size:1.6em;">Copying vs Shallow Copying</span>

We can copy a list, but this could have unintended side effects such as referencing the list copied instead of actually copying it the way we intended as a shallow copy. We can avoid this issue with the [`copy()`](https://docs.python.org/3/library/copy.html?highlight=shallow%20copy#module-copy) method which enables us to make a shallow copy.

```py
x = []
y = x

# x is [7], y is [7]
y.append(7)

'''alternatively'''

x = []
y = x.copy()

# x is [], y is [7]
y.append(7)
```

<!-- desirably avoidable -->

Another unintended side effect would be the inner elements of a nested list having the same reference. Modifying any of the elements modifies all lists because they all refer to the original which is being modified. In order to create a list of different individual lists we will need to use a list comprehension.

```py
# All three elements of [[]] * 3 are references to this single empty list. 
lists = [[]] * 3
lists
[[], [], []]

# Modifying any of the elements of lists modifies this single list.
lists[0].append(7)
lists
[[7], [7], [7]]

# To create a list of different lists you'll need to use a list comprehension.
lists = [[] for i in range(3)]
lists[0].append(7)
lists
[[7], [], []]

# reverse reverses in place
lists.reverse()
lists
[[], [], [7]]
```

<span style="font-size:1.6em;">Inserting & Popping</span>

I personally would resort to using slice notation, indexing, and del; however, you should know how to use these methods as well.

```py
x = [3, 2, 1]

x.pop()       
1
x       
[3, 2]

x.clear()
x
[]

x += [1,2,3]
x.extend([4,5,6])
x += [7,8,9]
x.append(10)
x
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

x.remove(1)
del x[2:7+1:2]
x
[2, 3, 5, 7, 9, 10]
```

<span style="font-size:1.6em;">Sorting</span>

Sorting can be achieved in a number of different ways. The list data type provides us with it's own sort method which sorts the items within the list in-place so no assignment need take place.

```py
y = [4,1,3,9,7,8,3,7]
y.sort()
y
[1, 3, 3, 4, 7, 7, 8, 9]

# alternatively
# [9, 8, 7, 7, 4, 3, 3, 1]
sorted(y, reverse=True)
```

<script>
    var refTagger = {
        settings: {
            bibleVersion: 'ESV'
        }
    }; 

    (function(d, t) {
        var n=d.querySelector('[nonce]');
        refTagger.settings.nonce = n && (n.nonce||n.getAttribute('nonce'));
        var g = d.createElement(t), s = d.getElementsByTagName(t)[0];
        g.src = 'https://api.reftagger.com/v2/RefTagger.js';
        g.nonce = refTagger.settings.nonce;
        s.parentNode.insertBefore(g, s);
    }(document, 'script'));
</script>