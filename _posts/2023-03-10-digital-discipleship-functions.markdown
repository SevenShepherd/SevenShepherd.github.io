---
layout: post
title: "🪀 Fundamentals Of Digital Discipleship, Part XVI: Function Definitions & Decorators"
date: 2023-03-10 02:30:00 -0500
categories: digital computer programming python ministry
published: true
---

<a href="https://docs.python.org/3/reference/compound_stmts.html#function-definitions" style="font-weight:italic;font-size:2em;">Function Definitions</a>

A function definition is an executable statement that gets executed only when the function is called, and may be wrapped by one or more decorator expressions. Decorator expressions are evaluated when the function is defined and can be nested (applied bottom to top).

<span style="font-weight:italic;font-size:1.4em;">Syntax</span>

Let's examine the syntax of a function definition. We can use the **def** keyword to create our function. After the keyword we supply a name which is bound to the current local namespace to a function object which wraps the executable code. We can then define the **parameters** that our function will accept, which will handle **arguments** passed into the function call.

> Parameters are defined by the names that appear in a function definition, whereas arguments are the values actually passed to a function when calling it. Parameters define what kind of arguments a function can accept. &mdash; [What is the difference between arguments and parameters?](https://docs.python.org/3/faq/programming.html#faq-argument-vs-parameter)

The text on the second line is a comment called a **docstring**, which describes what the function does. Finally the **code block** is supplied, in this case a simple print statement that echos the passed in argument. Simple!

```py
# basic function example
def function_name(parameter):
    """docstring"""
    print(parameter)

# This is the function call
# that prompts "argument"
function_name("argument")
```

<!-- <span style="font-weight:italic;font-size:1.4em;">Return</span> -->

The return keyword allows us to take a value from within a function and send it back, or return it, to the line that called the function. This allows us to simplify the main parts of our program. Functions, like those above, that are without a return statement do return a value, called None; however, from here on out we will mostly be returning specific values.

<!-- by offloading tasks to subroutines that can fetch a value for us without  -->

```py
# Alternatively
def function_name(parameter):
    """returns argument"""
    return parameter

# prompts "Hello, World!" in the terminal
message = function_return("Hello, World!")
print(message)
```

<a href="https://docs.python.org/3/tutorial/controlflow.html#default-argument-values" style="font-weight:italic;font-size:1.4em;">Default Arguments</a>

We can implement a default parameter value by using `'parameter = expression'`. If we utilize such an expression the corresponding argument may be omitted from a call, in which case the parameter’s default value will be substituted.

```py
# basic function example
def function_name(parameter = "default"):
    """docstring"""
    print(parameter)

# This is the function call
# that prompts "argument"
function_name("argument")

# prompts "default" because
# default value was substituted
function_name()
```

<a href="https://docs.python.org/3/tutorial/controlflow.html#keyword-arguments" style="font-weight:italic;font-size:1.4em;">Keyword Arguments</a>

There're two kinds of parameters we can define in a function, and [arguments](https://docs.python.org/3/glossary.html#term-argument) that can be passed into the function call. The first we've covered already, the *positional argument*, and the other is the *keyword argument*. 
- A *positional argument* preceded by an asterisk in the parameter `*args` tells the Python interpreter to create a tuple containing positional arguments of all the values received by this function. 
- A *keyword argument* preceded by `**kwargs` two asterisks creates a dictionary containing all keyword arguments. The way *keyword arguments* work should be reminiscent of how we can create dictionaries using the built-in `dict(a=1, b=2)` or braces `{'a':1, 'b':2}`.

```py
# I. positional arguments
def positional(*args):
    print(type(args), args)

# identical function calls
positional(7, 8)
positional(*(7, 8))

# II. keyword arguments
def keyword(**kwargs):
    print(type(kwargs), kwargs)

# identical function calls
keyword(completeness=7, new_beginning=8)
keyword(**{'completeness': 7, 'new_beginning': 8})
```

Let's combine the use of both for example.

```py
def pos_and_key(*args, **kwargs):
    """docstring"""

    print(type(args), args)
    print(type(kwargs), kwargs)

# both function calls are identical
pos_and_key('a', 'b', 'c', one=1, two=2, three=3)
pos_and_key(*('a', 'b', 'c'), **{'one':1, 'two':2, 'three':3})

'''
<class 'tuple'> ('a', 'b', 'c')
<class 'dict'> {'one': 1, 'two': 2, 'three': 3}
'''
```

<!-- ```py
def function_name(*args):
    print(type(args), args)

# <function function_name at 0x...>
function_name

# <class 'tuple'> ()
function_name()

# <class 'tuple'> ('hello',)
function_name("hello")

# <class 'tuple'> ('up', 'down', 'left', 'right', 'forward', 'backward')
function_name("up", "down", "left", "right", "forward", "backward")
``` -->

We can also assign each positional argument an individual variable handle within the function for processing.

```py
def function_name(*args):
    a, b, c, d, e = args
    print(a, b, c, d, e)

# 1 2 3
my_list = [1, 2, 3, 4, 5]
function_name(*my_list)
```

There's also a handy trick you can perform to grab hold of the initial argument.

```py
def function_name(*args):
    a, b, *c = args
    print(a, b, c)

# prompts 1 2 [3, 4, 5]
# a = 1, b = 2, c = [3, 4, 5]
my_list = [1, 2, 3, 4, 5]
function_name(*my_list)
```

When you want to discard all but the first variable of an incoming tuple you can use the _ to indicate this more idiomatically.

```py
def function_name(*args):
    up, *_ = args

    print(up)
    print(_)

# up
# ['down', 'left', 'right', 'forward', 'backward']
function_name("up", "down", "left", "right", "forward", "backward")
```

The reverse can be achieved as well using the unpacking syntax of asterisked variables.

```py
def function_name(*args):
    *_, back = args

    print(back)
    print(_)

# backward
# ['up', 'down', 'left', 'right', 'forward']
function_name("up", "down", "left", "right", "forward", "backward")
```

<a href="https://docs.python.org/3/tutorial/controlflow.html#special-parameters" style="font-weight:italic;font-size:1.4em;">Special Parameters</a>

Most of the time we pass arguments to a function by position or explicitly using a keyword. The documentation gives us a nice visual of how we can customize our function definition's parameters using `'/'` and `'*'`, this is of course optional and only used for readability and performance. If used they indicate that the function expects the kind of parameter indicated, raising TypeError otherwise.

```
def f(pos1, pos2, /, pos_or_kwd, *, kwd1, kwd2):
      -----------    ----------     ----------
        |             |                  |
        |        Positional or keyword   |
        |                                - Keyword only
         -- Positional only
```

This is much less flexible and much more restrictive than using the asterisked unpacking syntax, but as stated above, the purpose of such definitions is readability and performance.

```py
# standard allows both positional & keyword
def standard_function(arg):
    print(arg)

# expects positional arguments only
def positional_only(arg, /):
    print(arg)

positional_only(1)

# expects keyword arguments only
def keyword_only(*, arg):
    print(arg)

keyword_only(arg=1)

# this is a combined example
def positional_and_keyword(pos_only, /, standard, *, kwd_only):
    print(pos_only, standard, kwd_only)

positional_and_keyword("hi", "bye", kwd_only=1)
```

<a href="https://peps.python.org/pep-0484/" style="font-weight:italic;font-size:1.4em;">Type Hints</a>

New to Python 3.5+ are type hints, annotations that allow you to specify the expected types of variables, function arguments, and return values. Unlike special parameters, and more like the asterisked unpacking syntax, type hints are not enforced by the Python interpreter, and the code will still run even if the hints are incorrect. They simply improve code readability, maintainability, and make it easier to catch bugs during development. You can read more about [type hints](https://peps.python.org/pep-0484/) and supporting libraries like [typing](https://docs.python.org/3/library/typing.html#module-typing).

```py
# a standard function definition without type hints
def add_numbers(a, b):
    return a + b

# a function definition utilizing type hints
def add_numbers(a: int, b: int) -> int:
    return a + b
```

<a href="https://docs.python.org/3/reference/expressions.html#lambda" style="font-weight:italic;font-size:2em;">Lambda Expressions</a>

Before moving on to function decorators, i'd like to take a moment to cover lambda expressions. The anonymous function that a lambda expressions creates behaves like a function object. We can use [Callable](https://peps.python.org/pep-0612/) from the typing library to apply type hints to lambda expressions, although it's probably better to use a def when applying type hints.

```py
# function definition
def multiply(a, b):
    return a * b

# identical lambda function
g = lambda a, b: a * b

# utilizing type hints
def multiply(a: int, b: int) -> int:
    return a * b

# similar to function above
from typing import Callable
g: Callable[[int, int], int] = lambda a, b: a * b
```

<a href="https://peps.python.org/pep-0318/" style="font-weight:italic;font-size:2em;">Function Decorators</a>

Function decorators allow you to modify the behavior of a function without changing its source code. Decorator expressions are evaluated when the function is defined and can be nested (applied bottom to top). The decorator syntax what is known as syntactic sugar, which is a term used to describe a feature that makes code easier to read and write. Here is an example of two function definitions which are semantically equivalent:

```py
@decorator
def squared(x):
    return x**2

# semantically equivalent
def squared(x):
    return x**2

squared = decorator(square)
```

Let's learn how to create our own decorator so we can wrap functions. A decorator has an outer and inner function, with the latter wrapping or handling the parameters & arguments, and the former passing in the function handle so the inner function can access it.

```py
def decorator(func):
    def wrapper(*args, **kwargs):
        # do something before function call
        result = func(*args, **kwargs)
        # do something after function call
        return result
    return wrapper

# simple function definition
@decorator
def add_numbers(a, b):
    return a + b
```

You'll notice that when we call add_numbers, it gives us the metadata of the inner wrapper instead of the metadata of add_numbers. We can fix this issue by applying the @wraps decorator supplied by the functools library to the inner wrapping function of our decorator. @wraps is used to preserve the metadata of the calling function.

```py
from functools import wraps

def decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        # do something before function call
        result = func(*args, **kwargs)
        # do something after function call
        return result
    return wrapper

# simple function definition
@decorator
def add_numbers(a, b):
    return a + b
```

<!-- ```py
from functools import lru_cache

def decorator(func):
    @lru_cache(maxsize=None)
    def wrapper(*args, **kwargs):
        # do something before function call
        result = func(*args, **kwargs)
        # do something after function call
        return result
    return wrapper

# simple function definition
@decorator
def add_numbers(a, b):
    return a + b
``` -->


