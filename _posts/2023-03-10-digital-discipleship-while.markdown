---
layout: post
title: "🔁 Fundamentals Of Digital Discipleship, Part XIII: The While Statement"
date: 2023-03-10 01:40:00 -0500
categories: digital computer programming python ministry
published: true
---

<!-- <span style="font-style:Italic;font-size:32px;">Chapter Header</span>

<span style="font-style:Italic;font-size:24px;">Sub Chapter Header</span> -->

<a href="https://docs.python.org/3/reference/compound_stmts.html#the-while-statement" style="font-weight:italic;font-size:2em;">The While Statement</a>

The while statement is used for repeated execution as long as an expression is true. The [break](https://docs.python.org/3/reference/simple_stmts.html#break) and [continue](https://docs.python.org/3/reference/simple_stmts.html#continue) keywords come in handy for granular control over the loop. While can also be used with an [assignment expression](https://docs.python.org/3/reference/expressions.html#assignment-expressions) which is new to Python version 3.8.

<span style="font-size:1.6em;">The Infinite Loop</span>

```py
# Infinite loop
while True:
    print("ctrl+c to stop")

# Infinite Loop w/ counter
count = 0
while True:
    print(f"[{count}] ctrl+c to stop")
    count += 1
```

The [Walrus Operator](https://docs.python.org/3/reference/expressions.html#assignment-expressions) really makes our code much more clean and succinct; however, there seems to be a caveat when desiring to count from zero. An assignment expression assigns an expression to an identifier, while also returning the value of the expression. 

```py
# ⚠️ Doesn't run because `count := count + 1` evaluates to 0
count = -1
while count := count + 1:
    print(f"[{count}] press ctrl+c to stop")

# ⚠️ Starts at 1 instead of 0
count = 0
while count := count + 1:
    print(f"[{count}] press ctrl+c to stop")
```

<!-- If the value returned by that expression happens to be 0 in the condition of a while loop that evaluates to false and therefore prevents the loop beginning at 0.

The work around is to compare the value zero, which is returned by that expression, in order to change the 0 into something that evaluates to True. For instance 0 evaluates to False... and `0 > -1` evaluates to True. -->

If the count starts at -1, without the comparison, it will not run because `count := count + 1` evaluates to 0 or `while 0` which is the same thing as `while False`; however, if we use a comparison `(count := count + 1) > -1` this is essentially `0 > -1` or `while True`.

```py
# Infinite loop w/ walrus operator
count = -1
while (count := count + 1) > -1:
    print(f"[{count}] press ctrl+c to stop")
```

<span style="font-size:1.6em;">Breaking Out Of The Loop</span>

We can break out of the loop using the [break](https://docs.python.org/3/reference/simple_stmts.html#break) keyword.

```py
# Counter
# output: 0 1 2 3 4 5 6 7 8 9 10
count = 0
while True:
    print(f"{count}", end=" ")
    count += 1

    # exit loop at count 10
    if count > 10:
        break

# Countdown
# output: 10 9 8 7 6 5 4 3 2 1 0
count = 10
while True:
    print(f"{count}", end=" ")
    count -= 1

    # exit loop at 0
    if count < 0:
        break
```

The same result can be accomplished utilizing the while's condition instead of the break statement.

```py
# Identical to above except uses
# while condition to break loop
# output: 0 1 2 3 4 5 6 7 8 9 10
count = 0
while count <= 10:
    print(f"{count}", end=" ")
    count += 1

# Countdown using while
# condition to break loop
# output: 10 9 8 7 6 5 4 3 2 1 0
count = 10
while count >= 0:
    print(f"{count}", end=" ")
    count -= 1
```

Here we encounter the same problem as described in the infinite loop section when trying to start with zero. We are forced to start with 1.

```py
# counter w/ walrus operator
# ⚠️ starts at 1 instead of 0
# output: 1 2 3 4 5 6 7 8 9 10
count = 0
while count := count + 1:
    print(f"{count}", end=" ")
    # same as count > 9
    if count == 10:
        break

# countdown w/ walrus operator
# ⚠️ stops at 1 instead of 0
# output: 10 9 8 7 6 5 4 3 2 1 
count = 10+1
while count := count - 1:
    print(f"{count}", end=" ")

    # This loop will stop at 1
    # this break isn't needed
```

The solution is &mdash; once again &mdash; to use a comparison operator.

```py
# simplifying by breaking with condition
# output: 0 1 2 3 4 5 6 7 8 9 10
count = -1
while (count := count + 1) <= 10:
    print(f"{count}", end=" ")

# simplifying by breaking with condition
# output: 10 9 8 7 6 5 4 3 2 1 0
count = 10+1
while (count := count - 1) > -1:
    print(f"{count}", end=" ")
```

<span style="font-size:1.6em;">Skipping An Iteration With Continue</span>

The [continue](https://docs.python.org/3/reference/simple_stmts.html#continue) keyword can be used to skip code or the entire iteration.

```py
# skips printing on 3
# output: 1 2 [skipped] 4 5 6 7 8 9 10
count = 0
while count := count + 1:
    if count == 3:
        print("[skipped]", end=" ")
        continue

    print(f"{count}", end=" ")
    if count == 10:
        break

# simplifying by breaking with condition
# output: 1 2 [skipped] 4 5 6 7 8 9 10
count = 0
while (count := count + 1) <= 10:
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

<!-- ```py
# While loop w/ flag
flag = True
while flag:
    choice = input("y/n: ")
    if choice == "n":
        print("exiting loop")
        flag = False

# While loop w/ break
while True:
    choice = input("y/n: ")
    if choice == "n":
        print("exiting loop")
        break
``` -->

<!-- - flag
- walrus

- lists, tuples, ranges
- sets
- dictionaries


```py

# Infinite loop w/ continue
# skips printing on 3
count = 0
while count := count + 1:
    if count == 3:
        continue

    print(f"[{count}] press ctrl+c to stop")
    if count > 9:
        break

# The first run will countdown from 10 ... to 1
x = 10 + 1
while x := x - 1:
    print(x)

# However if you tried the loop again it would go negative
# to prevent this you can compare the current value to
# see if it is greater than zero, if not the condition
# will be false and it will not countdown negatively
while (x := x - 1) > 0:
    print(x)

# To restart the count, remember to reassign 10+1 to x
x = 10 + 1
while (x := x - 1) > 0:
    if x != 1:
        print(x, end=", ")
    else:
        print(x)

# One-liner if statement
x = 10 + 1
while (x := x - 1) > 0:
    print(x, end=", ") if x != 1 else print(x)

# Alternatively
x = 10 + 1
while (x := x - 1) > 0:
    print(f"{x}, " if x != 1 else f"{x}\n", end="")
``` -->

<!-- <a href="https://docs.python.org/3/reference/compound_stmts.html#the-for-statement" style="font-weight:italic;font-size:21px;">The For Statement</a>

The majority of the time, the for loop statement is more frequently used. Especially if infinite loops are not needed. For loops are very often used with the [range](https://docs.python.org/3/library/stdtypes.html?highlight=range#ranges) built-in.

```py
for i in range(1, 10+1):
    print(i, end=" ")

# this while loop is the same as ...
c = 0
while (c := c + 1) <= 10:
    print(f"{c}, " if c != 10 else f"{c}\n", end="")

# ... this for loop
for i in range(1, 10+1):
    print(f"{i}, " if i != 10 else f"{i}\n", end="")

# counting down can be achieved like so
x = 10 + 1
while (x := x - 1) > 0:
    print(f"{x}, " if x != 1 else f"{x}\n", end="")

# the equivalent using the for loop is as follows
for i in range(10, 0, -1):
    print(f"{i}, " if i != 1 else f"{i}\n", end="")
``` -->


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