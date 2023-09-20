---
title: Markdown Guide 
date: 2023-09-20 19:33:20 +0530
categories: [Programming, Miscellaneous]
tags: [programming, note taking, markdown]     # TAG names should always be lowercase
summary: This is post we walk through some basis markdown syntax 
excerpt_card: This is post we walk through some basis markdown syntax 
image:
  path: /assets/img/Markdown_Guide/MarkdownImage.png
  alt: Markdown symbol 
---

# Markdown Guide

Markdown is a "formatting" language, by which I mean it provides you with syntax that can be used to format your text in some predefined way like heading, paragraphs, etc. Well than you might ask .. so is HTML and latex, yes but for "simple" cases they are overkill, often slows you down, and not to mention hard to read! The reason is simple, to provide more formatting choices more syntax is required. And often syntax is "standardized" meaning you won't have simple syntax for some common formatting options and "hard" syntax for uncommon, usually syntax follow some uniform practice.

Markdown is very simple to learn. Apart from its popular usage, say in documentation and in literally every other file which has text and is not going to be "printed" i.e precise formatting is required, its just very convenient. Instead of using bare `.txt` file with no formatting, markdown is step up with very little learning curve. Which makes it a go-to for taking notes and making documentations.

In this post we will cover basic markdown syntax like creating headings, paragraph, bold and italic text, code blocks, block quotes, adding images, lists, links, divider (horizontal line), table, to-do list, and some other features like auto generating a table of content, etc. Though note that markdown viewers doesn't always abide by the "law". Every interpreter (the software which renders your `.md` file) has there own syntax which can sometimes be different from some other software. That said most of them do abide on some standard implementations. However, given markdown is so bare minimal, to provide a little more functionality each software might add a few tricks of there own. For instance table of content is not a universal markdown feature!

Philosophically the point of markdown is to create a readable text file with some standard protocol to symbolize say header or list, just like taking notes on piece of paper. Just that in computer you can't just increase the text of your word (in text file) so we agree if, say `# Calculus` it is to be read as heading is Calculus, i.e imagine in your mind while reading it has big font's .. the whole point is to provide some structure to our text file by keeping some protocols in place. It is only when we actually want to "view" the file as they were imagined we get into a bit of trouble as mentioned before.

## 1. Editors and Renders

