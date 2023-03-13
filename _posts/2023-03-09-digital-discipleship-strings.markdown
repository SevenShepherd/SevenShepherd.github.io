---
layout: post
title: "🧶 Fundamentals Of Digital Discipleship, Part VII: Strings"
date: 2023-03-09 03:20:20 -0500
categories: digital computer programming python ministry
published: true
---

<!-- <span style="font-style:Italic;font-size:32px;">Chapter Header</span>

<span style="font-style:Italic;font-size:24px;">Sub Chapter Header</span> -->

<a href="https://docs.python.org/3/library/stdtypes.html#textseq" style="font-weight:italic;font-size:2em;">Strings</a>

Strings in Python are written as a sequence of characters embedded between two single or double quotation marks. Many programs seek to gather and process data. Strings are incredibly effective at supplying programmers with a powerful way of easily manipulating many forms of data.

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
|`'f'`|Fixed-point notation. For a given precision p, formats the number as a decimal number with exactly p digits following the decimal point. With no precision given, uses a precision of 6 digits after the decimal point.|
|`'d'`|Decimal Integer. Outputs the number in base 10.|
|`'c'`|Character. Converts the integer to the corresponding unicode character before printing.|
|`'x'`|Hex format. Outputs the number in base 16, using lower-case letters for the digits above 9.|
|`'X'`|Hex format. Outputs the number in base 16, using upper-case letters for the digits above 9. In case `'#'` is specified, the prefix `'0x'` will be upper-cased to '0X' as well.|
|`'b'`|Binary format. Outputs the number in base 2.|
|`'e'`|Scientific notation. For a given precision p, formats the number in scientific notation with the letter `‘e’` separating the coefficient from the exponent.|
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

