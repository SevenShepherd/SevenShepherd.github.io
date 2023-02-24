---
layout: post
title: "💻👨‍💻 Computer Programming Courses And Digital Discipleship"
date: 2023-02-21 01:30:30 -0500
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

<!-- When you installed the [Python Interpreter](https://www.python.org/downloads/) it came packaged with something called IDLE.

```py
    Text Type:      str
    Numeric Types:  int, float, complex
    Sequence Types: list, tuple, range
    Mapping Type:   dict
    Set Types:      set, frozenset
    Boolean Type:   bool
    Binary Types:   bytes, bytearray, memoryview
``` -->

<!-- <span style="font-style:italic;font-size:21px;">Running The Script</span> -->


<!-- ```py
import os

def main():
    print("")

if __name__ == "__main__":
    main()
``` -->

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