First things first what is `.md` file, how to "write" it, how to "open" it. If you are new to programming world you might have these questions. Let me answer one by one. Markdown file is just a file with `.md` as the file extension, just like you have `.pdf` or `.mp4`. In order to edit the file you will need an editor, a software that lets you edit the contents of the file. There are many editors out there (actually too many). I personally use [Neovim](https://neovim.io/), however this might not be the best for you. To keep things simple you might wanna start with some online editors like [Stackedit](https://stackedit.io/) or [Dillinger](https://dillinger.io/). For completion sake, here are a few markdown editors that I have used and like -

1. [Simple Notes](https://simplenote.com/): It has a very nice feature, it auto syncs your files between different devices you are logged into. Now that I am writing this it doesn't seem a big deal, but it is just so fluid! Anyway if it is not enough, its super minimal and the typing, it just feels so good (I really don't know, may be that particular font size, family and the latency between display of character and me pressing it ..). I have used Linux and android versions, and it works like charm.
  
2. [Joplin](https://joplinapp.org/): A bit of heavy duty, room for a lot of customization.
  
3. [Marktext](https://www.marktext.cc/): The prettiest of the bunch I think. Minimal with good design
  
4. There are of course, dozens of other good apps like [Notion](https://www.notion.so/). Not sure but I think apple notes also allows for markdown. Basically at this point, we are straying away from basis editor to full fledged note taking systems with a lot of different features.
  

Now apps that can render your `.md` file. If you are using any of the above software (expect Neovim), than they have inbuilt viewer which shows the output side by side. But say you just have `.md` file natively on your disk and want to see formatted version. Well there is [Okular](https://okular.kde.org/), I don't know of any other good alternative though. I use this, doesn't have the best look by any measure but gets the job done. You can always copy the text and paste into one of the above editors and have a nicer viewing experience.

## 2. Markdown-101

### 2.1 Headings

```markdown
# Heading 1

## Heading 2
```

Use `#` before the word to make it a heading. Which basically means bigger font size. You can append `#` up to 6 times, each time decreases the font size. I.e `#` can be used as primary header, with `##` as sub headers and `###` as sub sub headers, and so on.

As an example the post's heading is `#`, each topic (like *Markdown-101*) or chapter is `##` and sub topics like this one (*Headings* section) is `###`.

### 2.2 Paragraph

```markdown
This is the first paragraph.
It is still continuing. While rendering, 
all lines will appear together without gap.

This is second paragraph.
```

This is sometimes where people get confused. Using a line break (enter) doesn't mean you changed paragraph. It makes no difference. The next line will appear right after the full stop. To enter into a new paragraph, you need to leave a line between or use 2 enters.

In some editors using 1 enter moves to a new paragraph like in Notion, Marktext, Joplin. But if you are reading documentations, than above convention is followed.

### 2.3 Bold and Italic

Use can use `**<word>**` or `__<word>__`to make it bold. And use `*<word>*` or `_<word>_` to make it italic. You can combine these two like ***hello*** using `***<word>***` or `___<word>___`.

### 2.4 Lists

For an un-ordered list you can use `-` and for ordered (i.e numbered) you can use `1. <line>` and `2. <line>` and so on. You can also use `1)` for ordered list. For to-do list you can use `[]`. To mark it as done, fill it with `x` as in `[x]`. Mixing is also allowed for instance you can unordered list with a to-do as shown below.

```markdown
- This is first point
- This is second point

1. First step
2. Second step

[] Buy apples
[x] Pick up groceries

- [] This is to-do in unordered list.
```

### 2.5 Code blocks

````markdown
```python
import matplotlib.pyplot as plt
import numpy as np
...
```
````

Use triple-'\`' followed by code in next line and ended with triple-'\`' again in new line, as shown above. Instead of python you can use any other language as well, your smart editor might use this information for syntax highlighting. 

### 2.6 Block quotes

```markdown
> This is a block quote
>
> This is being written in same block quote
```

You can have nested block quotes like -

```markdown
> This is block quote
>
>> This is sub block quote
```

You can use other markdown syntax inside block quote like lists, links, heading, etc.

### 2.7 Links

```markdown
Syntax: [<word>](link)

Example: [Google](www.google.com)
```

Use `[]()` where the word goes in square bracket and the hyperlink in round brackets.

### 2.8 Images

```markdown
Syntax: ![alt](link or path)

Example: ![Google logo](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/2560px-Google_2015_logo.svg.png)
```

Here alt means what to display if there is error while displaying image. Say your CDN goes down or you input wrong file path.

### 2.9 Horizontal line

Not sure why I put it so back, to draw a horizontal line whose purpose can be thought as divider use `---` i.e 3 dashes (or more).

### 2.10 HTML

You can always use HTML rules in markdown i.e `<em>word<em>` would work. But you can't markdown inside of it.

### 2.11 Tables

This is not elegant, you might wanna use an online table generator like [table generator](https://www.tablesgenerator.com/markdown_tables). But here is the syntax anyways -

```markdown
| Column 1 heading      | Col 2 heading |
| ----------- | ----------- |
| <something> | <something> |
| <something> | <something> |
```

Put your content of table in place `<something>`. You can increase the number of columns and rows by following the pattern.

### 2.12 Escaping characters

With any syntax there are some corner cases where the interpretation is ambigous. Say you want to display the following markdown where `-` is just outputted as minux and not as unordered list, how will you go about it?

```markdown
- <- this is minus sign
```

This will be viewed as a list, to indicate that it is not syntax but just symbol use `\`. I.e

```markdown
\- <- this is minus sign
```

### 2.13 Footnotes

```markdown
Consider a falling object[^1] with velocity v. Imagine another object[^assume]
collide with it.

[^1]: Ignore air resistance..

[^assume]: Let this object have same velocity as first object.
```

`[^<number>]` or `[^<id>]`, where id can be say a specific name like assumptions. Just note don't keep the id same for 2 footnotes, i.e numbering is the standard choice.

## 3. Further reading and resources

1. [Markdown Guide](https://www.markdownguide.org/basic-syntax): This is the place I learnt from. There explanation is simple and very visual. They have basic and an extended version, later contains some syntax that aren't supported by some processors.
