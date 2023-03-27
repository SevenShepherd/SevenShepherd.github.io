---
layout: post
title: "💾 Fundamentals Of Digital Discipleship, Part XVII: File Handling & The With Statement"
date: 2023-03-10 02:45:00 -0500
categories: digital computer programming python ministry
published: true
---

<a href="https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files" style="font-weight:italic;font-size:2em;">File Handling</a>

The Python programming language has provided the [open()](https://docs.python.org/3/library/functions.html#open) built-in function to create [file objects](https://docs.python.org/3/glossary.html#term-file-object) which mediate access to real on-disk files or to other types of storage or communication devices. <!-- (i.e. standard I/O, in-memory buffers, sockets, pipes, etc.).--> Raw binary files, buffered binary files, and text files make up the three different kinds of file objects.

<span style="font-size:1.4em;">The Open Function</span>

```py
open(file, mode='r', buffering=- 1, encoding=None, errors=None, newline=None, closefd=True, opener=None)
```

We can take a closer look at the first two parameters used to define the open function within Python. The open function will return a file object and throw / raise an OSError exception if the file cannot be opened. 

- The **file** parameter is a path-like object given a pathname (absolute or relative to the current working directory) of the file to be opened.
- The **mode** is an optional string that specifies the mode in which the file is opened. It defaults to 'r' (a synonym of 'rt') which means open for reading in text mode. Files opened in binary mode return contents as bytes objects without any decoding and files opened in text mode are returned as str.

|Modes|Meaning|
|:-:|:-|
|`'r'`|open for reading (default)|
|`'w'`|open for writing, **truncating** the file first|
|`'x'`|open for exclusive creation, failing if the file already exists|
|`'a'`|open for writing, appending to the end of file if it exists|
|`'b'`|binary mode|
|`'t'`|text mode (default)|
|`'+'`|open for updating (reading and writing)|

<span style="font-size:1.4em;">Creating File Objects And Reading From A File</span>

We can create a file handle to a file object using the open built-in. Let's create a file called read.txt and write the word *"Success!"* within the text file and see if we can use Python to read what we have written. Once we have created the file object we will have access to the `read(size)` method. Size is an optional numeric argument and if omitted or negative, the entire contents of the file is read and returned.

```py
# all three statements are identical
# 'r' or 'open for reading' is default
# 't' or 'text mode' is also default
file_handle = open("read.txt", 'rt')
file_handle = open("read.txt", 'r')
file_handle = open("read.txt")

# prompts Success! in terminal
print( file_handle.read() )

# manually close file handle
file_handle.close()
```

<span style="font-size:1.4em;">The With Statement And Context Managers</span>

We will be making use of the [the with statement](https://docs.python.org/3/reference/compound_stmts.html#the-with-statement) predominately, which is used to wrap the execution of a code block with methods defined by a [context manager](https://docs.python.org/3/reference/datamodel.html#with-statement-context-managers). The main reason being, that we won't need to manually close file objects.

```py
with open("read.txt") as file_handle:
    print( file_handle.read() )
```

<span style="font-size:1.4em;">Reading One Line At A Time</span>


Unlike the `read()` method where, if we omit the size, the entire contents of the file is read and returned; `list(file_handle)` or `file_handle.readlines()` reads all the lines of a file into a list.

```py
# identical to readlines; more descriptive
with open("read.txt") as file_handle:
    for line in list(file_handle):
        print(line, end="")

# alternatively and more idiomatically
with open("read.txt") as file_handle:
    for line in file_handle.readlines():
        print(line, end="")
```

The faster and more memory efficient method is to loop over the file object in order to read lines from a file. This is the more recommended way to achieve what was written above. I'll also demonstrate the use of enumerate in the second example.

```py
with open("read.txt") as file_handle:
    for line in file_handle:
        print(line, end="")

with open("read.txt") as file_handle:
    for line_number, line in enumerate(file_handle, start=1):
        print(f"{line_number}: {line}", end="")

'''file: read.txt
1: Success!
2: 
3: Hello?
4: 
5: Can You See This?
'''
```

<span style="font-size:1.4em;">Writing To A File</span>

Now that we understand the basic principles of reading from a file, let us delve into the ways we can write to a file. We must be careful to distinguish between `'w'` and `'a'` modes. We can see in the first examples that, if the file existed, then it would truncate the string *"Truncated!"* to the file; otherwise, if the file does not exist, it will first create the file and then write to it.

```py
with open("read.txt", 'w') as file_handle:
    file_handle.write("Truncated!")

with open("read.txt", 'w+') as file_handle:
    file_handle.write("Truncated!")
```

The additional `'+'` mode tells the interpreter to open the file for writing as well as reading. So in this example we will do both. Notice the use of the method call to <a href="https://docs.python.org/3/library/io.html?highlight=seek#io.IOBase.seek">`seek()`</a> which changes the stream position to the given byte offset.

```py
with open("read.txt", 'w+') as file_handle:

    # write the string to the file
    file_handle.write("Truncated!")

    # change the stream position from
    # a byte offset of 10 to 0
    file_handle.seek(0)

    # read the file from the beginning
    print(file_handle.read())
```

I'll give one more example, but this time implementing the `tell()` method so we can see why we needed to seek to byte offset 0 in the last example. You can see in the output below the compound with statement, that once the file descriptors write method had written to the file, the position was at 10, so if we had decided to read from this position it wouldn't have shown the *"Truncated!"* string until we set the position to the beginning of the file.

```py
with open("read.txt", 'w+') as file_handle:

    # write the string to the file
    file_handle.write("Truncated!")

    # print the current stream position
    print(file_handle.tell())

    # change the stream position from
    # a byte offset of 10 to 0
    file_handle.seek(0)

    # print the current stream position
    print(file_handle.tell())

    # read the file from the beginning
    print(file_handle.read())

'''
10
0
Truncated!
'''
```

<span style="font-size:1.4em;">Buffered Read</span>

Some files are so massive that we need to break them up into chunks of data before reading them. Let's first create a large file filled with data. We can use [mpmath](https://mpmath.org/doc/current/basics.html#setting-the-precision) to generate a large file containing a calculation of pi to a precision of 1,000,000 decimal places.

```py
from mpmath import mp

mp.dps  = 1000000
mp.prec = 3.33*mp.dps
bufSize = 25

with open("pi_1m.txt", 'w+') as file_handle:
    file_handle.write(str(mp.pi))
```

Here is an example of both creating, writing to, and reading from a file we have filled with pi to a precision of 1000.

```py
from mpmath import mp

mp.dps  = 1000
mp.prec = 3.33*mp.dps
bufSize = 25

with open("pi_1k.txt", 'w+') as file_handle:
    file_handle.write(str(mp.pi))

    file_handle.seek(0)

    while True:
        buffer    = file_handle.read(bufSize)
        bytesRead = len(buffer)

        if not bytesRead:
            break

        print(f"[{bytesRead:02,d}-bytes]: {buffer}")

'''
[25-bytes]: 3.14159265358979323846264
[25-bytes]: 3383279502884197169399375
[25-bytes]: 1058209749445923078164062
[25-bytes]: 8620899862803482534211706
[25-bytes]: 7982148086513282306647093
[25-bytes]: 8446095505822317253594081
[25-bytes]: 2848111745028410270193852
[25-bytes]: 1105559644622948954930381
[25-bytes]: 9644288109756659334461284
[25-bytes]: 7564823378678316527120190
[25-bytes]: 9145648566923460348610454
[25-bytes]: 3266482133936072602491412
[25-bytes]: 7372458700660631558817488
[25-bytes]: 1520920962829254091715364
[25-bytes]: 3678925903600113305305488
[25-bytes]: 2046652138414695194151160
[25-bytes]: 9433057270365759591953092
[25-bytes]: 1861173819326117931051185
[25-bytes]: 4807446237996274956735188
[25-bytes]: 5752724891227938183011949
[25-bytes]: 1298336733624406566430860
[25-bytes]: 2139494639522473719070217
[25-bytes]: 9860943702770539217176293
[25-bytes]: 1767523846748184676694051
[25-bytes]: 3200056812714526356082778
[25-bytes]: 5771342757789609173637178
[25-bytes]: 7214684409012249534301465
[25-bytes]: 4958537105079227968925892
[25-bytes]: 3542019956112129021960864
[25-bytes]: 0344181598136297747713099
[25-bytes]: 6051870721134999999837297
[25-bytes]: 8049951059731732816096318
[25-bytes]: 5950244594553469083026425
[25-bytes]: 2230825334468503526193118
[25-bytes]: 8171010003137838752886587
[25-bytes]: 5332083814206171776691473
[25-bytes]: 0359825349042875546873115
[25-bytes]: 9562863882353787593751957
[25-bytes]: 7818577805321712268066130
[25-bytes]: 0192787661119590921642019
[02-bytes]: 89
'''
```

We will make use of the `'b'` or binary mode as well. For reading and writing raw bytes use binary mode and leave encoding unspecified. Let's attempt to read from the file that contains the 1,000,000 precision pi calculation.

```py
bufSize = 100

with open("pi_1m.txt", "rb") as file_handle:
    while True:
        buffer = file_handle.read(bufSize)
        bytesRead = len(buffer)

        if not buffer:
            break

        print(f"[{bytesRead:02,d}-bytes]: {buffer}")
```

We can further condense our code by implementing an assignment expression via walrus operator.

```py
buffer, bufSize = None, 100

# example using length comparison in condition
with open("pi_1m.txt", "rb") as file_handle:
    while len(buffer := file_handle.read(bufSize)) != 0:
        print(f"[{len(buffer):02,d}-bytes]: {buffer}")

# example using EOF from read method return (string)
with open("pi_1m.txt", "r") as file_handle:
    while (buffer := file_handle.read(bufSize)) != '':
        print(f"[{len(buffer):02,d}-bytes]: {buffer}")

# example using EOF from read method return (bytes)
with open("pi_1m.txt", "rb") as file_handle:
    while (buffer := file_handle.read(bufSize)) != b'':
        print(f"[{len(buffer):02,d}-bytes]: {buffer}")
```

Instead of showing the size of the buffer every time, we could prompt the total amount of bytes read.

```py
buffer, bufLen, bufSize = None, 0, 50

with open("pi_1m.txt", "rb") as file_handle:
    while (buffer := file_handle.read(bufSize)) != b'':
        bufLen += len(buffer)
        print(f"{hex(bufLen):<8}: {buffer}")

'''
0x32    : b'3.141592653589793238462643383279502884197169399375'
0x64    : b'10582097494459230781640628620899862803482534211706'
0x96    : b'79821480865132823066470938446095505822317253594081'
0xc8    : b'28481117450284102701938521105559644622948954930381'
0xfa    : b'96442881097566593344612847564823378678316527120190'
0x12c   : b'91456485669234603486104543266482133936072602491412'
0x15e   : b'73724587006606315588174881520920962829254091715364'
--- [ 0x190 to 0xf4a74 skipped ] ---
0xf4aa6 : b'41834865833364314027639693910707237967638770808907'
0xf4ad8 : b'54603191915200788416149577637354864681844110384241'
0xf4b0a : b'65823969936822816403630388781648321432715341952500'
0xf4b3c : b'75515717529298633693673876694583251651911954657839'
0xf4b6e : b'36460223407898671238770886661104613626409576399196'
0xf4ba0 : b'55620296225771822659622911817677173943273852488446'
0xf4bbe : b'362636125648422069299840509968'
'''
```

<span style="font-size:1.4em;">Hash Checking With SHA256</span>

Another useful way we can used buffered read is by applying a one-way cryptographic hash algorithm to our file to check for integrity. That is, to "see if it has changed."

```py
import hashlib

sha256 = hashlib.sha256()
with open("pi_1m.txt", "rb") as file_handle:

    while True:
        buffer = file_handle.read(2**10)
        bytesRead = len(buffer)

        if not bytesRead:
            break

        sha256.update(buffer)

        print(f"[{bytesRead:02,d}-bytes]: {buffer}", end="\n\n")

    size = len(sha256.digest())
    hexdigest = sha256.hexdigest()
    print(f"[{size}-bytes]: {hexdigest}")

'''
df6fc820af22577855bf0fbf45c7e96241c699663add68b7e704b8386b9edbc3
'''
```

Once more, except this time we will apply an assignment expression to create more succinct code.

```py
import hashlib

buffer = b''
sha256 = hashlib.sha256()

with open("pi_1m.txt", "rb") as file_handle:
    while (buffer := file_handle.read(2**10)) != b'':
        sha256.update(buffer)
        print(f"[{len(buffer):02,d}-bytes]: {buffer}", end="\n\n")

    size = len(sha256.digest())
    hexdigest = sha256.hexdigest()
    print(f"[{size}-bytes]: {hexdigest}")

'''
df6fc820af22577855bf0fbf45c7e96241c699663add68b7e704b8386b9edbc3
'''
```

<!-- <span style="font-size:1.4em;">Buffered Write</span>

```py
with open(fromFile, "rb") as inFile, \
        open(toFile  , "wb") as outFile:

        while True:
            buffer    = inFile.read(2**10)
            bytesRead = len(buffer)

            if not bytesRead:
                break

            outFile.write(buffer)

            print(f"[{bytesRead:02,d}-bytes]: {buffer}", end="\n\n")
``` -->