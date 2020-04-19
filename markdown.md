# Markdown style guide

Version 1.2.0
Last updated: Wednesday 28 September 2016

The terms MUST, MUST NOT, SHOULD, SHOULD NOT, and MAY are used in this document with the meanings found in [RFC 2119: Key words for use in RFCs to indicate requirement levels](https://www.ietf.org/rfc/rfc2119.txt).

<!-- MarkdownTOC -->

- [1. Documents](#1-documents)
    - [1.1 Filenames](#11-filenames)
    - [1.2 Document layout](#12-document-layout)
        - [Intro block](#intro-block)
        - [Spacing](#spacing)
        - [Footer](#footer)
- [2. Block Elements](#2-block-elements)
    - [2.1 Paragraphs and line breaks](#21-paragraphs-and-line-breaks)
    - [2.2 Headings](#22-headings)
    - [2.3 Blockquotes](#23-blockquotes)
    - [2.4 Lists](#24-lists)
        - [Unordered lists](#unordered-lists)
        - [Ordered lists](#ordered-lists)
        - [Formatting lists](#formatting-lists)
    - [2.5 Code blocks](#25-code-blocks)
    - [2.6 Horizontal rules](#26-horizontal-rules)
    - [2.7 Tables](#27-tables)
- [3. Span elements](#3-span-elements)
    - [3.1 Links](#31-links)
        - [Inline links](#inline-links)
        - [Reference links](#reference-links)
        - [Automatic links](#automatic-links)
    - [3.2 Emphasis](#32-emphasis)
        - [Bold](#bold)
        - [Italic](#italic)
    - [3.3 Code](#33-code)
    - [3.4 Images](#34-images)
- [4. Miscellaneous](#4-miscellaneous)
    - [4.1 Backslash escapes](#41-backslash-escapes)
- [5. Sublime Text packages](#5-sublime-text-packages)
    - [5.1 Markdown​Editing](#51-markdown​editing)
    - [5.2 Markdown Preview](#52-markdown-preview)
    - [5.3 MarkdownTOC](#53-markdowntoc)

<!-- /MarkdownTOC -->




---

## 1. Documents

### 1.1 Filenames

Filenames MUST use `.md` suffix rather than `.markdown`.

If the Markdown file is a **product deliverable** (such as these style guide files) then the filename SHOULD be all lowercase, including the `.md` file suffix.

If the Markdown file is a **supporting document** with instructions, set up guides, changelogs, etc. (such as CHANGELOG.md, CONTRIBUTING.md, README.md, SETUP.md)  then the filename SHOULD be uppercase

```
\\ Correct

css.md
html.md
markdown.md
CHANGELOG.md
CONTRIBUTING.md
README.md
SETUP.md

\\ Wrong

css.MD
HTML.MD
MarkDown.md
changelog.md
CONTRIBUTING.MD
ReadMe.md
Setup.markdown
```


### 1.2 Document layout

#### Intro block

The standard layout for the beginning of a Markdown-formatted document is:

* Document title
* Version number
* Last updated date (written in full)
* TODO items
* Table of contents

Each section MUST be separated by a blank line, except version number and last update date which MUST be grouped together with a line-break.

It MUST look something like this:

```
# Document title (in sentence case)

Version 0.1
Last updated: Thursday 03 March 2016

TODO: (Optional) Add outstanding items here.
TODO: You can have as many or few as you like.

<!-- MarkdownTOC -->
    ...
<!-- /MarkdownTOC -->

---

```

If you are using Sublime Text then use the [MarkdownTOC](https://packagecontrol.io/packages/MarkdownTOC) package to automatically build the table of contents.


#### Spacing

Consistent spacing (blank lines between sections) can help aid the readability of the document, and aid the document reader and writer understand which sections belong together.

The general rules are:

* **Heading 1** No blank lines before, one blank line after.
* **Heading 2** Four blank lines before, one blank line after.
* **Heading 3, 4, 5 or 6** Two blank lines before, one blank line after.
* **Everything else** One blank line before, one blank line after.
* **End of document** Leave a single blank line at the end of the document.

```
# Document title (in sentence case)

Version 0.1
Last updated: Thursday 03 March 2016

TODO: Add outstanding items here.
TODO: You can have as many or few as you like.

<!-- MarkdownTOC -->

- [1. Heading 2](#heading-2)
    - [Heading 3](#heading-3)
        - [Heading 4](#heading-4)

<!-- /MarkdownTOC -->




## Heading 2

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. 

* Duis aute irure dolor in reprehenderit.
* In voluptate velit esse cillum dolore.
* Fugiat nulla pariatur. Excepteur sint occaecat.


### Heading 3

Duis fringilla tortor vel ipsum mattis, a sagittis sem interdum. 
Pellentesque venenatis ante a leo mollis auctor ac vel elit. 
Aenean semper sollicitudin  nulla ut auctor.


#### Heading 4

Etiam id metus purus. Vivamus suscipit id nibh et eleifend. Cras 
non nibh consequat, ultrices est sit amet, volutpat dui. [...]




---

## References

* [Useful resource](http://www.example.com/ "")
* [Another source](http://www.example.com/ "")

```


#### Footer

The footer of a Markdown document MAY be used to list useful resources, references, etc.

It should begin with a blank line, a horizontal rule (three dashes, `---`) and another blank line. Then a heading at level 2 (`##`).


```
\\ Example footer

---

## References

The initial version of this style guide was based on [Github's HTML 
style guide](https://github.com/styleguide/templates), with 
inspiration too from [MDO's code guide](http://mdo.github.io/code-guide/).

Boolean attributes, Lean markup, Forms and Tables taken from
[PrimerCSS](http://primercss.io/guidelines/)
```




---

## 2. Block Elements


### 2.1 Paragraphs and line breaks

According to the [Markdown definition of a paragraph](https://daringfireball.net/projects/markdown/syntax#p):

> A paragraph is simply one or more consecutive lines of text, separated 
> by one or more blank lines. (A blank line is any line that looks like a 
> blank line — a line containing nothing but spaces or tabs is considered 
> blank.) Normal paragraphs should not be indented with spaces or tabs.

* Paragraphs MUST be separated with a single blank line.
* Normal paragraphs MUST NOT be indented with either tabs or spaces.
* To create a line break (to insert a `<br />` tag) end a line with two or more spaces, then type return.
 

### 2.2 Headings

Markdown supports two styles of headings: [Setext](http://docutils.sourceforge.net/mirror/setext.html) and [atx](http://www.aaronsw.com/2002/atx/); we MUST use atx.

Atx-style headings use **one to six number sign characters** (`#`), also called a hash or pound sign, at the start of the line. These correspond to heading levels 1 to 6. For example:

```
# This is a heading 1 (H1)

## This is a heading 2 (H2)

### This is a heading 3 (H3)

#### This is a heading 4 (H4)

##### This is a heading 5 (H5)

###### This is a heading 6 (H6)
```

There MUST be at least **one blank line either side** of the heading.

```
\\ This is correct

## Heading

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua.


\\ This is wrong
## Heading
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua.

```

**Do not close** atx-style headings.

```
\\ This is correct

## This is a heading 2 (H2)


\\ This is wrong

## This is a heading 2 (H2) ##

```


### 2.3 Blockquotes

Prefix each line with a **greater-than sign** `>`. You MUST NOT use the lazy method of only prefixing the first line.

```
> This is a blockquote with two paragraphs. Notice how each
> line is prefixed with a greater-than symbol. You may be
> familiar with this convention from quoting passages in
> your email client.
> 
> You'll notice that blank lines also include a single `>`
> character.
```

You SHOULD avoid nesting blockquotes.


### 2.4 Lists

#### Unordered lists

Use **asterisks** (`*`) for unordered lists. Do not indent first-level lists.

```
\\ Correct

* Apples
* Bananas
* Oranges
* Pears


\\ Wrong

    * Apples
    * Bananas
    * Oranges
    * Pears
```


#### Ordered lists

Use a **number followed by a full-stop** (`1.`) for ordered lists. 

For short lists use sequential numbers, e.g.

```
1. Apples
2. Bananas
3. Oranges
4. Pears
```

For longer lists, reuse the number one (`1.`) before each item. The Markdown interpreter will automatically number the list correctly, but by using the same number for each list item you can easily reorder lists without having to labouriously renumber everything.

```
1. Apples
1. Bananas
1. Blackberries
1. Blueberries
1. Gooseberries
1. Grapefruit
1. Melons
1. Oranges
1. Pears
1. Pineapples
1. Strawberries
```


#### Formatting lists

You MAY use hanging indents, using either 4 spaces or a tab.

```
*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit. 
    Aliquam endrerit mi posuere lectus. Vestibulum enim wisi, 
    viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing.
```

To include a code block within a list item indent it twice — you SHOULD use 8 spaces or two tabs.

*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit. 
    Aliquam endrerit mi posuere lectus. Vestibulum enim wisi, 
    viverra nec, fringilla in, laoreet vitae, risus.

        <code>This is a code block</code>

*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing.

To separate list items (wrapping each list item with a `<p>` tag) add a blank line between each item:

```
1. Apples

1. Bananas

1. Oranges

1. Pears
```


### 2.5 Code blocks

To produce pre-formatted code blocks, add **three backticks** (` ``` `) on blank lines above and below your code.

    ```
    <html lang="en">
        <!-- ... -->
    </html>
    ```


### 2.6 Horizontal rules

Use **three hyphens on their own line** to add a horizontal rule (`<hr />`). There SHOULD be a **blank line above and below** the row of hyphens (otherwise the previous line may be misinterpreted as a Setext heading 2.

```
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum
dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
proident. End of previous paragraph.

---

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. 
```


### 2.7 Tables

Tables are not a part of the core Markdown specification but they are a part of [GFM](https://help.github.com/articles/organizing-information-with-tables/) (GitHub-flavoured Markdown).

An example Markdown table:

```
| Media type           | File extensions      | Content layouts     |
| -------------------- | -------------------- | ------------------- |
| Adobe PDF            | pdf                  | pdf/*               |
| Image                | gif,jpg,jpeg,jpe,png | image/*             |
| Javascript           | js                   | js/*                |
| Microsoft Word       | doc, docx            | docx/*              |
| Microsoft PowerPoint | ppt, pptx            | pptx/*              |
```

which will render like this:

| Media type           | File extensions      | Content layouts     |
| -------------------- | -------------------- | ------------------- |
| Adobe PDF            | pdf                  | pdf/*               |
| Image                | gif,jpg,jpeg,jpe,png | image/*             |
| Javascript           | js                   | js/*                |
| Microsoft Word       | doc, docx            | docx/*              |
| Microsoft PowerPoint | ppt, pptx            | pptx/*              |

* Each row in a table column SHOULD line up. This makes the table easier to read.
* Outer pipes (`|`) MUST be included. While these are optional, again, they make the table more readable while editing.
* There MUST be at least 3 dashes (`---`) separating each header cell. Dashes SHOULD extend the full width of the cell.
* There MUST be a space after the initial pipe and before the next pipe: (`| --- |`) in the header separators.

There may be occasions when you cannot line up all the columns. In this case longer lines MAY simply be written with inline Markdown, such as the second row in the following table. Following the extended cell contents, each pipe is prefixed and suffixed with a space.

```
| Name         | Value                               | Publish language     |
| ------------ | ----------------------------------- | -------------------- |
DC.description | St Andrews is a unique and captivating place, and the University is a key part of its charm. Find out all about the town and University here. | English |
DC.title       | About St Andrews                    | English              |
```




---

## 3. Span elements


### 3.1 Links

Markdown supports three styles of links: inline links, reference links, and automatic links.


#### Inline links

Link text is wrapped in square brackets, followed immediately (no space) by parentheses containing the URL. There MAY be an optional title, wrapped in quotes, after the URL.

```
This is [an example](http://www.example.com/ "Title") inline link.

This [example](http://www.example.com/) inline link has no title attribute.
```

#### Reference links

Reference-style links are best used when you need to link to the same resource repeatedly throughout a document.

Link text is wrapped in square brackets, followed immediately by a space and then a link label also wrapped in square brackets.

```
This is [an example] [label] reference-style link.
```

At the bottom of the section you are editing (above the next `## Heading 2,`) define your link using the label wrapped in square brackets, followed by a colon, space, URL, space, and optional title wrapped in double quotes.

```
[label]: http://www.example.com/ "Optional title"
```

For longer URLs you MAY put the title attribute on a separate line, indented with 4 spaces or a tab, like this:

```
[label]: http://www.example.com/longer/path/to/resource/here/
    "Optional title"
```


#### Automatic links

Markdown also supports a shortcut style for creating automatic links for URLs where you want to show the URL itself, or for email addresses.

Simply wrap the URL or email address in angle brackets, e.g.

```
* <http://digitalcommunications.wp.st-andrews.ac.uk>
* <digitalcommunications@st-andrews.ac.uk>
```

These will display as:

* <http://digitalcommunications.wp.st-andrews.ac.uk>
* <digitalcommunications@st-andrews.ac.uk>


### 3.2 Emphasis

#### Bold

To make text bold, you MUST wrap the text with **two asterisks**.

```
To make text bold, you MUST wrap the text with **two asterisks**.
```


#### Italic

To make text italic, you MUST wrap the text with _one underscore_.

```
To make text italic, you MUST wrap the text with _one underscore_.
```

Although asterisks and underscores can be used for both bold and italic (one for italic, two for bold) they are easier to distinguish if used for different purposes.


### 3.3 Code

Use single backticks to markup inline code, such as `<code>`.

```
Use single backticks to markup inline code, such as `<code>`.
```


### 3.4 Images

Although images are rarely used in our markdown documents, you MUST use the fuller syntax:

```
![Alt text](http://example.com/path/to/img.jpg "Optional title")
```




---

## 4. Miscellaneous


### 4.1 Backslash escapes

Markdown allows you to use backslash escapes to generate literal characters that would otherwise have special meaning in Markdown’s formatting syntax.

Markdown provides backslash escapes for the following characters:

```
*   asterisk
\   backslash
`   backtick
{}  curly braces
.   dot
!   exclamation mark
#   hash mark
-   minus sign (hyphen)
()  parentheses
+   plus sign
[]  square brackets
_   underscore
```




---

## 5. Sublime Text packages

There are a few Sublime Text packages that make working with Markdown documents easier.


### 5.1 Markdown​Editing

A powerful Markdown package for Sublime Text with more robust syntax highlighting and better colour schemes (light and dark). This supports 
    
* Standard Markdown
* GitHub-style Markdown
* MultiMarkdown

<https://packagecontrol.io/packages/MarkdownEditing>


### 5.2 Markdown Preview

Preview in your browser the Markdown file you are currently editing. Supports both standard and GitHub-style Markdown.

(If you choose GitHub-style then your code will be sent through https to the GitHub API for live conversion. You are limited to 60 calls a day unless you add your GitHub API key to your Sublime Text settings.)

https://packagecontrol.io/packages/Markdown%20Preview


### 5.3 MarkdownTOC

This package searches headings within a Markdown document and inserts a hierarchical table of contents (TOC).

<https://packagecontrol.io/packages/MarkdownTOC>
