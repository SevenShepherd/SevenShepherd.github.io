---
layout: post
title: "❓ Fundamentals Of Digital Discipleship, Part XI: The If Statement"
date: 2023-03-09 04:37:00 -0500
categories: digital computer programming python ministry
published: true
---

<a href="https://docs.python.org/3/reference/compound_stmts.html#the-if-statement" style="font-weight:italic;font-size:2em;">The If Statement</a>

<!-- https://docs.python.org/3/tutorial/controlflow.html#if-statements -->

<!-- [Compound statements](https://docs.python.org/3/reference/compound_stmts.html) contain groups of other statements and consist of one or more ‘clauses’ which span multiple lines. The clauses control and manipulate the other statements. -->

The if statement is a [compound statement](https://docs.python.org/3/reference/compound_stmts.html) and control flow tool that is used for conditional execution. 

<!-- ```py
if condition_or_assignment_expression:
    print("condition was true")
``` -->

```py
if_stmt ::= "if" assignment_expression ":" suite
            ("elif" assignment_expression ":" suite)*
            ["else" ":" suite]
```

<span style="font-size:1.6em;">Comparison Operators</span>

|Relational or Comparison|Operators|
|:-:|:-:|
|Equality (Equal)|`a == b`|
|Inequality (Not Equal)|`a != b`|
|Greater than|`a > b`|
|Greater than or equal to|`a >= b`|
|Less than|`a < b`|
|Less than or equal to|`a <= b`|

<span style="font-size:1.3em;">Equality</span>

When people first attempt to pick up a programming language they usually notice a difference between testing for equality in mathematics and testing for equality in most programming languages. The equality operator in math is `=` while in Python and most programming languages it is `==`.

```py
x, y = 1000, 10

# testing two numbers for equality inside the condition of an if statement. The code block in the if statement is never reached because 1000 is not equal to 10.
if x == y:
    print(f"{x} is equal to {y}")

# in this second example, the code block is executed because 1000 is equal to 1000.
if x == 1000:
    print(f"{x} is equal to 1000")

'''
1000 is equal to 1000
'''
```

<span style="font-size:1.3em;">Inequality</span>

There is one way we can get dissimilar values to execute. One such method is to use the `!=` or "not equal" operator. unlike `x == y` above, `x != y` will execute the if statement's code block because x is not equal to y, or 1000 is not equal to 10.

```py
x, y = 1000, 10

# unlike x == y above, x != y will execute the if statement's code block because x is not equal to y, or 1000 is not equal to 10.
if x != y:
    print(f"{x} is not equal to {y}")
```

<span style="font-size:1.3em;">Greater Than & Lesser Than</span>

We can also test a variable to see if it is greater than another number or variable.

```py
x, y = 1000, 100

if x > y:
    print(f"{x} is greater than {y}")
```

This will of course not run because x is not less than y; however, this might be the intended effect. Perhaps, we do not wish it to run.

```py
x, y = 1000, 100

if x < y:
    print(f"{x} is less than {y}")
```

<span style="font-size:1.3em;">... or equal to</span>

We would use the `>=` and `<=` operators to achieve the exact same effect above, in addition to the inclusion of the endpoints being compared.

```py
if 101 >= 100:
    print("101 is greater than or equal to 100")

if 100 <= 101:
    print("100 is less than or equal to 101")
```

<a href="https://docs.python.org/3/reference/expressions.html#comparisons" style="font-size:1.3em;">Chained Comparisons</a>

Comparisons can be chained arbitrarily. This could prove useful if you wanted to perform an operation on only a certain subset or range of an iteration. 

```py
if x < y and y <= z:
    pass

# equivalent to the above
# using the chained syntax
if x < y <= z:
    pass
```

If you haven't gone through our fundamentals class on iteration please refer to [for](http://bit.ly/3ZYw2Pk) and [while](http://bit.ly/426oyvm).

<!-- > Comparisons can be chained arbitrarily, e.g., x < y <= z is equivalent to x < y and y <= z, except that y is evaluated only once (but in both cases z is not evaluated at all when x < y is found to be false). -->

```py
for i in range(10):
    if 0 <= i and i <= 3:
        print(i)
    else:
        print(None)

# using chained comparison
for i in range(10):
    if 0 <= i <= 3:
        print(i)
    else:
        print(None)
'''   
0
1
2
3
None
None
None
None
None
None
'''
```

```py
# i is between -3 and 5 including the endpoints
for i in range(-3, 5+1):
    if 0 <= i <= 2:
        print(f"Index: {i:>2}, do something")
    else:
        print(f"Index: {i:>2}, ----------")

'''
Index: -3, ----------
Index: -2, ----------
Index: -1, ----------
Index:  0, do something
Index:  1, do something
Index:  2, do something
Index:  3, ----------
Index:  4, ----------
Index:  5, ----------
'''
```

<span style="font-size:1.6em;">The If-Elif-Else Chain</span>

The if statement can also utilize optional `elif` (short for ‘else if’), and `else` clauses. The if statement selects exactly one suite by evaluating the expressions one by one until one is found to be true then that suite is executed. If all expressions are false, the suite of the else clause, if present, is executed.

```py
x, y = 100, 5

# elif omitted
if x > y:
    print(f"It is true that {x} is greater than {y}")
else:
    print(f"{x} is not greater than {y}")

# else omitted
if x > y:
    print(f"It is true that {x} is greater than {y}")
elif x < y:
    print(f"It is true that {x} is less than {y}")

# if-elif-else chain
# else only on equality
if x > y:
    print(f"It is true that {x} is greater than {y}")
elif x < y:
    print(f"It is true that {x} is less than {y}")
else:
    print(f"{x} is neither greater than nor less than {y}")

# multiple elif clauses
if x > y:
    print(f"It is true that {x} is greater than {y}")
elif x < y:
    print(f"It is true that {x} is less than {y}")
elif x == y:
    print(f"{x} is equal to {y}")
else:
    print(f"never executed")
```

<span style="font-size:1.6em;">Logical Operators & Multiple Conditions</span>

|Logical|Operators|
|:-:|:-:|
|Logical AND|`a and b`|
|Logical OR|`a or b`|
|Logical NOT|`not(a or b)`<br>`not a and not b`|

The logical `AND` operator can be implemented in the following ways within the if statement, each are identical, with the last example employing a Chained Comparison.

```py
x = 7

# acceptable 0-9
if x >= 0 and x <= 9:
    pass

# acceptable 0-9
if 0 <= x and x <= 9:
    pass

# acceptable 0-9
if 0 <= x <= 9:
    pass
```

The Logical `OR` operator evaluates to true if either condition is met. The example below will run because x is greater than 3. If this had used `AND` the code would not have executed because both sides of the comparison would have had to evaluate to true.

```py
x = 7

if x > 3 or x > 1000:
    print("condition met")
```

You can also invert or negate a condition with the logical `NOT` operator. The first example will not run because the condition is, of course, false. The second example inverts the false boolean into a true one.

```py
false_condition = False

if false_condition:
    print("Never reached.")

if not false_condition:
    print("This will execute.")
```

Another good thing to understand is De Morgan’s theorem. This theorem states that the negation of an `OR` is the `AND` of the negations; and the negation of a `AND` is the `OR` of the negations.”

> “the negation of a disjunction is the conjunction of the negations;<br>and the negation of a conjunction is the disjunction of the negations.”

```py
( not True and not False ) == ( not (True or  False) )
( not True or  not False ) == ( not (True and False) )
```

<!-- <span style="font-size:1.6em;">Built-ins</span> -->

<span style="font-size:1.6em;">Testing For Membership</span>

|Membership|Operators|
|:-:|:-:|
|True if sequence a is in b|`a in b`|
|True if sequence a is not in b|`a not in b`|

We can also use the if statement in conjunction with the membership operator and a list to check and see if a list contains a certain value. The [all()](https://docs.python.org/3/library/functions.html#all) built-in function has a similar function to chaining `AND` without the messy code. When combined with a list comprehension, we can really reduce our code down to a clean and succinct snippet.

```py
felines  = ['cheetah', 'puma', 'jaguar', 'leopard', 'lion', 'lynx', 'tiger', 'balinese', 'maine coon']
domestic = ['balinese', 'maine coon']

# It is true that both domestic cats are in the felines list
# The result is: [True, True] 
[i in felines for i in domestic]

# It is not true that all felines are domestic and so only 2 are true
# [False, False, False, False, False, False, False, True, True]
[i in domestic for i in felines]

```

The following examples will return `True` and execute the code block underneath the if statement. The [any()](https://docs.python.org/3/library/functions.html#any) built-in is the analogous `OR` equivalent.

```py
# If *all* domestic cats are felines return True
# Use all if you want every item to be True
if all([i in felines for i in domestic]):
    print("do something")

# If *any* domestic cats are felines return True
# Use any if you only care that at least one is True
if any([i in felines for i in domestic]):
    print("do something")

# If *any* felines are domestic cats return True
if any([i in domestic for i in felines]):
    print("do something")
```

The following examples will return `False` and not execute the code block underneath the if statement.

```py
# not all felines are domestic, therefore False
if all([i in domestic for i in felines]):
    print("do something")
```

<!-- The old fashioned way would be to chain logical operators or use iteration. For instance if we wanted to prove that all domestic cats are felines. We could use the `all()` built-in or we could use De Morgan’s theorem. -->

One way of visualizing what could be happening inside the all() built-in function is to make a function of our own. If you have not taken our course on function definitions you may want to do that before attempting to understand this. Only for demonstration purposes.

```py
# If *all* domestic cats are felines return True
if all([i in felines for i in domestic]):
    print("do something")

# Iterating through all domestic cat breeds
# and testing their membership to felines
def all_true(domestic_x, felines_y):
    try:
        for d in domestic_x:
            assert d in felines_y, "False detected"
    except AssertionError as error:
        print(f"{error}: {d}")
        return False
    
    return True
```

<!-- <span style="font-size:1.6em;">Iteration</span>

If there're many values you want to check for, the if statement and several conditions or elif clauses can get really redundant, and a loop is in order.

```py
list_of_ints = [1,2,3,4,5,7,9]
check_for    = [1,3,7,9]

for i in check_for:
    if i in list_of_ints:
        print(f"{i} is in list")

'''
1 is in list
3 is in list
7 is in list
9 is in list
'''
```

```py
list_of_ints = [1,2,3,4,5,7]
check_for    = [1,3,7,9]

for i in check_for:
    if i in list_of_ints:
        print(f"{i} is in list")
    else:
        print(f"{i} is NOT in list!")

'''
1 is in list
3 is in list
7 is in list
9 is NOT in list!
'''
``` -->

<!-- ```py
list_of_ints = [1,2,3,4,5,7,9]
check_for    = [1,3,7,9]

if all([i in list_of_ints for i in check_for]):
    print("all elements of check_for are within list_of_ints")

# if 3 were missing this is how we'd know
list_of_ints.remove(3)

if all([i in list_of_ints for i in check_for]):
    print("all elements of check_for are within list_of_ints")
else:
    print("one of the elements in check_for is missing from list_of_ints")
``` -->

<!-- ```py
for i in range(-10, 15+1):
    if 0 <= i <= 9:
        print(i)
    else:
        print(f"[!] {i}")
``` -->

<!-- It could also be written, in such a way, as to place two conditions in the if clause. However if one is missing we'd not know the other was present unless we used an or instead of and. -->


<!-- ```py
list_of_ints = [1,2,3,4,5,7,9]

# both being present will execute (both only)
if 2 in list_of_ints and 4 in list_of_ints:
    print("both are in list")
else:
    print("neither are in list")

# either being present will execute (both or 1)
if 2 in list_of_ints or 4 in list_of_ints:
    print("2 or 4 is present in the list")
else:
    print("neither are in list")
``` -->

<!-- <span style="font-size:1.6em;">Testing For Membership</span>

|Membership|Operators|
|:-:|:-:|
|True if sequence a is in b|`a in b`|
|True if sequence a is not in b|`a not in b`|

We can also use the if statement in conjunction with the membership operator and a list to check and see if a list contains a certain value. In this example, only the else clause gets executed, because neither  2 or 4 was found in the List.

```py
list_of_ints = [1,3,5,7,9]

if 2 in list_of_ints:
    print("Two was found in the list!")
elif 4 in list_of_ints:
    print("four was found in the list!")
else:
    print("Neither 2 or 4 was found in the List!")
```

If we add 2 and 4 to the list, because only one suite ever gets executed, we never find out that 4 is a part of the list and only 2!

```py
list_of_ints = [1,2,3,4,5,7,9]

if 2 in list_of_ints:
    print("Two was found in the list!")
elif 4 in list_of_ints:
    print("four was found in the list!")
else:
    print("Neither 2 or 4 was found in the List!")
```

This is where it would be useful to use multiple if statements or iteration.

```py
list_of_ints = [1,2,3,4,5,7,9]

# executed
if 2 in list_of_ints:
    print("Two was found in the list!")

# executed
if 4 in list_of_ints:
    print("four was found in the list!")

# not executed
# if not (2 in list_of_ints or 4 in list_of_ints):
if not 2 in list_of_ints and not 4 in list_of_ints:
    print("Neither 2 or 4 was found in the List!")

``` -->

<!-- <span style="font-size:1.6em;">Membership</span> -->

<!-- We can also use the if statement in conjunction with the membership operator and a list to check and see if a list contains a certain value. In this example, only the else clause gets executed, because neither  2 or 4 was found in the List.

```py
list_of_ints = [1,3,5,7,9]

if 2 in list_of_ints:
    print("Two was found in the list!")
elif 4 in list_of_ints:
    print("four was found in the list!")
else:
    print("Neither 2 or 4 was found in the List!")
```

If we add 2 and 4 to the list, because only one suite ever gets executed, we never find out that 4 is a part of the list and only 2!

```py
list_of_ints = [1,2,3,4,5,7,9]

if 2 in list_of_ints:
    print("Two was found in the list!")
elif 4 in list_of_ints:
    print("four was found in the list!")
else:
    print("Neither 2 or 4 was found in the List!")
```

This is where it would be useful to use multiple if statements.

```py
list_of_ints = [1,2,3,4,5,7,9]

# executed
if 2 in list_of_ints:
    print("Two was found in the list!")

# executed
if 4 in list_of_ints:
    print("four was found in the list!")

# not executed
# if not (2 in list_of_ints or 4 in list_of_ints):
if not 2 in list_of_ints and not 4 in list_of_ints:
    print("Neither 2 or 4 was found in the List!") 
```
-->

<!-- <span style="font-size:1.6em;">Multiple Conditions</span> -->




<!-- The next question is, how do we know which element is missing? We'll have to employ a for loop again.

```py
list_of_ints = [1,2,4,5,7,9]
check_for    = [1,3,7,9]

for i in check_for:
    if i not in list_of_ints:
        print(i)

'''
3
'''
``` -->

<!-- ```py
list_of_ints = [1,2,3,4,5,7,9]
check_for    = [1,3,7,9]
try:
    for i in list_of_ints:
        print(i)
        if i in check_for:
            break
    else:
        raise ValueError("Missing value")

except ValueError as error:
    print(f"[!] {error}: 100 not found")
``` -->

<!-- Here is an example of finding out whether or not and element appears in a list that shouldn't. Here we have some possibly edible food and we want to see if there is something inedible. If anything inedible is found, the program will raise an exception.

```py
food     = ["cake", "donut", "pancake", "rock", "waffle"]
inedible = ["rock", "stick"]

try:
    for i in food:
        if i in inedible:
            raise LookupError("Inedible object found")

        print(f"[+] {i.capitalize()}s are edible.")

except LookupError as error:
    print(f"[!] {error}: {i.capitalize()}s are not edible!")


'''
[+] Cakes are edible.
[+] Donuts are edible.
[+] Pancakes are edible.
[!] Inedible object found: Rocks are not edible!
'''
``` -->
