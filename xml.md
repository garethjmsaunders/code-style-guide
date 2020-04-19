# XML style guide

Version 1.2.0
Last updated: Tuesday 19 July 2016

The terms MUST, MUST NOT, SHOULD, SHOULD NOT, and MAY are used in this document with the meanings found in [RFC 2119: Key words for use in RFCs to indicate requirement levels](https://www.ietf.org/rfc/rfc2119.txt).

<!-- MarkdownTOC -->

- [1. Syntax](#1-syntax)
    - [1.1 Well-formed XML](#11-well-formed-xml)
    - [1.2 General formatting](#12-general-formatting)
    - [1.3 Entity references](#13-entity-references)
        - [Character references](#character-references)
        - [International characters](#international-characters)
    - [1.4 Empty elements](#14-empty-elements)
- [2. Reuse existing XML formats](#2-reuse-existing-xml-formats)
    - [2.1 Extending existing formats](#21-extending-existing-formats)
- [3. XML prolog](#3-xml-prolog)
    - [3.1 Optional](#31-optional)
    - [3.2 Character encoding](#32-character-encoding)
- [4. Schemas](#4-schemas)
- [5. Namespaces](#5-namespaces)
    - [5.1 Prefixes](#51-prefixes)
    - [5.2 Namespace names](#52-namespace-names)
    - [5.3 Attribute names](#53-attribute-names)
- [6. Names](#6-names)
- [7. Elements](#7-elements)
    - [7.1 Mixed content](#71-mixed-content)
- [8. Attributes](#8-attributes)
- [9. Key-value pairs](#9-key-value-pairs)
- [10. Elements vs attributes](#10-elements-vs-attributes)
    - [10.1 Elements](#101-elements)
    - [10.2 Attributes](#102-attributes)
- [11. CDATA](#11-cdata)
- [12. Comments](#12-comments)
    - [12.1 Formatting](#121-formatting)
    - [12.2 General rules](#122-general-rules)
    - [12.3 TODOs](#123-todos)
- [References](#references)

<!-- /MarkdownTOC -->




---

## 1. Syntax


### 1.1 Well-formed XML

All XML documents MUST be 'well-formed' in accordance with the [latest XML specification](https://www.w3.org/TR/xml/).

You may find it useful to use an XML validation service, such as those provided by [Code Beautify](http://codebeautify.org/xmlvalidate) or [Validome](http://www.validome.org/xml/), or a code editor plugin such as [Sublime​Linter-xmllint](https://packagecontrol.io/packages/SublimeLinter-xmllint).


### 1.2 General formatting

For consistency:

* Use soft tabs with FOUR spaces. Spaces are the only way to guarantee code renders the same in any environment. Four spaces offer more obvious indentation compared with two.
* Nested elements should be indented once (four spaces).
* Element names should be written in lower camel case, e.g. `lowerCamelCase`.
* Attributes should be wrapped in double quotes (`"`) rather than single quotes (`'`), on attributes.
* Use one space before attributes in an opening-tag. If the tag is too long, the space may be replaced by a newline.


### 1.3 Entity references

Entity references other than the five standard XML entity references MUST NOT be used. The five acceptable entity references are:

* `&amp;` - ampersand (&)
* `&apos;` - apostrophe (')
* `&gt;` - greater than (>)
* `&lt;` - less than (<)
* `&quot;` - double quotation (")


#### Character references

Character references may be used, but actual characters are preferred as they are more-easily searchable. An exception to this rule is if the character set is not UTF-8.

For example the copyright symbol `©` may be represented either in decimal (`&#169;`) or hexadecimal (`&#x00A9;`) but it is preferable to use `©` where possible.


#### International characters

XML documents may contain international characters, like Scandanavian `ø`, `æ`, and `å` or French `ê`, `è` and `é`.

Again, you may use character references (above) but prefer to use actual characters.


### 1.4 Empty elements

Some elements do not have end tags because they do not contain anything, consider XHTML tags such as `<img />` and `<br />`.

These self-closing (or empty) elements may be written in one of two ways:

1. As a start tag immediately followed by an end tag, e.g. `<empty></empty>`.
2. As an empty element with a trailing slash, e.g. `<empty />`.

In the case of empty elements, include a space immediately before the closing slash.

Either format is acceptable as neither is preferred by XML parsers. Whichever you choose, please be consistent throughout your document.




---

## 2. Reuse existing XML formats

Where possible reuse existing XML formats, particularly those that allow extensions. XML Cover Pages curates a list of nearly 600 established [XML applications and initiatives](http://xml.coverpages.org/xmlApplications.html).

Creating a new XML format is hard work and should only be done with consideration. As Google advises, "try to get wide review of your format, from outside your organization as well, if possible [as] new document formats have a cost: they must be reviewed, documented, and learned by users".

Consider Tim Bray's article first: [Don’t invent XML languages](https://www.tbray.org/ongoing/When/200x/2006/01/08/No-New-XML-Languages).


### 2.1 Extending existing formats

When reusing or extending existing formats follow their established conventions and implicit styles for elements and attributes, even if they contradict this guide. Internal file consistency is prefered over strict adherance to this guide.




---

## 3. XML prolog

The XML prolog appears before the document's root element. XML documents SHOULD begin with an XML prolog that contains:

1. A declaration that specifies the version of XML being used;
2. A document type declaration (DTD)

```
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<!DOCTYPE foo SYSTEM "foo.dtd">
```


### 3.1 Optional

* The XML prolog itself is optional.
* If the XML prolog exists, it MUST come first in the document.
* The DTD is optional, depending on the schema used.
* The `standalone="yes"` attribute is optional. Valid values are `yes` and `no` (default value). The attribute is only relevant when a DTD is used; and irrelevant when used with a schema instead of a DTD.


### 3.2 Character encoding

To avoid errors, you should specify the encoding used, or save your XML files as UTF-8; UTF-8 is the default character encoding for XML documents.

The character encoding used should be UTF-8 (Unicode), which is a universal standard.

```
<?xml version="1.0" encoding="UTF-8" ?>
```

You will need to provide a very good argument for using a character encoding that is not UTF-8.




---

## 4. Schemas

Document formats SHOULD be expressed using a schema language. This improves clarity and ensures documents can be checked programmatically.

An XML schema is a language for defining constraints about XML documents. There are a number of common schema languages; the more popular are Document Type Definitions (DTDs), RELAX NG, Schematron and W3C XSD (XML Schema Definitions).

The schema language SHOULD be [RELAX NG compact syntax](http://www.relaxng.org/compact-tutorial-20030326.html) which is both simple and flexible.

DTDs and/or W3C XML Schemas may be provided for compatibility with existing products, tools, or users.




---

## 5. Namespaces

"XML namespaces are used for providing uniquely named elements and attributes in an XML document. They are defined in a [W3C recommendation](https://www.w3.org/TR/xml-names/). An XML instance may contain element or attribute names from more than one XML vocabulary. If each vocabulary is given a namespace, the ambiguity between identically named elements or attributes can be resolved." (Wikipedia)

Where possible, declare namespaces in the root element of a document.

An XML namespace is declared using the reserved XML attribute `xmlns` or `xmlns:prefix`, the value of which must be a valid namespace name.

* Element names MUST be in a namespace, except when extending pre-existing document types that do not use namespaces.
* A default namespace SHOULD be used.


### 5.1 Prefixes

Well-known prefixes such as `xhtml` (for XHTML), `dc` (for Dublin Core metadata), and `xs` (for XML Schema) SHOULD be used for standard namespaces.

St Andrews-specific prefixes SHOULD begin `sta`.

```
<root xmlns:xhtml="http://www.w3.org/1999/xhtml"
      xmlns:stahcard="http://www.st-andrews.ac.uk/xmlns/stahcard/2016">
    ...
</root>
```

* Namespace prefixes SHOULD be short, but not so short that they risk clashing with another namespaces.
* Single-letter prefixes MUST NOT be used.
* Prefixes SHOULD contain only lower-case ASCII letters.


### 5.2 Namespace names

Namespace names are HTTP URIs; they SHOULD take the form

```
https://www.st-andrews.ac.uk/xmlns/{namespace}/{year}
```

The namespace should be defined in an HTML document at that URI.


### 5.3 Attribute names

Attribute names SHOULD NOT be in a namespace.

Attribute names in a namespace are harder to read as each attribute in the namespace must be prefixed.

```
HARDER TO READ
<sta:dimensions sta:height="4" sta:length="5" sta:unit="metres" />

EASIER TO READ
<sta:dimensions height="4" length="5" unit="metres" />
```




---

## 6. Names

Names here refers to elements, attributes and enumerated values (controlled vocabularies).

* Names MUST use lowerCamelCase: they begin with an initial lower-case letter, then each new word begins with an initial capital letter.
* Names MUST contain only ASCII letters and digits.
* Names SHOULD NOT be longer than 25 characters.
* Acronyms MUST be treated as words for camel-case purposes: `sourceUrl` not `sourceURL`.




---

## 7. Elements

All elements MUST contain either:

Nothing (empty elements),

```
<name surname="Blackadder" />
<order orderId="7000" />
<shipDate date="2012-10-15" />
```

Character content, or

```
<name>Agnes Blackadder</name>
<orderId>7000</orderId>
<shipDate>2012-10-15</shipDate>
```

Child elements.

```
<letter>
    <name>Agnes Blackadder</name>
    <orderId>7000</orderId>
    <shipDate>2012-10-15</shipDate>
</letter>
```

### 7.1 Mixed content

DO NOT use mixed content as many XML data models do not handle mixed content properly.

```
<letter>
  Dear Dr <name>Agnes Blackadder</name>.
  Your order <orderId>7000</orderId>
  will be shipped on <shipDate>2012-10-15</shipDate>.
</letter>
```


XML elements that merely wrap repeating child elements SHOULD NOT be used as they add nothing to the document.




---

## 8. Attributes

* You may use either single (`'`) or double (`"`) quotation marks around attribute values; XML parsers make no distinction. However, be consistent in your use of one or the other, and where possible prefer double quotation marks.
* `&apos;` and `&quot;` may be freely used to escape each type of quote.
* Use one space before each attribute in an element. If the line is too long then use a newline instead.`
* Do not use too many attributes (fewer than 10 is a good guide). Consider using child elements if you need to convey that amount of information.
* Attributes must not be used to hold values in which line breaks are important. Complient XML parsers will simply convert these line breaks to spaces.

If creating your own document formats:

* Document formats MUST NOT depend on the order of attributes in an element.
* Document formats MUST allow either single (`'`) or double (`"`) quotation marks around attribute values; XML parsers make no distinction.




---

## 9. Key-value pairs

Simple key-value pairs SHOULD be represented with an empty element whose name represents the key, with the value attribute containing the value.

```
<key valueID="value" />
```

It can be helpful to include a unit attribute to specify the unit of measurement. Physical measurements should be specified using the SI system, e.g.

```
<dimensions height="4" length="5" unit="metres" />
```


As Google point out: "keeping the value in an attribute hides it from the user, since displaying just the value without the key is not useful."




---

## 10. Elements vs attributes

There are no strict rules for deciding when to use elements and when to use attributes. However, bear in mind that elements are generally less restrictive than attributes.

* When streaming XML documents, elements are processed serially (one at a time) while attributes and their values are all reported at the same time (which also has an impact on memory).
* Both element content and attribute values need to be escaped appropriately. Therefore, escaping cannot be used as a factor to determine which to use.
* Similarly, depending on the language and parser one may be easier to process than the other. Schemas like RELAX NG regard elements and attributes equally.

Needless to say, for the sake of continuity and document integrity, if you extend an existing schema follow its internal conventions.


### 10.1 Elements

Bear in mind that elements generally use more memory than attributes.

Consider using an element if the data should normally be shown to the user, or if something may appear more than once in the data model.


### 10.2 Attributes

Consider [Google's advice](https://google.github.io/styleguide/xmlstyle.html) about attributes:

> * If the data is a code from an enumeration, code list, or controlled vocabulary, put it in an attribute if possible.  For example, language tags, currency codes, medical diagnostic codes, etc. are best handled as attributes."
> 
> * If a piece of data is really metadata on some other piece of data (for example, representing a class or role that the main data serves,  or specifying a method of processing it), put it in an attribute if possible.
> 
> * In particular, if a piece of data is an ID for some other piece of data, or a reference to such an ID, put the identifying piece in an attribute.  When it's an ID, use the name xml:id for the attribute.
> * If a piece of data is applicable to an element and any descendant elements unless it is overridden in some of them, it is conventional to put it in an attribute.  Well-known examples are xml:lang, xml:space, xml:base, and namespace declarations.




---

## 11. CDATA

CDATA sections allow the use of all valid Unicode characters in their literal forms; in other words, characters that would otherwise be interpretted as markup.

CDATA sections may be used, as follows:

* Begin with `<![CDATA[`
* Insert your content (with no spaced before or after)
* End with `]]>`, like so:

```
<![CDATA[your content here]]>
```

Specifications must not forbid the use of CDATA sections.




---

## 12. Comments

Comments allow you to leave messages for other developers (and for yourself, if you return to your code months later).

As a general rule, if it is not immediately obvious from the code alone then write a comment. For instance, you could explain

* the structure or role of a file
* the thought process behind a way of doing something
* the name of a digital pattern library pattern being used.

Comments SHOULD appear only in the document prolog, or in elements that contain child elements.


### 12.1 Formatting

* Comments SHOULD be written as complete, grammatical sentences with an initial capital and a full-stop at the end.
* Begin comments with `<!-- `, this includes a space after the dashes.
* End comments with ` -->`, this incluedes a space before the dashes.
* Comments SHOULD have whitespace before and after, to aid readability

```
WRONG
<!--not a complete sentence and harder to read-->

CORRECT
<!-- With spaces it makes this sentence easier to read. -->
```


### 12.2 General rules

* Comments MUST be kept up-to-date when code changes.
* Comments MUST NOT be used to carry real data.
* Closing tag comments MUST NOT be written, e.g. `<!-- /element -->`. These simply add to code bloat, besides most code editors now have good indentation.
* Comments SHOULD NOT make their way into production environments.
* Comments SHOULD NOT appear in elements that contain character content.


### 12.3 TODOs

Comments MAY be used to contain `TODO`s in hand-written XML documents. These should be written at the top of the document, in the prolog.

Write each TODO as a new comment; this makes it easier to edit and remove.

```
<!-- TODO Remember the milk -->
<!-- TODO Second thing to remember -->
```



---

## References

The initial version of this style guide was based on [Google XML document format style guide](https://google.github.io/styleguide/xmlstyle.html)