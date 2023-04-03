---
layout: post
title: "👨‍💻 Introduction To Computer Programming"
date: 2023-02-21 04:30:00 -0500
categories: digital computer programming python ministry
published: false
---

<span style="font-style:Italic;font-size:21px;color:Black;">Hello and welcome,</span>

<!-- I know you've waited a long time *unknown* blessed *unknown* *unknown* -->

<!-- 💻👨‍💻 Computer Programming Courses And Digital Discipleship -->

<!-- 💻🐱‍💻👨‍💻 For Ministry Automation-->

My name is Ryan and my philosophy is known as autodidacticism. I have been a programmer since the turn of the millennium. In the past, I successfully taught myself how to program in C/C++, grew advanced with Perl, but ultimately my formal language of choice became Python, and as a result, the predominant paradigm you’ll see me implement in this blog is of the imperative rather than declarative variety.

> <sup style="font-weight:bold;">16</sup> Let your light so shine before men, that they may see your good works, and glorify your Father which is in heaven. &mdash; Matthew 5:16 KJV

In 2016 I created a custom programmed and automated Twitter based Christian ministry at [@SevenShepherd](https://twitter.com/SevenShepherd) that has been running successfully ever since, from a custom built raspberry pi single-board computer. From 2016 to January 2023, this ministry has posted over 2,639,234 tweets, and received more than 7,597,960 likes & retweets. This is approximately [100 lifetimes](https://www.biblegateway.com/passage/?search=Matthew+13%3A1-23%3B+Luke+8%3A4-15%3B+Mark+4%3A2-20&version=NLT) of preaching the gospel message within a 7 year period.

<!-- From 2016 to the January 2023, this ministry has posted over 2.7 million tweets, and received more than 7.6 million likes & retweets. This is approximately 100 lifetimes of preaching the gospel message within a 7 year period. -->

> <sup style="font-weight:bold;">19</sup> Go therefore and make disciples of all nations, baptizing them in<span style="color:#A7A7A7;">[a]</span> the name of the Father and of the Son and of the Holy Spirit, <sup style="font-weight:bold;">20</sup> teaching them to observe all that I have commanded you. And behold, I am with you always, to the end of the age.” &mdash; Matthew 28:19-20 ESV

God has put it on my heart and mind to teach the computer programming experience He has given me to others in hopes that they would be able to spread the gospel message more efficiently, and in doing so, curb the tides of darkness which is at our very doorstep, threatening the very fabric of our society.

<span style="font-weight:italic;font-size:32px;color:Black;">Content Overview</span>

After much deliberation, all articles pertaining to the Bible will remain free and accessible to everyone at anytime [through our blog](https://bit.ly/3G0CTAO). Instead the way I've decided to support and grow this ministry is by offering courses on computer programming and ministry automation.

> <sup style="font-weight:bold;">16</sup> “·Listen <span style="color:#A7A7A7;">[<sup>L</sup> Look; <sup>T</sup> Behold]</span>, I am sending you out like sheep among wolves. So be as ·clever <span style="color:#A7A7A7;">[wise; shrewd; cunning]</span> as ·snakes <span style="color:#A7A7A7;">[serpents]</span> and as ·innocent <span style="color:#A7A7A7;">[harmless]</span> as doves. &mdash; Matthew 10:16 <a href="https://amzn.to/3vlMXy5" style="color:MediumPurple;">Expanded Bible (EXB)</a>

I have decided to use the Python programming language to teach fundamental programming concepts. This is a language suitable for the beginner, as well as the most advanced computer programmers. Python is used by organizations such as: Google, CERN, NASA, Facebook, Amazon, Instagram, Spotify, Reddit, and Wikipedia.

<!-- Some of the more advanced topics and skills that will eventually be covered are as follows: data analysis, botting and automation, machine learning and chatbots, deep learning and neural networks, web programming and blog development, and software development and GUI programming. With the initial emphasis on fundamentals and ministry automation. -->

<span style="font-weight:italic;font-size:32px;color:Black;">A Basic Introduction To Computer Programming</span>

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

<span style="font-weight:italic;font-size:32px;color:Black;">I. Understanding Data Types And Variables</span>

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
- Variable names are case-sensitive, so lord, Lord, LoRd, and LORD are all different variables.

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


<span style="font-weight:italic;font-size:32px;color:Black;">II. Operators And Precedence</span>

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

<span style="font-weight:italic;font-size:32px;color:Black;">II. Strings</span>

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
string = "Hello"

# 'H' is the "Zeroth element," first character
# 'e' is the first element, second character
string[1]
'e'
```

|0|<span style="font-weight:bold;font-size:21px;color:teal;">1</span>|2|3|4|
|:-:|:-:|:-:|:-:|:-:|
|H|<span style="font-weight:bold;font-size:21px;color:teal;">e</span>|l|l|o|

You can also use negative numbers as indices, which begins counting from the right. So an index of `[-1]` would be the last element in the sequence. It should be noted that because -0 is the same as 0, negative indices must start from -1. 

```py
string = "Hello"

# 'H' is the "Zeroth element," first character
# 'e' is the first element, second character
string[-1]
'o'
string[-4]
'e'
```

|-5|<span style="font-weight:bold;font-size:21px;color:teal;">-4</span>|-3|-2|-1|
|:-:|:-:|:-:|:-:|:-:|
|H|<span style="font-weight:bold;font-size:21px;color:teal;">e</span>|l|l|o|

Slicing strings with *slice notation* can provide a convenient way to extract specific characters from strings. The ability to target a *substring* within text will prove to be a useful skill to add to your toolbox. 

```py
# Strings can be sliced
string = "Encouragement"

# string[include:exclude]
string[7:9+1] # or string[7:10]
'gem'

string[2:8+1]
'courage'

# Negative slices are also a thing
string[-6:-4+1]
'gem'

# You can also concatenate
string[7:9+1] + " of " + string[2:8+1]
'gem of courage'
```

|6|<span style="font-weight:bold;font-size:21px;color:teal;">7</span>|<span style="font-weight:bold;font-size:21px;color:teal;">8</span>|<span style="font-weight:bold;font-size:21px;color:teal;">9</span>|10|
|:-:|:-:|:-:|:-:|:-:|
|...a|<span style="font-weight:bold;font-size:21px;color:teal;">g</span>|<span style="font-weight:bold;font-size:21px;color:teal;">e</span>|<span style="font-weight:bold;font-size:21px;color:teal;">m</span>|e...|

A potential gotcha of *slice notation* is that the position specified on the left side of the semicolon is included in the slice, while the position on the right hand side of the semicolon is excluded. If your target *substring* is elements 7, 8, and 9, you'll have to consider that `[7:9]` will leave out the 9th element unless you account for this with `[7:9+1]` or `[7:10]`.

<span style="font-weight:italic;font-size:21px;color:Black;">String Methods</span>

Previously you were introduced to the `format()` string method and alternative formatted string literals (f-strings). Let's look at the other extraordinarily useful [string methods](https://docs.python.org/3/library/stdtypes.html#string-methods) available to us.

<!-- |Description|Method|
|:-:|:-:|
||[`capitalize()`](https://docs.python.org/3/library/stdtypes.html#str.capitalize)|
||`casefold()`|
||`center()`|
||`count()`|
||`encode()`|
||`endswith()`|
||`expandtabs()`|
||`find()`|
||`format()`|
||`format_map()`|
||`index()`|
||`isalnum()`|
||`isalpha()`|
||`isascii()`|
||`isdecimal()`|
||`isdigit()`|
||`isidentifier()`|
||`islower()`|
||`isnumeric()`|
||`isprintable()`|
||`isspace()`|
||`istitle()`|
||`isupper()`|
||`join()`|
||`ljust()`|
||`lower()`|
||`lstrip()`|
||`maketrans()`|
||`partition()`|
||`removeprefix()`|
||`removesuffix()`|
||`replace()`|
||`rfind()`|
||`rindex()`|
||`rjust()`|
||`rpartition()`|
||`rsplit()`|
||`rstrip()`|
||`split()`|
||`splitlines()`|
||`startswith()`|
||`strip()`|
||`swapcase()`|
||`title()`|
||`translate()`|
||`upper()`| -->

|Description|Method|
|:-:|:-:|
|Returns a copy of the string with its first character capitalized and the rest lowercased.|[`capitalize()`](https://docs.python.org/3/library/stdtypes.html#str.capitalize)|
|Returns a titlecased version of the string where words start with an uppercase character and the remaining characters are lowercase.|[`title()`](https://docs.python.org/3/library/stdtypes.html#str.title)|
|Returns a copy of the string converted to lowercase.|[`lower()`](https://docs.python.org/3/library/stdtypes.html#str.lower)|
|Returns a copy of the string converted to uppercase.|[`upper()`](https://docs.python.org/3/library/stdtypes.html#str.upper)|
|Returns a copy of the string with uppercase characters converted to lowercase and vice versa.|[`swapcase()`](https://docs.python.org/3/library/stdtypes.html#str.swapcase)|

```py
"solomon".capitalize()
'Solomon'

"digital discipleship".title()
'Digital Discipleship'

"exit".upper()
'EXIT'

"QUIETLY".lower()
'quietly'
```

The next set of string methods are normally used in conjunction with control flow statements like the `if` statement, but since we haven't reached that part of this tutorial I'll list them out with some basic examples.

<!-- |Description|Method|
|:-:|:-:|
|Returns True if all characters in the string are alphanumeric and there is at least one character, False otherwise. A character c is alphanumeric if one of the following returns True: c.isalpha(), c.isdecimal(), c.isdigit(), or c.isnumeric().|[`isalnum()`](https://docs.python.org/3/library/stdtypes.html#str.isalnum)|
|Return True if all characters in the string are alphabetic and there is at least one character, False otherwise.|[`isalpha()`](https://docs.python.org/3/library/stdtypes.html#str.isalpha)|
|Return True if the string is empty or all characters in the string are ASCII, False otherwise. ASCII characters have code points in the range U+0000-U+007F.|[`isascii()`](https://docs.python.org/3/library/stdtypes.html#str.isascii)|
|Return True if all characters in the string are decimal characters and there is at least one character, False otherwise.|[`isdecimal()`](https://docs.python.org/3/library/stdtypes.html#str.isdecimal)|
|Return True if all characters in the string are digits and there is at least one character, False otherwise. Formally, a digit is a character that has the property value Numeric_Type=Digit or Numeric_Type=Decimal.|[`isdigit()`](https://docs.python.org/3/library/stdtypes.html#str.isdigit)|
|Return True if the string is a valid identifier according to the language definition. Call keyword.iskeyword() to test whether string s is a **reserved** identifier, such as def and class.|[`isidentifier()`](https://docs.python.org/3/library/stdtypes.html#str.isidentifier)|
|Return True if all cased characters 4 in the string are lowercase and there is at least one cased character, False otherwise.|[`islower()`](https://docs.python.org/3/library/stdtypes.html#str.islower)|
|Return True if all characters in the string are numeric characters, and there is at least one character, False otherwise. Formally, numeric characters are those with the property value of digit, decimal, or numeric.|[`isnumeric()`](https://docs.python.org/3/library/stdtypes.html#str.isnumeric)|
|Return True if all characters in the string are printable or the string is empty, False otherwise.|[`isprintable()`](https://docs.python.org/3/library/stdtypes.html#str.isprintable)|
|Return True if there are only whitespace characters in the string and there is at least one character, False otherwise.|[`isspace()`](https://docs.python.org/3/library/stdtypes.html#str.isspace)|
|Return True if the string is a titlecased string and there is at least one character, for example uppercase characters may only follow uncased characters and lowercase characters only cased ones. Return False otherwise.|[`istitle()`](https://docs.python.org/3/library/stdtypes.html#str.istitle)|
|Return True if all cased characters 4 in the string are uppercase and there is at least one cased character, False otherwise.|[`isupper()`](https://docs.python.org/3/library/stdtypes.html#str.isupper)| -->

|Description|Method|
|:-:|:-:|
|Return True if all characters in the string are alphabetic and there is at least one character, False otherwise.|[`isalpha()`](https://docs.python.org/3/library/stdtypes.html#str.isalpha)|
|Return True if all characters in the string are decimal characters and there is at least one character, False otherwise.|[`isdecimal()`](https://docs.python.org/3/library/stdtypes.html#str.isdecimal)|
|Return True if all cased characters in the string are lowercase and there is at least one cased character, False otherwise.|[`islower()`](https://docs.python.org/3/library/stdtypes.html#str.islower)|
|Return True if there are only whitespace characters in the string and there is at least one character, False otherwise.|[`isspace()`](https://docs.python.org/3/library/stdtypes.html#str.isspace)|
|Return True if all cased characters in the string are uppercase and there is at least one cased character, False otherwise.|[`isupper()`](https://docs.python.org/3/library/stdtypes.html#str.isupper)|

```py
"abcdefg".isalpha()
True
"abc123".isalpha()
False
"1234567".isdecimal()
True
"123AllEyesOnMe".isdecimal()
False
```

|Description|Method|
|:-:|:-:|
|Return True if string starts with the prefix, otherwise return False. prefix can also be a tuple of prefixes to look for. With optional start, test string beginning at that position. With optional end, stop comparing string at that position.|[`startswith()`](https://docs.python.org/3/library/stdtypes.html#str.startswith)|
|Return True if the string ends with the specified suffix, otherwise return False. suffix can also be a tuple of suffixes to look for. With optional start, test beginning at that position. With optional end, stop comparing at that position.|[`endswith()`](https://docs.python.org/3/library/stdtypes.html#str.endswith)|
|Return the lowest index in the string where substring sub is found within the slice s[start:end]. Optional arguments start and end are interpreted as in slice notation. Like `find()`, but instead of returning -1 if sub is not found it raises ValueError instead.|[`index()`](https://docs.python.org/3/library/stdtypes.html#str.index)|

```py
psalm23_1 = "The LORD is my shepherd, I lack nothing."
psalm23_1.startswith("The LORD")
True

psalm23_1.startswith(("LORD", "The"))
True

psalm23_1.endswith("I lack nothing.")
True

start = psalm23_1.index("LORD")
end   = start + len("LORD")
start, end
(4, 8)

psalm23_1[start:end]
'LORD'
```

|Description|Method|
|:-:|:-:| 
|Return centered in a string of length width. Padding is done using the specified fillchar (default is an ASCII space). The original string is returned if width is less than or equal to len(s).|[`center()`](https://docs.python.org/3/library/stdtypes.html#str.center)|
|Return the string left justified in a string of length width. Padding is done using the specified fillchar (default is an ASCII space). The original string is returned if width is less than or equal to len(s).|[`ljust()`](https://docs.python.org/3/library/stdtypes.html#str.ljust)|
|Return the string right justified in a string of length width. Padding is done using the specified fillchar (default is an ASCII space). The original string is returned if width is less than or equal to len(s).|[`rjust()`](https://docs.python.org/3/library/stdtypes.html#str.rjust)|

```py
# Same as: f"{'Knight':♘^12}"
"Knight".center(12,'♘')
'♘♘♘Knight♘♘♘'

# Same as: f"{'Knight':♘<12}"
"Knight".ljust(12,'♘')
'Knight♘♘♘♘♘♘'

# Same as: f"{'Knight':♘>12}"
"Knight".rjust(12,'♘')
'♘♘♘♘♘♘Knight'
```

|Description|Method|
|:-:|:-:|
|Return a copy of the string with the leading and trailing characters removed. The chars argument is a string specifying the set of characters to be removed. If omitted or None, the chars argument defaults to removing whitespace. The chars argument is not a prefix or suffix; rather, all combinations of its values are stripped|[`strip()`](https://docs.python.org/3/library/stdtypes.html#str.strip)|
|Return a copy of the string with leading characters removed. The chars argument is a string specifying the set of characters to be removed. If omitted or None, the chars argument defaults to removing whitespace. The chars argument is not a prefix; rather, all combinations of its values are stripped:|[`lstrip()`](https://docs.python.org/3/library/stdtypes.html#str.lstrip)|
|Return a copy of the string with trailing characters removed. The chars argument is a string specifying the set of characters to be removed. If omitted or None, the chars argument defaults to removing whitespace. The chars argument is not a suffix; rather, all combinations of its values are stripped|[`rstrip()`](https://docs.python.org/3/library/stdtypes.html#str.rstrip)|

```py
knight = '♘♘♘Knight♘♘♘'
knight.rstrip('♘')
'♘♘♘Knight'

knight.lstrip('♘')
'Knight♘♘♘'

knight.strip('♘')
'Knight'
```

|Description|Method|
|:-:|:-:|
|If the string starts with the prefix string, return string[len(prefix):]. Otherwise, return a copy of the original string|[`removeprefix()`](https://docs.python.org/3/library/stdtypes.html#str.removeprefix)|
|If the string ends with the suffix string and that suffix is not empty, return string[:-len(suffix)]. Otherwise, return a copy of the original string|[`removesuffix()`](https://docs.python.org/3/library/stdtypes.html#str.removesuffix)|
|Return a copy of the string with all occurrences of substring old replaced by new. If the optional argument count is given, only the first count occurrences are replaced.|[`replace()`](https://docs.python.org/3/library/stdtypes.html#str.replace)|

```py
knight = '♘♘♘Knight♘♘♘'
knight.removeprefix('♘')
'♘♘Knight♘♘♘'

"Mr. Doctor".removeprefix("Mr.")
' Doctor'

"Mr. Doctor".removeprefix("Mr.").lstrip()
'Doctor'

king = knight.replace('♘', '♔')
king = king.replace('Knight', 'King')
king
'♔♔♔King♔♔♔'
```

|Description|Method|
|:-:|:-:|
|Return a string which is the concatenation of the strings in iterable. A TypeError will be raised if there are any non-string values in iterable, including bytes objects. The separator between elements is the string providing this method.|[`join()`](https://docs.python.org/3/library/stdtypes.html#str.join)|
|Return a list of the words in the string, using sep as the delimiter string. If maxsplit is given, at most maxsplit splits are done (thus, the list will have at most maxsplit+1 elements). If maxsplit is not specified or -1, then there is no limit on the number of splits (all possible splits are made).|[`split()`](https://docs.python.org/3/library/stdtypes.html#str.split)|
|Split the string at the first occurrence of sep, and return a 3-tuple containing the part before the separator, the separator itself, and the part after the separator. If the separator is not found, return a 3-tuple containing the string itself, followed by two empty strings.|[`partition()`](https://docs.python.org/3/library/stdtypes.html#str.partition)|

```py
veritas = "Quid est veritas?".split()
veritas
['Quid', 'est', 'veritas?']

" ".join(['Quid', 'est', 'veritas?'])
'Quid est veritas?'

" ".join(veritas)
'Quid est veritas?'

"Hello, World!".partition(", ")
('Hello', ', ', 'World!')
```

|Description|Method|
|:-:|:-:|
|This static method returns a translation table usable for str.translate().|[`maketrans()`](https://docs.python.org/3/library/stdtypes.html#str.maketrans)|
|Return a copy of the string in which each character has been mapped through the given translation table.|[`translate()`](https://docs.python.org/3/library/stdtypes.html#str.translate)|

```py
# ROT-13 Encryption
msg   = "Hello"
trans = str.maketrans(
    "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ", 
    "nopqrstuvwxyzabcdefghijklmNOPQRSTUVWXYZABCDEFGHIJKLM"
)

# Encrypted message
msg.translate(trans)
'Uryyb'
```

<span style="font-weight:italic;font-size:32px;color:Black;">Lists</span>

A [list](https://docs.python.org/3/library/stdtypes.html#lists) is an ordered mutable sequence of values enclosed in square brackets, and one of the four collection data types in the Python programming language, including tuples, sets, and dictionaries. Most sequence types share the [Common Sequence Operations](https://docs.python.org/3/library/stdtypes.html#common-sequence-operations).

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

```py
list_of_strings = ["forward", "backward", "left", "right"]
list_random     = ["up", "down", 6, 7.8, True]

"up" in list_of_strings
False

"up" not in list_of_strings
True

"up" in list_random
True

"up" not in list_random
False

list_of_strings + list_random
['forward', 'backward', 'left', 'right', 'up', 'down', 6, 7.8, True]

list_random*2
['up', 'down', 6, 7.8, True, 'up', 'down', 6, 7.8, True]

list_random[3]
7.8

# Same as ...[0:5+1]
(list_of_strings + list_random)[:5+1]
['forward', 'backward', 'left', 'right', 'up', 'down']

l = list_of_strings + list_random
l[:5+1:2]
['forward', 'left', 'up']

len(l)
9

min(l[:5+1])
'backward'

max(l[:5+1])
'up'

min([1,2,3,4,5,6,7])
1

max([1,2,3,4,5,6,7])
7

l.index('up')
4

l.count(7.8)
1
```

Lists implement all of the common and [mutable Sequence operations](https://docs.python.org/3/library/stdtypes.html#mutable-sequence-types). Lists also provide the additional [`sort()`](https://docs.python.org/3/library/stdtypes.html#list.sort) method.

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

x = [1, 2, 3]
x.reverse()
x
[3, 2, 1]

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

y = [4,1,3,9,7,8,3,7,]
y.sort()
y
[1, 3, 3, 4, 7, 7, 8, 9]
```

<span style="font-weight:italic;font-size:32px;color:Black;">Dictionaries</span>

[Dictionaries](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict) provide the only standard mapping type avaliable to Python. A mapping objects are mutable and they map hashable values to arbitrary objects.

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

```py

# Either will achieve the same result
d = dict(key = "value")
d = {"key":"value"}

# Either will do, the first returns None
# if the key is not found. The second
# throws a KeyError that can be caught
d.get("key")
d["key"]

# Output
"value"

d = dict(key = "value")
"value"
```

```py
d = {
    "key1": 1,
    "key2": 2,
    "key3": 3,
    "key4": 4,
    "key5": 5,
    "key6": 6,
    "key7": 7
}
d
{'key1': 1, 'key2': 2, 'key3': 3, 'key4': 4, 'key5': 5, 'key6': 6, 'key7': 7}
```

<span style="font-weight:italic;font-size:32px;color:Black;">Compound Statements & Control Flow</span>

[Compound statements](https://docs.python.org/3/reference/compound_stmts.html) contain groups of other statements and consist of one or more ‘clauses’ which span multiple lines. The clauses control and manipulate the other statements.

<a href="https://docs.python.org/3/reference/compound_stmts.html#the-if-statement" style="font-weight:italic;font-size:21px;">The If Statement</a>

The if statement is used for conditional execution. It selects exactly one of the suites by evaluating the expressions one by one until one is found to be true then that suite is executed. If all expressions are false, the suite of the else clause, if present, is executed.

```py
if condition_is_true:
    print("print this message")

if False:
    print("The If clause will never be executed")
else:
    print("The else clause was executed")

if True:
    print("The If clause was executed")
else:
    print("The else clause will never be executed")

if False:
    print("The If clause will NEVER executed")
elif True:
    print("The elif clause IS executed")
else:
    print("The else clause will NEVER be executed")

if True:
    print("The If clause IS executed")
elif True:
    print("The elif clause is NEVER reached")
else:
    print("The else clause will NEVER be executed")

if 1 + 1 == 2:
    print("One plus one is two!")

list_of_ints = [1,3,5,7,9]

if 2 in list_of_ints:
    print("Two was found in the list!")
elif 4 in list_of_ints:
    print("Two was found in the list!")
else:
    print("Neither 2 or 4 was found in the List!")
```

<a href="https://docs.python.org/3/reference/compound_stmts.html#the-match-statement" style="font-weight:italic;font-size:21px;">The Match Statement</a>

While you can use as many elif clauses as you like, once you go beyond needing the if, elif, and else, and onto using many elifs, you may want to utilize the match statement. This compound statement is reminiscent of the switch statement in the C programming language, and is new in version 3.10 of the Python programming language.

```py
subject_expr = "hello"

# This will execute the case sensitive code block
match subject_expr:
    case "Hello":
        print("case insensitive")
    case "hello":
        print("case sensitive")
    case _:
        print("matches everything")
```

It used to be fun to create your own switch or match statement since Python was devoid of one, but luckily they brought match to Python.

```py
def switch(opt):
    return {
        "key": "value",
        "k2" : "etc."
    }.get(opt)

switch("k2")
'etc.'
```

<a href="https://docs.python.org/3/reference/compound_stmts.html#the-while-statement" style="font-weight:italic;font-size:21px;">The While Statement</a>

The while statement is used for repeated execution as long as an expression is true. The [break](https://docs.python.org/3/reference/simple_stmts.html#break) and [continue](https://docs.python.org/3/reference/simple_stmts.html#continue) keywords come in handy for granular control over the loop. While can also be used with the [walrus operator](https://docs.python.org/3/reference/expressions.html#assignment-expressions) which is new to Python version 3.8.

```py
# Infinite loop
while True:
    print("press ctrl+c to stop")

# Infinite loop w/ count
count = 0
while count := count + 1:
    print(f"[{count}] press ctrl+c to stop")

# Infinite loop w/ break at 10
count = 0
while count := count + 1:
    print(f"[{count}] press ctrl+c to stop")
    if count > 9:
        break

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
```

<a href="https://docs.python.org/3/reference/compound_stmts.html#the-for-statement" style="font-weight:italic;font-size:21px;">The For Statement</a>

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
```

<a href="https://docs.python.org/3/reference/compound_stmts.html#the-try-statement" style="font-weight:italic;font-size:21px;">The Try Statement</a>

Exception handling is much more easy in Python than it is in many older languages. The try and except keywords make catching errors a breeze. We can simulate an error with the [raise](https://docs.python.org/3/reference/simple_stmts.html#the-raise-statement) statement. We can also use the simpler [assert](https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement) statement.

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

<!-- <span style="font-weight:italic;font-size:21px;color:Black;">The With Statement</span> -->

<span style="font-weight:bold;color:darkorange;font-size:21px;">Under Construction</span>

**Refresh page for updates in real time.** We will eventually provide links to the courses, but we will need time to prepare the full curriculum. Please be patient and bare with us while we methodically create a friendly end user experience. A free introduction will appear here in this article so bookmark and check back every couple days for updates. We will also present the courses on our [twitter page](https://twitter.com/SevenShepherd).

Sincerely,

~ [SevenShepherd](https://twitter.com/SevenShepherd)

<!-- <span style="font-weight:italic;font-size:32px;color:Black;">I. Work Smarter Not Harder</span>

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