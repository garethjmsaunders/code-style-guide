# HTML style guide

Version 1.1.1
Last updated: Tuesday 5 July 2016

The terms MUST, MUST NOT, SHOULD, SHOULD NOT, and MAY are used in this document with the meanings found in [RFC 2119: Key words for use in RFCs to indicate requirement levels](https://www.ietf.org/rfc/rfc2119.txt).

<!-- MarkdownTOC depth=3 -->

- [1. Syntax](#1-syntax)
    - [1.1 General formatting](#11-general-formatting)
    - [1.2 Accessibility](#12-accessibility)
    - [1.3 Attribute order](#13-attribute-order)
    - [1.4 Boolean attributes](#14-boolean-attributes)
    - [1.5 Lean markup](#15-lean-markup)
- [2. Document head](#2-document-head)
    - [2.1 HTML5 doctype](#21-html5-doctype)
    - [2.2 Language attribute](#22-language-attribute)
    - [2.3 Character encoding and meta tags](#23-character-encoding-and-meta-tags)
    - [2.4 Page title](#24-page-title)
    - [2.5 IE compatibility](#25-ie-compatibility)
    - [2.6 Links to external CSS and JavaScript files](#26-links-to-external-css-and-javascript-files)
- [3. Element rules](#3-element-rules)
    - [3.1 Address](#31-address)
    - [3.2 Bold and strong](#32-bold-and-strong)
    - [3.3 Comments](#33-comments)
    - [3.4 Forms](#34-forms)
    - [3.5 Images](#35-images)
    - [3.6 Italics and emphasis](#36-italics-and-emphasis)
    - [3.7 Lists](#37-lists)
    - [3.8 Tables](#38-tables)
    - [3.9 tor.com/element-index/\) for advice on the best use of HTML5 elements.](#39-torcomelement-index-for-advice-on-the-best-use-of-html5-elements)
- [4. Class and ID names](#4-class-and-id-names)
    - [4.1 Standard class names](#41-standard-class-names)
    - [4.2 Microformats](#42-microformats)
- [5. Avoid JavaScript-generated markup](#5-avoid-javascript-generated-markup)
- [6. Error pages](#6-error-pages)
    - [6.1 Error templates](#61-error-templates)
- [References](#references)

<!-- /MarkdownTOC -->




---

## 1. Syntax 

### 1.1 General formatting

As [@mdo](http://mdo.github.io/code-guide/) says in his code guide, "Strive to maintain HTML standards and semantics, but not at the expense of practicality. Use the least amount of markup with the fewest intricacies whenever possible."

* Use soft tabs with FOUR spaces. Spaces are the only way to guarantee code renders the same in any environment.
* Nested elements SHOULD be indented once (four spaces).
* Elements SHOULD always be written in lowercase.
* Always use double quotes (`"`), never single quotes (`'`), on attributes. While optional, include quotes to improve code readability.
* Do not include a trailing slash on self-closing elements, such as `<br>`, `<hr>`, `<img>`, `<link>` and `<meta>`. These are optional in the [HTML5 specification](http://dev.w3.org/html5/spec-author-view/syntax.html#syntax-start-tag).


### 1.2 Accessibility
* Do not set `tabindex` manually; rely on the browser to set the order.
* Paragraphs of text SHOULD always be placed in a `<p>` tag. Never use multiple `<br>` tags.


### 1.3 Attribute order

HTML attributes SHOULD come in this particular order for easier reading of code.

* `class`
* `id`, `name`
* `data-*`
* `src`, `for`, `type`, `href`, `value`, `rel`
* `title`, `alt`
* `role`, `aria-*`

Classes make for great reusable components, so they come first; `id`s are more specific and SHOULD be used sparingly (e.g., for in-page bookmarks or JavaScript hooks), so they come second.


### 1.4 Boolean attributes

Unlike in XHTML, in HTML5 many attributes don't require a value to be set, like `disabled` or `checked`, so do not set them.

```
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
    <option value="1" selected>1</option>
</select>
```

If you _must_ include the attribute's value (if you are using XHTML5, for instance) then follow the [WhatWG guideline](https://html.spec.whatwg.org/multipage/infrastructure.html#boolean-attributes):

> If the attribute is present, its value MUST either be the empty string or [...] the attribute's canonical name, with no leading or trailing whitespace.

For more information, read the latest [HTML5 specification](http://www.w3.org/html/wg/drafts/html/master/infrastructure.html#boolean-attributes).


### 1.5 Lean markup

Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML. For example:

```
<!-- Not so great -->
<span class="user-photo">
    <img src="...">
</span>

<!-- Better -->
<img class="user-photo" src="...">
```




---

## 2. Document head

### 2.1 HTML5 doctype 

Use a doctype that triggers standards mode in your browser; this ensures more consistent rendering in browsers. Quirks mode MUST always be avoided.

For simplicity, use the HTML5 doctype:

```
<!DOCTYPE html>
```


### 2.2 Language attribute

The HTML5 specification recommends specifying a language attribute on the root HTML element. This aids speech synthesis tools to determine what pronounciation to use, translation tools what rules to use, etc.

Read more about the `lang` attribute in the latest [HTML5 spec](http://www.w3.org/html/wg/drafts/html/master/semantics.html#the-html-element).

Sitepoint lists all [ISO two-letter language codes](http://www.sitepoint.com/web-foundations/iso-2-letter-language-codes/). W3C Internationalization site discusses [Language tags in HTML and XML](https://www.w3.org/International/articles/language-tags/).

```
<html lang="en-GB">
    <!-- ... -->
</html>
```


### 2.3 Character encoding and meta tags

Ensure proper rendering of your content by declaring an explicit character encoding. When doing so, you may avoid using character entities in your HTML, provided their encoding matches that of the document, generally UTF-8 ([Unicode](http://unicode.org/)).

The character encoding MUST be the first element within `head` as this affects the character set for the entire document, including the `title`.

```
<head>
    <meta charset="utf-8">
    <title> ... </title>
    <meta http-equiv="x-ua-compatible" content="ie=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>
```

These three `<meta>` elements (if used) MUST come before any other `<meta>`elements.

Remember, in HTML5 `<meta>` tags SHOULD NOT include a self-closing trailing slash.

A comprehensive list of `<meta>`, `<link>`, social media, and browser and platform-specific elements can be found on Josh Buchea's [HEAD GitHub repository](https://github.com/joshbuchea/HEAD).


### 2.4 Page title

The standard format for the `<title> ... </title>` tag uses a pipe (`|`) character to separate the page name from the University name:

```
Page name | University of St Andrews
```

Including the page name first makes it easier to create meaningful bookmarks, and improved SEO.


### 2.5 IE compatibility

Internet Explorer 8 and newer supports the use of a document compatibility <meta> tag to specify what version of IE the page should be rendered as.

Unless you have a very specific use-case, it is most helpful to instruct IE to use the latest version of IE using edge mode:

```
<title>
<meta http-equiv="x-ua-compatible" content="ie=edge">
```

This element SHOULD immediately follow the `<title>` element.

As [Microsoft has withdrawn support for older versions of Internet Explorer](https://www.microsoft.com/en-gb/WindowsForBusiness/End-of-IE-support) we now support only IE 11, which is standards-compliant. However, it is courteous to still include this tag for any users who have not yet upgraded.

For more information, read this comprehensive [Stack Overflow article](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e).


### 2.6 Links to external CSS and JavaScript files

Link to external CSS and JavaScript files so that the files may be cached by your browser, saving bandwidth.

Do not embed `<style>` CSS or use inline JavaScript or `<script>` code (unless absolutely necessary).


#### Do not use `type`

In line with the HTML5 specification, there is no need to specify a `type` when including CSS and JavaScript files, as `text/css` and `text/javascript` are their respective defaults.

```
<!-- Do this -->
<link href="screen.css" rel="stylesheet">
<script src="file.js"></script>

<!-- Not this -->
<link type="text/css" rel="stylesheet" href="screen.css">
<script type="text/javascript" src="file.js"></script>
```




---

## 3. Element rules

Specific guidelines about certain HTML elements.


### 3.1 Address

Do not use the `<address>` element. Despite having been around since HTML3 in 1995, it is invariably used the wrong way.

According to the [W3C HTML specification](http://w3c.github.io/html/sections.html#the-address-element):

> The `address` element represents the contact information for its nearest `article` or `body` element ancestor. If that is the `body` element, then the contact information applies to the document as a whole.
> 
>The `address` element MUST not be used to represent arbitrary addresses (e.g., postal addresses), unless those addresses are in fact the relevant contact information. (The `p` element is the appropriate element for marking up postal addresses in general.)

Rather than causing confusion, simply do not use it.


### 3.2 Bold and strong

Remember that markup should be semantic: the elements used should also convey a layer of meaning. In HTML5:

* `<strong>` indicates strong importance, seriousness (a warning or cautionary notice), or urgency. ([WhatWG](https://html.spec.whatwg.org/multipage/semantics.html#the-strong-element))
* `<b>` indicates "a span of text to which attention is being drawn for utilitarian purposes without conveying any extra importance and with no implication of an alternate voice or mood, such as keywords in a document abstract, product names in a review, actionable words in interactive text-driven software, or an article lede." ([WhatWG](https://html.spec.whatwg.org/multipage/semantics.html#the-b-element))


### 3.3 Comments

Comments are your messages to other developers, as well as to yourself, if you come back to your code after several months working on something else.

Write comments as complete, grammatical sentences with an initial capital and a full-stop at the end.

As a rule, comment anything that isn't immediately obvious from the code alone. These could be explaining:

* the structure and/or role of a file;
* the thought process behind a way of doing things;
* the name of a digital pattern library pattern being used.

Keep comments up-to-date when code changes.

Comments MAY make their way into production environments.

Avoid writing closing tag comments, like `<!-- /.element -->`. This just adds to page load time. Plus, most editors have indentation guides and open/close tag highlighting.


### 3.4 Forms

* Lean towards radio or checkbox lists instead of select menus; the former are more accessible.
* Wrap radio and checkbox inputs and their text in `<label>`s. No need for `for` attributes here: the wrapping automatically associates the two.
* Form buttons SHOULD always include an explicit `type`. Use primary buttons for the `type="submit"` button and regular buttons for `type="button"`.
* The primary form button MUST come first in the DOM, especially for forms with multiple submit buttons.
* Input field placeholders are generally bad for accessibility. Do not hide text that would be useful to the user in a placeholder as it will disappear as soon as the user starts typing. For more guidance see [Placeholders in form fields are harmful](https://www.nngroup.com/articles/form-design-placeholders/).


### 3.5 Images

* All images used in `<img>` elements MUST be in either GIF, JPG, PNG or SVG formats.
* You MUST specify height and width attributes when using an `<img>` element. This improves page rendering speed as it allows the browser to understand the page layout without having to wait for the images to download to learn their dimensions.


#### alt text

All images MUST have `alt` attributes defined to describe the image. The description SHOULD be:

* Accurate;
* Succinct: typically no more than a few words, although a short sentence or two may be appropriate;
* Unique: do not provide the same information as the text within the context of the image.

Do not use phases like "Image of..." or "Graphic of...". It should be clear from the context that this is an image.


### 3.6 Italics and emphasis

Remember that markup SHOULD be semantic: the elements used SHOULD also convey a layer of meaning. In HTML5 

* `<em>` indicates _emphatic stress_, that is something you would pronounce differently. ([WhatWG](https://html.spec.whatwg.org/multipage/semantics.html#the-em-element))
* `<i>` indicates "a span of text in an alternate voice or mood, or otherwise offset from the normal prose in a manner indicating a different quality of text, such as a taxonomic designation, a technical term, an idiomatic phrase from another language, transliteration, a thought, or a ship name in Western texts." ([WhatWG](https://html.spec.whatwg.org/multipage/semantics.html#the-i-element))


### 3.7 Lists

List items MUST always be within `<ul>`, `<ol>`, or `<dl>` elements. Never use a set of `<div>` or `<p>` tags.

Although in HTML5 you may omit closing tags from certain elements such as list items, always close list items:

```
<!-- Do this -->
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>

<!-- Not this -->
<ul>
    <li>Item 1
    <li>Item 2
    <li>Item 3
</ul>
```


### 3.8 Tables

Tables MUST only be used to present tabular data; they MUST NOT be used for presentation.

Make use of `<thead>`, `<tfoot>`, `<tbody>`, and `<th>` tags (and `scope` attribute) when appropriate. (Note: `<tfoot>` goes above `<tbody>` for speed reasons. You want the browser to load the footer before a table full of data.)

```
<table summary="This is a chart of invoices for 2015.">
    <thead>
        <tr>
            <th scope="col">Table header 1</th>
            <th scope="col">Table header 2</th>
        </tr>
    </thead>
    <tfoot>
        <tr>
            <td>Table footer 1</td>
            <td>Table footer 2</td>
        </tr>
    </tfoot>
    <tbody>
        <tr>
            <td>Table data 1</td>
            <td>Table data 2</td>
        </tr>
    </tbody>
</table>
```


### 3.9 tor.com/element-index/) for advice on the best use of HTML5 elements.




---

## 4. Class and ID names

Guidance on class and ID names can be found in the CSS style guide. Here are a few basics:

* First two characters MUST be either letters, underscores or hyphens; thereafter, any number of underscores, hyphens, letters or numbers.
* Do not use asterisks (`*`) which are universal selectors; forward slashes (`/`) or backward slashes (`\`) are not accepted.
* Use [BEM - Block Element Modifier](http://getbem.com/)-style class and ID names.
* Class and ID names MUST be lowercase. Do not use camelCase.
* Delimit words with a hyphen (`-`), e.g. `page-head`.
* Separate multiple values in a class attribute with two spaces; this makes it much easier to read, e.g. `<button class="btn`  `btn-link">`.


### 4.1 Standard class names

Where possible prefer to use standard class names, for example when using [Bootstrap](http://getbootstrap.com/) components.


### 4.2 Microformats

"Designed for humans first and machines second, microformats are a set of simple, open data formats built upon existing and widely adopted standards. Instead of throwing away what works today, microformats intend to solve simpler problems first by adapting to current behaviors and usage patterns."

For the following content types, consider using [Microformat 2](http://microformats.org/wiki/microformats2) class name standards, especially:

* [h-adr](http://microformats.org/wiki/h-adr) is a simple, open format for publishing structured locations such as addresses, physical and/or postal.
* [h-card](http://microformats.org/wiki/h-card) is a simple, open format for publishing people and organisations on the web.
* [h-entry](http://microformats.org/wiki/h-entry) is a simple, open format for episodic or datestamped content on the web. h-entry is often used with content intended to be syndicated, e.g. blog posts. 
* [h-event](http://microformats.org/wiki/h-event) is a simple, open format for publishing events on the web. 
* [h-geo](http://microformats.org/wiki/h-geo) is a simple, open format for publishing [WGS84](https://en.wikipedia.org/wiki/World_Geodetic_System) geographic coordinates.




---

## 5. Avoid JavaScript-generated markup

Unless you are using a JavaScript templating engine such as [Handlebars]](http://handlebarsjs.com/), do not 'hide' markup in JavaScript files. It makes content harder to find, harder to edit and diminishes performance.

If you must, in the document into which you are injecting code prefix the section ID with `js-` so that it is clear that the content is generated via JavaScript, e.g.

```
<div id="js-generated-message"></div>
```

See CSS style guide for more on JavaScript hooks.



---

## 6. Error pages

Error pages MUST be built such that they require no external dependency on anything whatsoever. That means static HTML with inline CSS and base64-encoded images.

The following are banned from every error page:

* All `<script>` tags with a `src` attribute.
* All JavaScript that loads external data.
* All `<link>` tags.
* All `<img>` tags with a `src` pointing to a URL.


### 6.1 Error templates

We use error pages for very specific purposes.

* **403** — Access denied/forbidden.
Requests that require authentication may return 404 Not Found, instead of 403 Forbidden, in some places. This is to prevent the accidental leakage of private information to unauthorized users. See GitHub [API Authentication](https://developer.github.com/v3/#authentication).

* **404** — Not found.
See Github [404](https://github.com/404.html) and [404-pages](https://github.com/404-pages.html)

* **410** — Feature gone.
See Github [410](https://github.com/410.html). Not sure we need this one.

* **500** — An exception occurred and we couldn't recover.
See Github [500](https://github.com/500.html)

* **502** — The page likely timed out.
See Github [502](https://github.com/502.html)

* **503** — We are having a bad problem and the app server will not talk to us.
See Github [503](https://github.com/503.html)

* **maintenance** — For the rare case we have to take the website down to perform maintenance. See Github [maintenance](https://github.com/maintenance.html). May need this for other systems, e.g. Pure.




---

## References

The initial version of this style guide was based on [Github's HTML style guide](https://github.com/styleguide/templates), with inspiration too from [MDO's code guide](http://mdo.github.io/code-guide/).

Boolean attributes, Lean markup, Forms and Tables taken from [PrimerCSS](http://primercss.io/guidelines/).
