---
layout: post
title: "🚫 Fundamentals Of Digital Discipleship, Part XIII: Exception Handling"
date: 2023-03-10 02:30:00 -0500
categories: digital computer programming python ministry
published: true
---

<!-- <span style="font-style:Italic;font-size:32px;">Chapter Header</span>

<span style="font-style:Italic;font-size:24px;">Sub Chapter Header</span> -->

<a href="https://docs.python.org/3/reference/compound_stmts.html#the-try-statement" style="font-weight:italic;font-size:2em;">The Try Statement</a>

Exceptions break out of the normal control flow of a program and indicate that an error has taken place. The try and except keywords make catching errors a fairly simple task. We can simulate an error with the [raise](https://docs.python.org/3/reference/simple_stmts.html#the-raise-statement) statement. We can also use the simpler [assert](https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement) statement.

<a href="https://docs.python.org/3/library/exceptions.html#concrete-exceptions" style="font-weight:italic;font-size:1.6em;">Concrete Exceptions</a>

|Exception||
|:-:|:-:|
|[`AssertionError`](https://docs.python.org/3/library/exceptions.html#AssertionError)|Raised when an assert statement fails.|
|[`AttributeError`](https://docs.python.org/3/library/exceptions.html#AttributeError)|Raised when an [attribute reference](https://docs.python.org/3/reference/expressions.html#attribute-references) or assignment fails.|
|[`EOFError`](https://docs.python.org/3/library/exceptions.html#EOFError)|Raised when the input() function hits an end-of-file condition (EOF) without reading any data.|
|[`IndexError`](https://docs.python.org/3/library/exceptions.html#IndexError)|Raised when a sequence subscript is out of range.|
|[`KeyError`](https://docs.python.org/3/library/exceptions.html#KeyError)|Raised when a mapping (dictionary) key is not found in the set of existing keys.|
|[`KeyboardInterrupt`](https://docs.python.org/3/library/exceptions.html#KeyboardInterrupt)|Raised when the user hits the interrupt key (normally Control-C or Delete).|
|[`NameError`](https://docs.python.org/3/library/exceptions.html#NameError)|Raised when a local or global name is not found.|
|[`OSError`](https://docs.python.org/3/library/exceptions.html#OSError)|This exception is raised when a system function returns a system-related error, including I/O failures such as “file not found” or “disk full”.|
|[`RecursionError`](https://docs.python.org/3/library/exceptions.html#RecursionError)|Raised when the interpreter detects that the [maximum recursion depth](https://docs.python.org/3/library/sys.html#sys.getrecursionlimit) is exceeded.|
|[`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError)|Raised when an operation or function is applied to an object of inappropriate type.|
|[`ValueError`](https://docs.python.org/3/library/exceptions.html#ValueError)|Raised when an operation or function receives an argument that has the right type but an inappropriate value.|
|[`ZeroDivisionError`](https://docs.python.org/3/library/exceptions.html#ValueError)|Raised when the second argument of a division or modulo operation is zero.|

<a href="https://docs.python.org/3/library/exceptions.html#os-exceptions" style="font-weight:italic;font-size:1.6em;">OS exceptions</a>

These exceptions are subclasses of [OSError](https://docs.python.org/3/library/exceptions.html#OSError).

|Exception||
|:-:|:-:|
|[`FileExistsError`](https://docs.python.org/3/library/exceptions.html#FileExistsError)|Raised when trying to create a file or directory which already exists. Corresponds to errno [EEXIST](https://docs.python.org/3/library/errno.html#errno.EEXIST).|
|[`FileNotFoundError`](https://docs.python.org/3/library/exceptions.html#FileNotFoundError)|Raised when a file or directory is requested but doesn’t exist. Corresponds to errno [ENOENT](https://docs.python.org/3/library/errno.html#errno.ENOENT).|
|[`IsADirectoryError`](https://docs.python.org/3/library/exceptions.html#IsADirectoryError)|Raised when a file operation (such as os.remove()) is requested on a directory. Corresponds to errno [EISDIR](https://docs.python.org/3/library/errno.html#errno.EISDIR).|
|[`NotADirectoryError`](https://docs.python.org/3/library/exceptions.html#NotADirectoryError)|Raised when a directory operation (such as os.listdir()) is requested on something which is not a directory. Corresponds to errno [ENOTDIR](https://docs.python.org/3/library/errno.html#errno.ENOTDIR).|

<!-- |`ImportError`|Raised when the import statement has troubles trying to load a module. Also raised when the “from list” in from ... import has a name that cannot be found.| -->

<span style="font-weight:italic;font-size:1.4em;">AssertionError & TypeError</span>

The first example will compare raising a TypeError with [the raise statement](https://docs.python.org/3/reference/simple_stmts.html?highlight=assert#the-raise-statement), with raising an AssertionError with [the assert statement](https://docs.python.org/3/reference/simple_stmts.html?highlight=assert#the-assert-statement). The [isinstance(object, classinfo)](https://docs.python.org/3/library/functions.html#isinstance) built-in function gives us some useful functionality that returns True if the object argument is an instance of the classinfo argument. If object is not an object of the given type, the function always returns False. classinfo can also be a tuple of multiple types to check against. TypeError is raised if classinfo is not a type or tuple of types.

```py
# Raise
try:
    if not isinstance(x, int):
        raise TypeError("The variable needs to be an integer!")
except TypeError as error:
    print(error)
 
# Assert
try:
    assert isinstance(x, int), "Integers only!"
except AssertionError as error:
    print(error)
```

We can also make use of an else clause like we can with the compound if statement.

```py
# Raise
try:
    if not isinstance(x, int):
        raise TypeError("The variable needs to be an integer!")
except TypeError as error:
    print(error)
else:
    print("The variable has passed type inspection.")

# Assert
try:
    assert isinstance(x, int), "Integers only!"
except AssertionError as error:
    print(error)
else:
    print("The variable has passed type inspection.")
```

Python's exception handling also supplies us with a finally clause which gets executed without fail no matter the outcome of the try, except, and else.

```py
# Raise
try:
    if not isinstance(x, int):
        raise TypeError("The variable needs to be an integer!")
except TypeError as error:
    print(error)
else:
    print("The variable has passed type inspection.")
finally:
    print("This will run either way")

# Assert
try:
    assert isinstance(x, int), "Integers only!"
except AssertionError as error:
    print(error)
else:
    print("The variable has passed type inspection.")
finally:
    print("This will run either way")
```

It should be noted that there can be multiple except clauses in a try-except-else-finally just like there can be multiple elif clauses in an if-elif-else chain. The else clause and finally are optional and do not interfere with using multiple except clauses.

```py
try:
    assert isinstance(x, int), "Integers only!"

# will raise if x is float or any other type
except AssertionError as error:
    print(error)

# never reached
except TypeError as error:
    print(error)
```

Because TypeError is raised if classinfo is not a type or tuple of types, we actually have two exceptions we can catch with an assert isinstance.

```py
try:
    # for example we enter the wrong classinfo
    assert isinstance(x, 1), "Integers only!"

# never raised because of classinfo
except AssertionError as error:
    print(error)

# raised because classinfo should 
# be a type or tuple of types
except TypeError as error:
    print(error)
```

<span style="font-weight:italic;font-size:1.4em;">TypeError & ValueError</span>

It's important to know the difference between a TypeError and a ValueError. One checks the type and the other it's value. Simple isn't it, but how do we implement it?

```py
number = "not a number"

try:
    if not isinstance(number, (int, float)):
        raise TypeError("Wrong Type!")

    if not 0 <= number <= 9:
        raise ValueError("number should be 0 - 9")

# raised because number is a string
except TypeError as error:
    print(error)

# never caught
except ValueError as error:
    print(error)
```

Given the correct type, ValueError is raised and handled if number falls outside of the defined range.

```py
number = 70*770

try:
    if not isinstance(number, (int, float)):
        raise TypeError("Wrong Type!")

    if not 0 <= number <= 9:
        raise ValueError("number should be 0 - 9")

# never caught because number is an int
except TypeError as error:
    print(error)

# catches & prompts: number should be 0 - 9
except ValueError as error:
    print(error)
```

<span style="font-weight:italic;font-size:1.4em;">AttributeError & NameError</span>

An AttributeError is raised when an [attribute reference](https://docs.python.org/3/reference/expressions.html#attribute-references) or assignment fails. The following example would throw `AttributeError: type object 'storm' has no attribute 'lightning'` without the try-except statement.

```py
class storm:
    def rain(self):
        pass

try:
    storm.lightning()
except AttributeError:
    print("The lightning method does not exist.")
```

Trying to call or assign a variable that does not exist will raise a NameError exception. Without our except, this example would normally throw `NameError: name 'no_variable' is not defined`.

```py
# trying to call or assign a
# variable that does not exist
# will raise a NameError
try:
    no_variable
except NameError:
    print("This variable does not exist.")
```


<span style="font-weight:italic;font-size:1.4em;">KeyboardInterrupt & EOFError</span>

KeyboardInterrupt is raised when the user hits the interrupt key (normally Control-C or Delete). Note that the input() function itself already includes a built-in try-except block that catches EOFError and raises a KeyboardInterrupt instead. This is because in a console or terminal window, the user can signal the end of the input by pressing the Ctrl-C key combination, which normally raises a KeyboardInterrupt.

<!-- EOFError is raised when the input() function hits an end-of-file condition (EOF) without reading any data. -->

```py
try:

    # infinite loop
    while True:
        something = input("Enter something: ")
        print(something)

except KeyboardInterrupt:
    print("Control-C or Delete pressed.")
```

For EOFError, the open() function is used to open a file called input.txt, and then the readline() method is used to read the first line of input from the file. If the end of the file is reached unexpectedly before the first line of input is read, an EOFError is raised and the corresponding except block is executed.

```py
try:
    with open('input.txt') as f:
        user_input = f.readline()
except EOFError:
    print("Error: Reached end of input unexpectedly.")
```

<span style="font-weight:italic;font-size:1.4em;">IndexError & KeyError</span>

An IndexError is raised when a sequence subscript is out of range. We can easily catch this within our code with a simple try-except chain.

```py
ordo_salutis = [
    "Foreknowledge", 
    "Predestination",
    "Effectual Calling",
    "Regeneration",
    "Saving Faith",
    "Repentance",
    "Justification",
    "Adoption",
    "Sanctification",
    "Perseverance",
    "Glorification"
]

ordo_salutis[11]
'''
Traceback (most recent call last):
  File "<pyshell#5>", line 1, in <module>
    ordo_salutis[11]
IndexError: list index out of range
'''

try:
    ordo_salutis[11]
except IndexError:
    print(f"Range is 0 to {len(ordo_salutis)-1}")
```

The simplest example of catching a KeyError is to use a non-existent key in a dictionary. Since owls do not belong to the muscicapoidea superfamily of infraorder Passerides, as we have made sure in our dictionary of lists definition, a KeyError will be thrown.

```py
muscicapoidea = {
    'buphagidae'  : ['oxpeckers'],
    'cinclidae'   : ['dippers'],
    'elachuridae' : ['spotted elachura'],
    'mimidae'     : ['mockingbirds', 'thrashers'],
    'muscicapidae': ['flycatchers', 'relatives'],
    'sturnidae'   : ['starlings', 'mynas'],
    'turdidae'    : ['thrushes', 'relatives']
}

# throws KeyError
muscicapoidea['owl']

'''
Traceback (most recent call last):
  File "<pyshell#83>", line 1, in <module>
    muscicapoidea['owl']
KeyError: 'owl'
'''

try:
    owl = 'strigiformes'
    print(muscicapoidea[owl])
except KeyError:
    print(f"An owl is not a muscicapoidea.")
```

<span style="font-weight:italic;font-size:1.4em;">OS Exceptions</span>

In this example, the FileNotFoundError will be caught and print *"This file does not exist."* to the terminal.

```py
try:
    file_handle = open("read.txt" , 'rt')

# Raised when trying to create a file 
# or directory which already exists.
except FileExistsError:
    print("This file already exists.")

# Raised when a file or directory
# is requested but doesn’t exist.
except FileNotFoundError:
    print("This file does not exist.")

# Raised when a file operation
# is requested on a directory.
except IsADirectoryError:
    print("This is not a file.")

# Raised when a directory operation is 
# requested on something which is not a directory.
except NotADirectoryError:
    print("This is not a directory.")
```

We can also catch them all with one of the [base exception](https://docs.python.org/3/library/exceptions.html#base-classes) classes, specifically the built-in exception ['Exception'](https://docs.python.org/3/library/exceptions.html#Exception), which is what all built-in, and non-system-exiting exceptions are derived from.

```py
try:
    file_handle = open("read.txt" , 'rt')

# [Errno 2] No such file or directory: 'read.txt'
except OSError as error:
    print(error)
```

<span style="font-weight:italic;font-size:1.4em;">ZeroDivisionError</span>

This built-in exception is particularly useful for those who are performing arithmetic. Division by zero is an arithmetic operation that results in an undefined or indeterminate value because it is impossible to divide any number by zero.

```py
try:
    print(1/0)
except ZeroDivisionError:
    print("You cannot divide by zero!")
```

The [exception hierarchy](https://docs.python.org/3/library/exceptions.html#exception-hierarchy) is a useful visual to reference taken from the documentation.

```
BaseException
 ├── BaseExceptionGroup
 ├── GeneratorExit
 ├── KeyboardInterrupt
 ├── SystemExit
 └── Exception
      ├── ArithmeticError
      │    ├── FloatingPointError
      │    ├── OverflowError
      │    └── ZeroDivisionError
      ├── AssertionError
      ├── AttributeError
      ├── BufferError
      ├── EOFError
      ├── ExceptionGroup [BaseExceptionGroup]
      ├── ImportError
      │    └── ModuleNotFoundError
      ├── LookupError
      │    ├── IndexError
      │    └── KeyError
      ├── MemoryError
      ├── NameError
      │    └── UnboundLocalError
      ├── OSError
      │    ├── BlockingIOError
      │    ├── ChildProcessError
      │    ├── ConnectionError
      │    │    ├── BrokenPipeError
      │    │    ├── ConnectionAbortedError
      │    │    ├── ConnectionRefusedError
      │    │    └── ConnectionResetError
      │    ├── FileExistsError
      │    ├── FileNotFoundError
      │    ├── InterruptedError
      │    ├── IsADirectoryError
      │    ├── NotADirectoryError
      │    ├── PermissionError
      │    ├── ProcessLookupError
      │    └── TimeoutError
      ├── ReferenceError
      ├── RuntimeError
      │    ├── NotImplementedError
      │    └── RecursionError
      ├── StopAsyncIteration
      ├── StopIteration
      ├── SyntaxError
      │    └── IndentationError
      │         └── TabError
      ├── SystemError
      ├── TypeError
      ├── ValueError
      │    └── UnicodeError
      │         ├── UnicodeDecodeError
      │         ├── UnicodeEncodeError
      │         └── UnicodeTranslateError
      └── Warning
           ├── BytesWarning
           ├── DeprecationWarning
           ├── EncodingWarning
           ├── FutureWarning
           ├── ImportWarning
           ├── PendingDeprecationWarning
           ├── ResourceWarning
           ├── RuntimeWarning
           ├── SyntaxWarning
           ├── UnicodeWarning
           └── UserWarning
```

<!-- ```py
try:
    # take user input 
    number = int(input("Enter a number: "))

    # type conversion
    # if isinstance(number, str) and number.isdecimal():
    #     number = int(number)

    # number should be an integer
    if not isinstance(number, int):
        raise TypeError("number should be an integer")

    # number should be 0 - 9
    if not 0 <= number <= 9:
        raise ValueError("number should be 0 - 9")
        
    # ZeroDivisionError
    print(number/0)

# chained except clauses
except TypeError as error:
    print("Number should be an integer")

except ValueError as error:
    print("Number should be 0 - 9.")

except ZeroDivisionError:
    print("ZeroDivisionError")
``` -->


