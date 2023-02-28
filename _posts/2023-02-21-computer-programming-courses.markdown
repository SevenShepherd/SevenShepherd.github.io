---
layout: post
title: "💻👨‍💻 Computer Programming Courses And Digital Discipleship"
date: 2023-02-21 01:55:55 -0500
categories: computer programming python ministry
published: true
---

<!-- I know you've waited a long time *unknown* blessed *unknown* *unknown* -->

<!-- 💻🐱‍💻👨‍💻 For Ministry Automation-->

<span style="font-style:Italic;font-size:21px;color:Black;">Hello and welcome,</span>

My name is Ryan and my philosophy is known as autodidacticism. I have been a programmer since the turn of the millennium. In the past, I successfully taught myself how to program in C/C++, grew advanced with Perl, but ultimately my formal language of choice became Python, and as a result, the predominant paradigm you’ll see me implement in this blog is of the imperative rather than declarative variety.

> <sup style="font-weight:bold;">16</sup> Let your light so shine before men, that they may see your good works, and glorify your Father which is in heaven. &mdash; Matthew 5:16 KJV

In 2016 I created a custom programmed and automated Twitter based Christian ministry at [@SevenShepherd](https://twitter.com/SevenShepherd) that has been running successfully ever since, from a custom built raspberry pi single-board computer. From 2016 to the January 2023, this ministry has posted over 2,639,234 tweets, and received more than 7,597,960 likes & retweets. This is approximately [100 lifetimes](https://www.biblegateway.com/passage/?search=Matthew+13%3A1-23%3B+Luke+8%3A4-15%3B+Mark+4%3A2-20&version=NLT) of preaching the gospel message within a 7 year period.

<!-- From 2016 to the January 2023, this ministry has posted over 2.7 million tweets, and received more than 7.6 million likes & retweets. This is approximately 100 lifetimes of preaching the gospel message within a 7 year period. -->

> <sup style="font-weight:bold;">19</sup> Go therefore and make disciples of all nations, baptizing them in<span style="color:#A7A7A7;">[a]</span> the name of the Father and of the Son and of the Holy Spirit, <sup style="font-weight:bold;">20</sup> teaching them to observe all that I have commanded you. And behold, I am with you always, to the end of the age.” &mdash; Matthew 28:19-20 ESV

I've decided to teach my hard won computer programming experience to others in hopes that they would be able to spread the gospel message more efficiently, and in doing so, curb the tides of darkness which is at our very doorstep, threatening the very fabric of our society.

<span style="font-weight:bold;font-size:30px;color:Black;">Content Overview</span>

After much deliberation, all articles pertaining to the Bible will remain free and accessible to everyone at anytime [through our blog](https://bit.ly/3G0CTAO). Instead the way I've decided to support and grow this ministry is by offering courses on computer programming and ministry automation.

> <sup style="font-weight:bold;">16</sup> “·Listen <span style="color:#A7A7A7;">[<sup>L</sup> Look; <sup>T</sup> Behold]</span>, I am sending you out like sheep among wolves. So be as ·clever <span style="color:#A7A7A7;">[wise; shrewd; cunning]</span> as ·snakes <span style="color:#A7A7A7;">[serpents]</span> and as ·innocent <span style="color:#A7A7A7;">[harmless]</span> as doves. &mdash; Matthew 10:16 <a href="https://amzn.to/3vlMXy5" style="color:MediumPurple;">Expanded Bible (EXB)</a>

I have decided to use the Python programming language to teach fundamental programming concepts. This is a language suitable for the beginner, as well as the most advanced computer programmers. Python is used by organizations such as: Google, CERN, NASA, Facebook, Amazon, Instagram, Spotify, Reddit, and Wikipedia.

Some of the more advanced topics and skills that will eventually be covered are as follows: data analysis, botting and automation, machine learning and chatbots, deep learning and neural networks, web programming and blog development, and software development and GUI programming. With the initial emphasis on fundamentals and ministry automation.

<span style="font-weight:bold;font-size:30px;color:Black;">A Basic Introduction To Computer Programming</span>

<span style="font-style:italic;font-size:21px;">What Is Programming?</span>

This will be a very gentle introduction to fundamental concepts of computer programming with the Python programming language. This article will assume the reader is starting from zero. For those of you who may not understand what *"programming is"*, let's start with what *"it is not"*:

- ❌ Programming **is not** repairing computers, printers, or installing software (i.e. operating systems), or hardware (i.e. HDDs, SSDs, GPUs, MOBOs, ...). 
- ✅ Programming **is** a creative process where we create hand written instructions for a computer to complete a task. We achieve this by utilizing a programming language. 

<!-- - ❌ Programming **is not** Computer Science. While all Computer Scientists are Computer Programmers, not all Programmers are Computer Scientists. -->
    
Computers require programmers to tell them what to do, otherwise it will just sit there like a rock. Everything you see and interact with on your phone or PC had a programmer sit down and work out what should happen when you click a button, visit a webpage, or scroll down with your thumb to read the rest of this article.

There are many different types of programming languages, but the best for our purposes is the high-level, multi-paradigm, dynamically typed, garbage collected, cross-platform, "batteries-included" programming language known as Python. Understanding the technical jargon is not required, but looking it up is encouraged. Python's core philosophy is summarized aphoristically in a document called [*"The Zen of Python (PEP 20)."*](https://peps.python.org/pep-0020/) A few of the points are mentioned below:

- Beautiful is better than ugly.
- Explicit is better than implicit.
- Simple is better than complex.
- Complex is better than complicated.
- Readability counts.
- In the face of ambiguity, refuse the temptation to guess.
- There should be one&mdash; and preferably only one &mdash;obvious way to do it.

<span style="font-style:italic;font-size:21px;">Prerequisites</span>

There are two ways you can follow along, both of which require you to install the [Python Interpreter](https://www.python.org/downloads/). For this lesson, the first method is easier. 

- The first method, once you have installed the interpreter, is to use the program called **IDLE** that comes packaged with the interpreter.
- The second way is to run our code from a file. If you decided to use the second way, you'll need to install [Notepad++](https://notepad-plus-plus.org/), which is a very simplistic sourcecode editor that is both free and provides syntax highlighting.

<!-- I want you all to download the program called [Notepad++](https://notepad-plus-plus.org/), which is a very simplistic sourcecode editor that is both free and provides syntax highlighting. I will sometimes use this for small scripts and as an upgrade to notepad. The other program you need to install is the actual [Python Interpreter](https://www.python.org/downloads/). Eventually, you will be required to install [Visual Studio Code](https://code.visualstudio.com/Download); however, this article does not require it. -->

✔️ When installing the [Python Interpreter](https://www.python.org/downloads/), make sure you select the checkbox labeled Add Python to PATH.

<span style="font-style:italic;font-size:21px;">Instructions For First Method</span>

![IDLE](/assets/images/code/IDLE.png)

If you chose the first method, click the start menu in your Windows operating system, and type *"IDLE"* (less quotations) to search for the *"Integrated Development and Learning Environment"* that came bundled with the [Python Interpreter](https://www.python.org/downloads/) you should have installed by this point.

```py
print("Hello, World!")
```

Once IDLE has been opened, type or copy & paste the code above into the program, and then hit enter. You should see something similar to the screenshot above. **Congratulations on running your first program!**

<span style="font-style:italic;font-size:21px;">Instructions For Second Method</span>

![Notepad++](/assets/images/code/Notepad++.png)

If you chose the second method, once having installed the [Python Interpreter](https://www.python.org/downloads/) and [Notepad++](https://notepad-plus-plus.org/). Open [Notepad++](https://notepad-plus-plus.org/), type or copy & paste `print("Hello, World!")` to the editor and save the file to your Desktop, naming it anything you want as long as it ends in *".py"* (less the quotations). main.py or hello.py for example.

Click the start menu and type `cmd.exe` and hit enter or click to run the commandline interface. change the directory to the Desktop where you saved the *.py file. You can do this within the commandline with the `cd` command. Type `cd Desktop`. If that does not work, try `cd %USERPROFILE%\Desktop`.

![CMD](/assets/images/code/cmd.png)

Now you just need to run the code snippet. Type `python main.py` or whatever you have named your file followed by a `.py` within the commandline's black terminal window. If you were successful congratulations on running your first program. In the commandline, you should see *"Hello, World!"* appear in the commandline.

<!-- <span style="font-style:italic;font-size:21px;">Troubleshooting</span>

If you run into problems, ask yourself these questions:

1. Did I save the file to my Desktop?
    - If not the commandline wont be able to find it.
    - You can change directory to wherever you saved it.
    - Just resave to desktop and run the same command.
2. Did I specify to the commandline the correct program name?
    - `python main.py` only works with main.py
    - If you named your program something else, specify it.
3. Did I paste the correct code in the file?
    - Don't forget to paste `print("Hello, World!")`
    - If you saved an empty file nothing will happen.
    - Improper code will result in an error.
4. If you need to run the program again, you don't need to include `cd Desktop` since the directory has already been changed. 
    - Instead simply type `python main.py` -->

<span style="font-weight:bold;font-size:30px;color:Black;">I. Understanding Data Types And Variables</span>

I wanted you all to experience positive feedback before I taught the details to you. The rest of this article will function as the true tutorial starting with data types and variables. If you had issues with the second method, the first method is recommend for this article.

There are many built-in data types in Python, and while it is true that Python is dynamically typed, and that we do not have to declare the type of a variable statically, we still need to understand what is being assigned on the right hand side of the assignment operator. I understand that I've used some words that you do not understand yet, just bare with me as I explain the aforementioned terms.

Before moving on to variables and assignment, let's look at a few of the built in data types that are available to us in the Python programming language. According to the [The Python Standard Library](https://docs.python.org/3/library/stdtypes.html) the principal built-in types are numerics, sequences, mappings, classes, instances and exceptions.

|Data Type|Built-in|
|:-:|:-:|
|Numerics|[int, float, complex](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)|
|Sequences|[list, tuple, range](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)|
|Text Sequence|[str](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)|
|Binary Sequence|[bytes, bytearray, memoryview](https://docs.python.org/3/library/stdtypes.html#binary-sequence-types-bytes-bytearray-memoryview)|
|Set Types|[set, frozenset](https://docs.python.org/3/library/stdtypes.html#set-types-set-frozenset)|
|Mappings|[dict](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict)|
|Boolean Type|bool|

For thoroughness, the aforementioned types can further be subdivided. You don't really need to understand everything in this second chart, nor use everything in the first chart for this tutorial; however, you should know the difference between mutability (modifiable) and immutability (unmodifiable).

<!-- **mutable** (list, set, dict) and **immutable** (tuple, range, str, frozenset). -->

|||
|:-:|:-:|
|Mutable|list, set, dict, bytearray|
|Immutable|int, float, complex, str, bool, bytes, tuple, range, frozenset|
|Ordered|list, tuple, str, dict|
|Unordered|set, frozenset|
|Hashable|str, int, float, complex, bool, bytes, ranges, frozensets, functions, classes, both [built-in](https://docs.python.org/3/library/functions.html) and user-defined|
|Unhashable|list, dict, set, bytearray|

<!-- Let me provide you with some examples of working with these basic building blocks within IDLE or your script. Try copying and pasting some of the lines below. You don't need to use the print function with IDLE, but if you are following with the second method by running your code from a file you will need to wrap the code below in the print function. -->

<!-- Python has many ways of working with output withing the Print function. One such way is string variable interpolation. -->

Let me show you how to work with variables now. You can think of a variable as a named container that you can put things in and store away for another time. Let's create a variable, we'll call it x for simplicity. In order to store a value of data type int within x, we will need to assign the integer to the variable. 

```py
x = 100
```

The statement reads: ***"x is assigned one-hundred"***. The assignment operator in Python and most all other programming languages is the `=` operator. This is not the equality operator like it is in mathematics. In Python we would use `==` for equality. For example, if I wanted to see if the value that now resided in x (100) is *"equal to"* another integer, see below.

```py
x == 10
```

Since x contains that integer 100 from the previous assignment, this comparison will result in a **False** boolean because 100 is not equal to 10. Another thing you should keep in mind, is that strings are not the same as integers. For instance what do you think will happen if we test the following expression.

```py
100 == '100'
```

The result is yet again **False** because the integer 100 is not equal to a string of letters that say "100". Before getting too in-depth into the inner workings of arithmetic and operators, let's digress and speak once more on variables and data types.

```py
a_number  = 100
a_string  = "Hello"
a_list    = [1,2,3,4]
all_above = [a_number, a_string, a_list]
a_dict    = {"all": all_above, "bool": True}
```

<!-- You'll notice that I spelt the List & Dict variables with capital letters, and this is because -->

There are rules; however, as to how variables are to be named.

- Variable names must start with a letter or the underscore character and cannot start with a number, only containing alpha-numeric characters and underscores.
- Variable names are case-sensitive, so cool, coOL, and COOL are all different variables.

Python reserves the following identifiers or [keywords](https://docs.python.org/3/reference/lexical_analysis.html#keywords) which cannot be used as ordinary identifiers. When thinking up names for your variables, you will have to avoid the following keywords. You'll also want to avoid accidentally overriding [built-in functions](https://docs.python.org/3/library/functions.html), as this can really make things difficult for you.

|||||
|:-:|:-:|:-:|:-:|
|False|await|else|import|
|pass|None|break|except
|in|raise|True|class|
|finally|is|return|and|
|continue|for|lambda|try|
|as|def|from|nonlocal|
|while|assert|del|global|
|not|with|async|elif|
|if|or|yield||

In addition to avoiding the use of keywords as variable names, you will also be expected to write python idiomatically, that is, to conform to a sort of analogous orthopraxy commonly understood by Python programmers. [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/#function-and-variable-names) lists acceptable conventions in which you should name your variables and function names.

> <a href="https://peps.python.org/pep-0008/#function-and-variable-names" style="font-size:21px;">Function and Variable Names</a>
>
Function names should be **lowercase, with words separated by underscores** as necessary to improve readability.
>
Variable names follow the same convention as function names.
>
mixedCase is allowed only in contexts where that’s already the prevailing style (e.g. threading.py), to retain backwards compatibility.


<span style="font-weight:bold;font-size:30px;color:Black;">II. Operators And Precedence</span>

The [Python Language Reference](https://docs.python.org/3/reference/lexical_analysis.html#operators) provides us with the following tokens as operators. Let's organize the operators into categories so we can understand them better.

<!-- ```
+       -       *       **      /       //      %      @
<<      >>      &       |       ^       ~       :=
<       >       <=      >=      ==      !=
``` -->

<!-- |Arithmetic Operators||
|:-:|:-:|
|Addition|`x + y`|
|Subtraction|`x - y`|
|Multiplication|`x * y`|
|Division|`x / y`|
|Division (Floor)|`x // y`|
|Modulus|`x % y`|
|Exponent|`x ** y`| -->

|Arithmetic|Operators|
|:-:|:-:|
|Addition|`a + b`|
|Subtraction|`a - b`|
|Multiplication|`a * b`|
|Division|`a / b`|
|Division (Floor)|`a // b`|
|Modulus|`a % b`|
|Exponent|`a ** b`|
|||
|**Relational or Comparison**|Operators|
|Equality (Equal)|`a == b`|
|Inequality (Not Equal)|`a != b`|
|Greater than|`a > b`|
|Greater than or equal to|`a >= b`|
|Less than|`a < b`|
|Less than or equal to|`a <= b`|
|||
|**Logical**|Operators|
|Logical AND|`a and b`|
|Logical OR|`a or b`|
|Logical NOT|`not(a or b)`<br>`not a and not b`|
|||
|**Identity**|Operators|
|Same object|`a is b`|
|Not the same object|`a is not b`|
|||
|**Membership**|Operators|
|True if sequence a is in b|`a in b`|
|True if sequence a is not in b|`a not in b`|
|||
|**Bitwise**|Operators|
|Bitwise AND|`a & b`|
|Bitwise OR|`a | b`|
|Bitwise XOR|`a ^ b`|
|Bitwise NOT|`a ~ b`|
|Left-shift (Zero-fill)|`a << b`|
|Right-shift (Signed)|`a >> b`|
|||
|**Compound Assignment**|Operators|
|a = a + b|`a += b`|
|a = a - b|`a -= b`|
|a = a * b|`a *= b`|
|a = a / b|`a /= b`|
|a = a % b|`a %= b`|
|a = a // b|`a //= b`|
|a = a ** b|`a **= b`|
|a = a & b|`a &= b`|
|a = a \| b|`a |= b`|
|a = a ^ b|`a ^= b`|
|a = a >> b|`a >>= b`|
|a = a << b|`a <<= b`|

Just like in mathematics when you learned about PEMDAS and the order of operations, Python also has an order of operations, it's just a little bit bigger. You'll find that you wont have to concern yourself with this as much as you might think, but when in doubt, use parentheses.

<!-- you should keep this in mind when errors start popping up in your own coding adventures. -->

|**Precedence**|Order|
|:-:|:-:|
|Parentheses|`()`|
|Exponentation|`**`|
|Unary plus, unary minus, and bitwise NOT|`+x` `-x` `~x`|
|Multiplication, division, floor division, and modulus|`*` `/` `//` `%`|
|Addition and subtraction|`+` `-`|
|Bitwise left and right shifts|`<<` `>>`|
|Bitwise AND|`&`|
|Bitwise XOR|`^`|
|Bitwise OR|`|`|
|Comparisons, identity, and membership operators|`==` `!=` `>` `>=` `<` `<=` `is` `is not` `in` `not in`|
|Logical NOT|`not`|
|Logical AND|`and`|
|Logical OR|`or`|

<!-- for this article we will focus on only the most frequently used for basic tasks. int, list, range, str, dict, and bool. -->

<!-- When you installed the [Python Interpreter](https://www.python.org/downloads/) it came packaged with something called IDLE.
-->

<!-- <span style="font-style:italic;font-size:21px;">Running The Script</span> -->


<!-- ```py
import os

def main():
    print("")

if __name__ == "__main__":
    main()
``` -->

<span style="font-weight:bold;font-size:30px;color:Black;">II. Strings</span>

Strings in Python are written as a sequence of characters embedded between two single or double quotation marks. Many programs seek to gather and process data. Strings are incredibly effective at supplying progammers with a powerful way of easily manipulating many forms of data.

<span style="font-weight:italic;font-size:21px;color:Black;">Concatenation</span>

Strings can be added together, the term for this is called "concatenation." The `+` operator is the main way we concatenate strings, here are some examples.

```py
# Mailbox
"Mail" + "box"
# Moonlight
"Moon" + "light"
# Sunshine
"Sun" + "shine"
# Cream cheese
"Cream" + " cheese"
# Hello World
"Hello" + " " + "World"
# Dishwasher
x = "Dish"
y = "washer"
print(x + y)
```

You might have noticed text beginning with a `#` sign. These are called **comments** and are not executed by the interpreter. In other words, comments help you take notes and keep your code clean and organized. We will be using them throughout the remainder of the walkthrough.

<span style="font-weight:italic;font-size:21px;color:Black;">String Formatting</span>

Strings can be formatted in a number of ways, but the two best ways would be to use the string [format()](https://docs.python.org/3/library/string.html#formatstrings) method, or to use [formatted string literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings) otherwise known as f-strings. The latter of which is the preferred method since the release of Python version 3.6 and up.

```py
replacement_field ::=  "{" [field_name] ["!" conversion] [":" format_spec] "}"
field_name        ::=  arg_name ("." attribute_name | "[" element_index "]")*
arg_name          ::=  [identifier | digit+]
attribute_name    ::=  identifier
element_index     ::=  digit+ | index_string
index_string      ::=  <any source character except "]"> +
conversion        ::=  "r" | "s" | "a"
format_spec       ::=  <described in the next section>
```

The [Format Specification Mini-Language](https://docs.python.org/3/library/string.html#format-specification-mini-language) further expands format_spec.

```go
format_spec     ::=  [[fill]align][sign][z][#][0][width][grouping_option][.precision][type]
fill            ::=  <any character>
align           ::=  "<" | ">" | "=" | "^"
sign            ::=  "+" | "-" | " "
width           ::=  digit+
grouping_option ::=  "_" | ","
precision       ::=  digit+
type            ::=  "b" | "c" | "d" | "e" | "E" | "f" | "F" | "g" | "G" | "n" | "o" | "s" | "x" | "X" | "%"
```

The most common types that will be used most frequently is `f` (Fixed-point notation), `d` (Decimal Integer in base 10), `x` or `X` (Hex format in base 16), and maybe `e` (Scientific notation).

|Option|Meaning|
|:-:|:-:|
|`'f'`|Fixed-point notation. For a given precision p, formats the number as a decimal number with exactly p digits following the decimal point. With no precision given, uses a precision of 6 digits after the decimal point for float, and uses a precision large enough to show all coefficient digits for Decimal. If no digits follow the decimal point, the decimal point is also removed unless the # option is used.|
|`'d'`|Decimal Integer. Outputs the number in base 10.|
|`'x'`|Hex format. Outputs the number in base 16, using lower-case letters for the digits above 9.|
|`'X'`|Hex format. Outputs the number in base 16, using upper-case letters for the digits above 9. In case `'#'` is specified, the prefix `'0x'` will be upper-cased to '0X' as well.|
|`'e'`|Scientific notation. For a given precision p, formats the number in scientific notation with the letter `‘e’` separating the coefficient from the exponent. The coefficient has one digit before and p digits after the decimal point, for a total of p + 1 significant digits. With no precision given, uses a precision of 6 digits after the decimal point for float, and shows all coefficient digits for Decimal. If no digits follow the decimal point, the decimal point is also removed unless the # option is used.|
|`'s'`|String format. This is the default type for strings and may be omitted.|
|`'None'`|Default for integer presentation is `'d'`, for strings `'s'`, for float this is the same as `'g'` which is general format.|

<!-- |Option|Meaning|
|:-:|:-:|
|`'<'`|Forces the field to be left-aligned within the available space (this is the default for most objects).|
|`'>'`|Forces the field to be right-aligned within the available space (this is the default for numbers).|
|`'='`|Forces the padding to be placed after the sign (if any) but before the digits. This is used for printing fields in the form ‘+000000120’. This alignment option is only valid for numeric types. It becomes the default for numbers when ‘0’ immediately precedes the field width.|
|`'^'`|Forces the field to be centered within the available space.| -->

Within the format_spec, which comes after the `:` in the replacement field, we can toy with the precision of any floating point number. In the example below, we've set the precision to 3 digits after the decimal point. The default precision for the fixed-point notation is 6.

```py
golden_ratio = 1.61803398874989484820

# String format() method
"{:.03f}".format(golden_ratio)

# Formatted string literal (f-string)
f"{golden_ratio:.03f}"
```

<span style="font-weight:italic;font-size:21px;color:Black;">Escape Characters</span>

The Python Language Reference's [Lexical Analysis](https://docs.python.org/3/reference/lexical_analysis.html#string-and-bytes-literals) documentation supplies us with a list of escape sequences. There are only a handful that you'll use frequently.

<!-- |||
|:-:|:-:|
|`\<newline>`|Backslash and newline ignored|
|`\\`|Backslash (\)|
|`\'`|Single quote (')|
|`\"`|Double quote (")|
|`\a`|ASCII Bell (BEL)|
|`\b`|ASCII Backspace (BS)|
|`\f`|ASCII Formfeed (FF)|
|`\n`|ASCII Linefeed (LF)|
|`\r`|ASCII Carriage Return (CR)|
|`\t`|ASCII Horizontal Tab (TAB)|
|`\v`|ASCII Vertical Tab (VT)|
|`\ooo`|Character with octal value ooo|
|`\xhh`|Character with hex value hh|
|`\N{name}`|Character named name in the Unicode database|
|`\uxxxx`|Character with 16-bit hex value xxxx|
|`\Uxxxxxxxx`|Character with 32-bit hex value xxxxxxxx| -->

|||
|:-:|:-:|
|`\\`|Backslash (\\)|
|`\'`|Single quote (')|
|`\"`|Double quote (")|
|`\n`|ASCII Linefeed (LF)|
|`\t`|ASCII Horizontal Tab (TAB)|

Some examples might be escaping a single quote in a single quoted string. This prevents the line from breaking and throwing an error. Another example would be a nested quote using the same outer quotes. One way to get around needing to escape the quotes is to mix them, like in the forth and fifth examples.

```py
'That\'s Interesting'
'I\'d\'ve gone.'
"A nested \"quote\""
# Mixing quotation marks
# to avoid the need to escape
"It's great."
'A nested "quote"'
# Newlines are the most
# frequently used
"Run this\nstring in IDLE."
```

<!-- ```py
f"{x}, {y}"
"{}".format(x, y)
"%d %f" % (x, y)
``` -->

<span style="font-weight:italic;font-size:21px;color:Black;">Indexing & Slicing Strings</span>

<!-- https://docs.python.org/3/tutorial/introduction.html#strings -->

Strings can be indexed (subscripted); the first character has an index of 0. There is no separate character type as a single character is just a string of size one. Just like arrays in the C programming language, lists and sequences in Python start with a zeroth index, so if you want to index the second character, you'll need to select position 1 since that comes after the zeroth element.

```py
>>> string = "Hello"

>>> # 'H' is the "Zeroth element," first character
>>> # 'e' is the first element, second character
>>> string[1]
'e'
```

|0|<span style="font-weight:bold;font-size:21px;color:teal;">1</span>|2|3|4|
|:-:|:-:|:-:|:-:|:-:|
|H|<span style="font-weight:bold;font-size:21px;color:teal;">e</span>|l|l|o|

You can also use negative numbers as indices, which begins counting from the right. So an index of `[-1]` would be the last element in the sequence. It should be noted that because -0 is the same as 0, negative indices must start from -1. 

```py
>>> string = "Hello"

>>> # 'H' is the "Zeroth element," first character
>>> # 'e' is the first element, second character
>>> string[-1]
'o'
>>> string[-4]
'e'
```

|-5|<span style="font-weight:bold;font-size:21px;color:teal;">-4</span>|-3|-2|-1|
|:-:|:-:|:-:|:-:|:-:|
|H|<span style="font-weight:bold;font-size:21px;color:teal;">e</span>|l|l|o|

Slicing strings with *slice notation* can provide a convenient way to extract specific characters from strings. The ability to target a *substring* within text will prove to be a useful skill to add to your toolbox. 

```py
# Strings can be sliced
>>> string = "Encouragement"
>>> # string[include:exclude]
>>> string[7:9+1] # or string[7:10]
'gem'
>>> string[2:8+1]
'courage'
>>> # Negative slices are also a thing
>>> string[-6:-4+1]
'gem'
>>> # You can also concatenate
>>> string[7:9+1] + " of " + string[2:8+1]
'gem of courage'
```

|6|<span style="font-weight:bold;font-size:21px;color:teal;">7</span>|<span style="font-weight:bold;font-size:21px;color:teal;">8</span>|<span style="font-weight:bold;font-size:21px;color:teal;">9</span>|10|
|:-:|:-:|:-:|:-:|:-:|
|...a|<span style="font-weight:bold;font-size:21px;color:teal;">g</span>|<span style="font-weight:bold;font-size:21px;color:teal;">e</span>|<span style="font-weight:bold;font-size:21px;color:teal;">m</span>|e...|

A potential gotcha of *slice notation* is that the position specified on the left side of the semicolon is included in the slice, while the position on the right hand side of the semicolon is excluded. If your target *substring* is elements 7, 8, and 9, you'll have to consider that `[7:9]` will leave out the 9th element unless you account for this with `[7:9+1]` or `[7:10]`.

<!-- 
<span style="font-weight:italic;font-size:21px;color:Black;">String Methods</span> -->

<span style="font-weight:bold;color:darkorange;font-size:21px;">Under Construction</span>

**Refresh page for updates in real time.** We will eventually provide links to the courses, but we will need time to prepare the full curriculum. Please be patient and bare with us while we methodically create a friendly end user experience. A free introduction will appear here in this article so bookmark and check back every couple days for updates. We will also present the courses on our [twitter page](https://twitter.com/SevenShepherd).

Sincerely,

~ [SevenShepherd](https://twitter.com/SevenShepherd)

<!-- <span style="font-weight:bold;font-size:30px;color:Black;">I. Work Smarter Not Harder</span>

In my youth I often asked myself &mdash; whilst in deep reflection &mdash; *"... are my options really only between poverty or slavery?"* Not knowing the answers I meditated on the perplexing question for years until simple truths hit me. During the process of dire contemplation I became monastic (secluded and contemplative) in my Christianity.

> <sup style="font-weight:bold;">15</sup> The labour of the foolish wearieth every one of them, because he knoweth not how to go to the city. &mdash; Ecclesiastes 10:15 KJV

I stumbled upon a verse, that when correctly rendered, essentially said that I was foolish because I did not understand how to do business in the city, and that this was the cause of, not only mine, but all of our hardships financially. -->


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