|Method|Description|
|:-:|:-:|
|[`capitalize()`](https://docs.python.org/3/library/stdtypes.html#str.capitalize)|Returns a copy of the string with its first character capitalized and the rest lowercased.|
|[`title()`](https://docs.python.org/3/library/stdtypes.html#str.title)|Returns a title cased version of the string where words start with an uppercase character and the remaining characters are lowercase.|
|[`lower()`](https://docs.python.org/3/library/stdtypes.html#str.lower)|Returns a copy of the string converted to lowercase.|
|[`upper()`](https://docs.python.org/3/library/stdtypes.html#str.upper)|Returns a copy of the string converted to uppercase.|
|[`swapcase()`](https://docs.python.org/3/library/stdtypes.html#str.swapcase)|Returns a copy of the string with uppercase characters converted to lowercase and vice versa.|

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

|Method|Description|
|:-:|:-:|
|[`isalpha()`](https://docs.python.org/3/library/stdtypes.html#str.isalpha)|Return True if all characters in the string are alphabetic and there is at least one character, False otherwise.|
|[`isdecimal()`](https://docs.python.org/3/library/stdtypes.html#str.isdecimal)|Return True if all characters in the string are decimal characters and there is at least one character, False otherwise.|
|[`islower()`](https://docs.python.org/3/library/stdtypes.html#str.islower)|Return True if all cased characters in the string are lowercase and there is at least one cased character, False otherwise.|
|[`isspace()`](https://docs.python.org/3/library/stdtypes.html#str.isspace)|Return True if there are only whitespace characters in the string and there is at least one character, False otherwise.|
|[`isupper()`](https://docs.python.org/3/library/stdtypes.html#str.isupper)|Return True if all cased characters in the string are uppercase and there is at least one cased character, False otherwise.|

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

|Method|Description|
|:-:|:-:|
|[`startswith()`](https://docs.python.org/3/library/stdtypes.html#str.startswith)|Return True if string starts with the prefix, otherwise return False.|
|[`endswith()`](https://docs.python.org/3/library/stdtypes.html#str.endswith)|Return True if the string ends with the specified suffix, otherwise return False.|
|[`index()`](https://docs.python.org/3/library/stdtypes.html#str.index)|Return the lowest index in the string where substring sub is found within the slice s[start:end]. Optional arguments start and end are interpreted as in slice notation. Like `find()`, but instead of returning -1 if sub is not found it raises ValueError instead.|

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

|Method|Description|
|:-:|:-:| 
|[`center()`](https://docs.python.org/3/library/stdtypes.html#str.center)|Return centered in a string of length width. Padding is done using the specified fillchar (default is an ASCII space).|
|[`ljust()`](https://docs.python.org/3/library/stdtypes.html#str.ljust)|Return the string left justified in a string of length width. Padding is done using the specified fillchar (default is an ASCII space).|
|[`rjust()`](https://docs.python.org/3/library/stdtypes.html#str.rjust)|Return the string right justified in a string of length width. Padding is done using the specified fillchar (default is an ASCII space).|

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

|Method|Description|
|:-:|:-:|
|[`strip()`](https://docs.python.org/3/library/stdtypes.html#str.strip)|Return a copy of the string with the leading and trailing characters removed. The chars argument is a string specifying the set of characters to be removed. If omitted or None, the chars argument defaults to removing whitespace.|
|[`lstrip()`](https://docs.python.org/3/library/stdtypes.html#str.lstrip)|Return a copy of the string with leading characters removed. The chars argument is a string specifying the set of characters to be removed. If omitted or None, the chars argument defaults to removing whitespace.|
|[`rstrip()`](https://docs.python.org/3/library/stdtypes.html#str.rstrip)|Return a copy of the string with trailing characters removed. The chars argument is a string specifying the set of characters to be removed. If omitted or None, the chars argument defaults to removing whitespace.|

```py
knight = '♘♘♘Knight♘♘♘'
knight.rstrip('♘')
'♘♘♘Knight'

knight.lstrip('♘')
'Knight♘♘♘'

knight.strip('♘')
'Knight'
```

|Method|Description|
|:-:|:-:|
|[`removeprefix()`](https://docs.python.org/3/library/stdtypes.html#str.removeprefix)|If the string starts with the prefix string, return string[len(prefix):]. Otherwise, return a copy of the original string|
|[`removesuffix()`](https://docs.python.org/3/library/stdtypes.html#str.removesuffix)|If the string ends with the suffix string and that suffix is not empty, return string[:-len(suffix)]. Otherwise, return a copy of the original string|
|[`replace()`](https://docs.python.org/3/library/stdtypes.html#str.replace)|Return a copy of the string with all occurrences of substring old replaced by new. If the optional argument count is given, only the first count occurrences are replaced.|

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

|Method|Description|
|:-:|:-:|
|[`join()`](https://docs.python.org/3/library/stdtypes.html#str.join)|Return a string which is the concatenation of the strings in iterable. A TypeError will be raised if there are any non-string values in iterable, including bytes objects. The separator between elements is the string providing this method.|
|[`split()`](https://docs.python.org/3/library/stdtypes.html#str.split)|Return a list of the words in the string, using sep as the delimiter string. If maxsplit is given, at most maxsplit splits are done (thus, the list will have at most maxsplit+1 elements). If maxsplit is not specified or -1, then there is no limit on the number of splits (all possible splits are made).|
|[`partition()`](https://docs.python.org/3/library/stdtypes.html#str.partition)|Split the string at the first occurrence of sep, and return a 3-tuple containing the part before the separator, the separator itself, and the part after the separator. If the separator is not found, return a 3-tuple containing the string itself, followed by two empty strings.|

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

|Method|Description|
|:-:|:-:|
|[`maketrans()`](https://docs.python.org/3/library/stdtypes.html#str.maketrans)|This static method returns a translation table usable for str.translate().|
|[`translate()`](https://docs.python.org/3/library/stdtypes.html#str.translate)|Return a copy of the string in which each character has been mapped through the given translation table.|

For more on fun [Classical Cryptography](http://bit.ly/3kZ2D8V) puzzles, check out our exercise.

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