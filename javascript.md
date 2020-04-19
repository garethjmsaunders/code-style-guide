# JavaScript style guide

version 1.0.0
Last updated: Thursday 21 July 2016

The terms MUST, MUST NOT, SHOULD, SHOULD NOT, and MAY are used in this document with the meanings found in [RFC 2119: Key words for use in RFCs to indicate requirement levels](https://www.ietf.org/rfc/rfc2119.txt).

<!-- MarkdownTOC depth=4 -->

- [1. Introduction](#1-introduction)
- [2. File format](#2-file-format)
    - [2.1 Unicode \(UTF-8\)](#21-unicode-utf-8)
    - [2.2 Use LF \(Unix\) line endings](#22-use-lf-unix-line-endings)
- [3. General formatting](#3-general-formatting)
    - [3.1 Indentation](#31-indentation)
    - [3.2 Line width \(80 characters\)](#32-line-width-80-characters)
    - [3.3 One statement per line](#33-one-statement-per-line)
    - [3.4 Semicolons](#34-semicolons)
    - [3.5 Parentheses](#35-parentheses)
    - [3.6 Brace style](#36-brace-style)
    - [3.7 Single and double quotation marks](#37-single-and-double-quotation-marks)
- [4. Spaces](#4-spaces)
    - [4.1 Remove trailing spaces](#41-remove-trailing-spaces)
    - [4.2 Array items](#42-array-items)
    - [4.3 Blocks](#43-blocks)
    - [4.4 Functions](#44-functions)
    - [4.5 Logical comparisons](#45-logical-comparisons)
    - [4.6 String concatenation](#46-string-concatenation)
- [5. Comments](#5-comments)
    - [5.1 JSDoc](#51-jsdoc)
    - [5.2 Single-line comments](#52-single-line-comments)
    - [5.3 Magic numbers](#53-magic-numbers)
- [6 Naming conventions](#6-naming-conventions)
    - [6.1 Classes and methods](#61-classes-and-methods)
        - [Class names](#class-names)
        - [Class method names](#class-method-names)
    - [6.2 Constant names](#62-constant-names)
    - [6.3 Enumerated types \(enum\)](#63-enumerated-types-enum)
    - [6.4 Filenames](#64-filenames)
    - [6.5 Function names](#65-function-names)
    - [6.6 Variable names](#66-variable-names)
- [7. Language specifics](#7-language-specifics)
    - [7.1 Arrays and objects](#71-arrays-and-objects)
    - [7.2 Avoid mixing technologies](#72-avoid-mixing-technologies)
    - [7.3 Continue](#73-continue)
    - [7.4 Eval](#74-eval)
    - [7.5 Function arguments](#75-function-arguments)
    - [7.6 JavaScript Object Notation \(JSON\)](#76-javascript-object-notation-json)
    - [7.7 jQuery](#77-jquery)
    - [7.8 Quoting strings](#78-quoting-strings)
    - [7.9 Ternary operators](#79-ternary-operators)
    - [7.10 Variable declarations](#710-variable-declarations)
    - [7.11 With](#711-with)
- [8. JSLint configuration](#8-jslint-configuration)
- [Further reading](#further-reading)

<!-- /MarkdownTOC -->







## 1. Introduction

JavaScript code SHOULD pass [JSLint](http://www.jslint.com/). JSLint defines an opinionated subset of JavaScript with a very strict definition of acceptable style.




---

## 2. File format

### 2.1 Unicode (UTF-8)

* Files MUST be saved with Unicode (UTF-8) encoding.
* Files MUST NOT be saved with the byte-order mark (UTF-8 with BOM).


### 2.2 Use LF (Unix) line endings

Lines MUST end with a single, Unix-style line feed (LF) character.

Do not use carriage returns (CR) as used by Apple OS, or carriage return/line feed (CRLF) as used by Windows.

Ensure that your text editor is set up to save files with Unix-style line breaks. For example, in Sublime Text you can add the following to your user settings:

```
    "default_line_ending": "LF",
```




---
## 3. General formatting

### 3.1 Indentation

JavaScript parsers do not care about indentation, it is solely used for the convenience of human readers. Indentation should be used to enhance readability of the source code.

* Do not indent code unnecessarily.
* Indent on purpose.
* Indent consistently.

Code indentation should always reflect the logical structure of the code.

* Use only spaces, and indent FOUR (4) spaces at a time. Spaces are the only way to guarantee code renders the same in any environment.
* Use spaces for indentation. Do not use tabs in your code. You should set your editor to emit spaces when you hit the tab key.
* Nested elements SHOULD be indented once (four spaces).


### 3.2 Line width (80 characters)

Where possible, limit JavaScript files' width to 80 characters. Reasons for this include:

* the ability to have multiple files open side by side;
* viewing JavaScript on sites like GitHub, or in a terminal window;
* providing a comfortable line length for comments.

Do not worry about unavoidable exceptions to this rule, such as URLs.


### 3.3 One statement per line

Statements SHOULD always be written one per line; do not combine statements on one line.

One statement per line makes code easier to read and compare using a diff tool.

At best multiple, combined statements makes code look messy and confusing, at worst it can contribute to the insertion of errors or missing something when reviewing code.

There MAY be some exceptions, such as `switch` statements, but readability and ease of debugging and code maintenance should take precidence over strict adherence to this rule, e.g.

```
switch (new Date().getDay()) {
    case 0:   day = "Sunday";        break;
    case 1:   day = "Monday";        break;
    case 2:   day = "Tuesday";       break;
    case 3:   day = "Wednesday";     break;
    case 4:   day = "Thursday";      break;
    case 5:   day = "Friday";        break;
    case 6:   day = "Saturday";      break;
}
```


### 3.4 Semicolons

JavaScript uses semicolons (`;`) to mark the end of a statement; it is required on these statements:

* `break`
* `continue`
* `debugger`
* `do`
* `empty`
* `expression`
* `for` (separating control clauses)
* `return`
* `throw`
* `var`

Every statement MUST be followed by a semicolon except for

* `for`
* `function`
* `if`
* `switch`
* `try`
* `while`

You MUST NOT rely on automatic semicolon insertion.

A code block, enclosed in braces `{...}` is not a statement, it is a group of statements. Each statement within the code block MUST be terminated with a semicolon, but the code block itself is NOT terminated with a semicolon.


### 3.5 Parentheses

Parentheses SHOULD only be used where they are required. Additional parentheses may be used to clarify groupings in complex conditional constructs, but knowing operator precedence should eliminate their necessity.

When calling class constructors with no arguments, always include parentheses: The constructors are functions, so constructor calls need to look like function calls.

Never use parentheses for unary operators such as `delete`, `typeof` and `void` or after keywords such as `return`, `throw` as well as others (`case`, `in` or `new`).


### 3.6 Brace style

You MUST use 1TBS (one true brace style) to indent braces, e.g.

```
if ( condition ) {
    action1();
    action2();
} else if ( condition2 && condition3 ) {
    action3();
    action4();
} else {
    defaultaction();
}
```

Braces MUST always be used, even when they are not required. This means that single-statement inline control structures MUST NOT be used.


### 3.7 Single and double quotation marks

Use single quotes (`'`) for symbols, character constants, and internal strings such as property names.

Use double quotes (`"`) for strings that will be exported from the program, such as HTML fragments, URLs, or messages to the user.




---

## 4. Spaces

Spaces MUST always be inserted after commas, and on both sides of logical, comparison, string and assignment operators.


### 4.1 Remove trailing spaces

You MUST remove trailing whitespace at the end of each line of code.


### 4.2 Array items

Spaces MUST always be inserted after commas.

When referring to array items, one space MUST be inserted around the index ONLY if it is a variable.

```
x = [ 1, 2, 3 ];

x = foo['bar'];
x = foo[0];
x = foo[ bar ];
```


### 4.3 Blocks

Spaces MUST be inserted on both sides of the opening and closing parenthesis of `if`, `elseif`, `foreach`, `for`, and `switch` blocks.

```
for ( expr1; expr2; expr3 ) {
    ... 
}

let iterable = [10, 20, 30];
for ( let value of iterable ) {
  console.log(value);
}

if ( x < 45 ) {
    else if ( x > 45 ) {
}

switch ( $i ) { 
    ... 
}
```


### 4.4 Functions

When defining a function:

```
function my_function( parameter1, parameter2, parameter3 ) {
    ...
}
```


When calling a function:

```
my_function( parameter1, parameter2, parameter3 );
```


### 4.5 Logical comparisons

When performing logical comparisons:

```
if ( ! $foo ) { 
    ...
}

x == 23;
baz === '-5';
foo && bar;
! foo;

```


### 4.6 String concatenation

When concatenating strings using the `+` operator, a space MUST be inserted on both sides of the operator to improve readability.

```
institution = "University";
town = "St Andrews";
name = institution + " of " + town;
```




---
## 5. Comments

In general, code needs more comments; comment your code prolifically.

Comments are your messages to other developers (and yourself, if you come back to your code after several months working on something else).

You SHOULD comment anything that isn't immediately obvious from the code alone. These could be explaining:

* the structure and/or role of a file;
* the goal of a function or class;
* the idea behind a 'magic number';
* the reason for a statement;
* the order of items in an array or constant;
* the thought process behind a way of doing things.

In situations where it would be useful for a developer to know exactly how a JavaScript snippet applies to some HTML, you MAY include a snippet of HTML in a comment.

If you find an answer online (for example, on Stack Overflow, or a blog) then you SHOULD add the link to a comment so future developers know what's up.

You MUST keep comments up-to-date when code changes.

Comments SHOULD NOT make their way into production environments. Comments are for development not production.

All JavaScript SHOULD be minified, stripping out comments, before being deployed.


### 5.1 JSDoc

Multi-line comments SHOULD use [jSDoc](http://usejsdoc.org/)-style comments.

```
/**
 * Comment heading
 * Comment about what the following piece of code is for and why.
 *
 * @version 1.2.0 2016-07-04
 * @author Gareth J M Saunders <gjms1@st-andrews.ac.uk>
 * @copyright 2016
 * @license http://opensource.org/licenses/gpl-license.php, GNU Public License
 * @since 1.0.9
 */
```

Comments SHOULD be written as complete, grammatical sentences with an initial capital and a full-stop at the end.

All [JSDoc block tags](http://usejsdoc.org/) are available for use. Pay particular attention to block tags used to comment on classes, enums, events, functions, global objects, types, etc.


### 5.2 Single-line comments

Use single line comments within code, leaving a blank line between large comment blocks and code.

```
// Split a string into an array of substrings.
var str = "How are you doing today?";
var res = str.split(" ");

// A longer comment that needs more detail
// on what is occurring and why can use multiple single-line comments.

document.getElementById("demo").innerHTML = "Hello World.";
```


### 5.3 Magic numbers

"Magic number" is an old school programming term for an unnamed numerical constant. Basically, it's just a random number that happens to _just work_™ yet is not tied to any logical explanation.

Needless to say, magic numbers are a plague and should be avoided at all costs. When you cannot manage to find a reasonable explanation for why a number works, add an extensive comment explaining how you got there and why you think it works. Admitting you don’t know why something works is still more helpful to the next developer than them having to figure out what's going on from scratch.

---

## 6 Naming conventions

### 6.1 Classes and methods

#### Class names

Regex pattern: `(([A-Z]{1}[a-zA-Z]*)_*)+`

* Class names MUST always start with an uppercase letter.
* Multiple words MUST be separated with an underscore.
* Subsequent words MUST also begin with an uppercase letter.
* Abbreviations MUST be written in all-uppercase.

```
class Class_Name
class Longer_Class_Name
class WP_HTTP
```


#### Class method names

Regex pattern: `(([a-z]+)_*)+`

A method is a function used in the context of a class/object.

* Class methods MUST be entirely lowercase
* Class methods SHOULD be named to clearly indicate their function, preferably beginning with a verb.
* Multiple words MUST be separated with an underscore.

```
function get_file_properties()
```


### 6.2 Constant names

Regex pattern: `(([A-Z]+)_*)+`

Constants MUST only contain UPPERCASE letters, use underscore separators, and be reasonably named to indicate their purpose and contents. Numbers SHOULD NOT be used in constants.

```
const MIN_VALUE = 0.0;
const MAX_VALUE = 1.0;
```


### 6.3 Enumerated types (enum)

Regex pattern: `(([a-z]+)_*)+`

An enumerated type (also called enumeration or enum) is a data type that consists of a set of named values called elements, members or enumerators of the type.

The enumerator names are usually identifiers that behave as constants in the language. A variable that has been declared as having an enumerated type can be assigned any of the enumerators as a value.

In other words, an enum restricts variables to one value from a predefined set of constants. For example,

```
var WeekDay = { MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY };
```

* Enums MUST be entirely lowercase
* Enums SHOULD be named to clearly indicate their function, preferably beginning with a verb.
* Multiple words MUST be separated with an underscore.


### 6.4 Filenames

Regex pattern: `(([a-z])+-*)+(.inc)*.js

* Files SHOULD be named descriptively.
* Files MUST be named using only lowercase letters.
* Words MUST be separated by hyphens.

```
filename.js
my-plugin-name.js
helper-class-library.js
```


### 6.5 Function names

Regex pattern: `(([a-z])+_*)+`

Function MUST contain only lowercase letters, use underscore separators, and be reasonably named to indicate their purpose and contents.

```
function write_message() {
    ...
}

function greet_fullname( first_name, last_name ) {
    ...
}
```



### 6.6 Variable names

Regex pattern: `\$(([a-z])+_*)+`

Variable names MUST contain only lowercase letters, use underscore separators, and be reasonably named to indicate their purpose and contents. Very short, non-word variables should only used for iterations in `for()` loops.

```
for ( var j = 0; j < 0; j++ ) { ... }
var str = '';
var buffer = '';
var group_id = 0;
var last_city = 'St Andrews';
```



---

## 7. Language specifics

### 7.1 Arrays and objects

* Use `[]` instead of `new Array()`.
* Use `{}` instead of `new Object()`.


### 7.2 Avoid mixing technologies

While it is possible to create everything you need in a document using JavaScript and the DOM it is not necessarily the most effective way of doing so. We could write CSS inline on a DOM element, but it would be far better to apply a class and let the styling be handled in the style sheet.

This
```
var f = document.getElementById('mainform');
var inputs = f.getElementsByTagName('input');
for(var i=0,j=inputs.length;i<j;i++){
  if(inputs[i].className === 'mandatory' &&
     inputs[i].value === ''){
    inputs[i].className += ' error';
  }
}
```

Not this
```
var f = document.getElementById('mainform');
var inputs = f.getElementsByTagName('input');
for(var i=0,j=inputs.length;i<j;i++){
    if(inputs[i].className === 'mandatory' &&
    inputs[i].value === ''){
    inputs[i].style.borderColor = '#f00';
    inputs[i].style.borderStyle = 'solid';
    inputs[i].style.borderWidth = '1px';
    }
}
```


### 7.3 Continue

Avoid use of the `continue` statement as it tends to obscure the control flow of a function.


### 7.4 Eval

You MUST NOT use `eval`.

`eval` is probably the most misused feature of JavaScript, because there is almost always a better way to achieve the same thing.

See the [JSLint article](https://jslinterrors.com/eval-is-evil) for more information.


### 7.5 Function arguments

Where possible, all function arguments SHOULD be listed on the same line.

If doing so would exceed the 80-column limit, the arguments MUST be line-wrapped in a readable way. To save space, you may wrap as close to 80 as possible, or put each argument on its own line to enhance readability. The indentation may be either four spaces, or aligned to the parenthesis.

Either of these is acceptable:

```
// Indent arguments by four spaces
function my_function( parameter1, parameter2, parameter3, 
    parameter4, parameter5 ) {
    ...
}

// Align arguments with first row
function my_function( parameter1, parameter2, parameter3, 
                      parameter4, parameter5 ) {
    ...
}
```


### 7.6 JavaScript Object Notation (JSON)

If manually creating a JavaScript Object Notation (JSON) file use the following layout:

```
{"employees":[
    { "firstName":"John",  "lastName":"Burnet" },
    { "firstName":"Agnes", "lastName":"Blackadder" },
    { "firstName":"David", "lastName":"Russell" }
]}
```

* Records MUST be indented with FOUR (4) spaces.
* You MAY align name:value pairs to make the lines easier to read.
* Records SHOULD be listed on a single line. If lines exceed 80 characters then split across multiple lines, e.g.

```
{"employees":[
    { "firstName":  "John",
      "lastName":   "Burnet",
      "employeeID": "0001"
    },
    { "firstName":  "Agnes",
      "lastName":   "Blackadder",
      "employeeID": "0002"
    },
    { "firstName":  "David",
      "lastName":   "Russell",
      "employeeID": "0003" }
]}
```

### 7.7 jQuery

When creating or extending jQuery plugins the conventions recommended by the [jQuery JavaScript style guide](https://contribute.jquery.org/style-guide/js/) SHOULD take precedence over the guidelines contained within this style guide, particularly if the plugin is to be submitted to the jQuery plugin registry.

### 7.8 Quoting strings

You SHOULD always use single-quotes (`'`) rather than double-quotes (`"`). This is helpful when creating strings that include HTML:

```
var msg = 'This is some <a href="#url">HTML</a>';
```


### 7.9 Ternary operators

A ternary operator is a conditional operator that uses the syntax:

```
(condition) ? (if_true) : (if_false)
```

* Ternary operators SHOULD only be used for simple evaluations.
* Ternary operators MUST NOT be used for complex or nested conditionals.
* The complete statement SHOULD fit onto a single 80-character line; if the line exceeds 80-characters then split and indent across multiple lines, prefixing the true and false evaluations with the `?` and `:` operators.

```
(condition) 
    ? (if_true) 
    : (if_false)
```


### 7.10 Variable declarations

* All variables MUST be declared before being used.
* Implied global variables MUST NOT be used.
* Use of global variables SHOULD be minimized.

Listed variables in alphabetical order, if possible and comment each.

```
var currentStudentID;   // This is taken from the SITS student record
var graduationYear;     // Calculated from start date
var orientation;        // options: landscape or portrait
```


### 7.11 With

The `with` statement MUST not be used.

See [with Statement Considered Harmful](http://yuiblog.com/blog/2006/04/11/with-statement-considered-harmful/) on the Yahoo! UI blog.




---


## 8. JSLint configuration

The pattern library provides a JSLint config file that implements many of these rules and can be used to ensure that your code matches our work.

---




## Further reading

For more in-depth treatment, see the following:

* [Code conventions for the JavaScript programming language](http://javascript.crockford.com/code.html) by Douglas Crockford
* [JSLint](http://www.jslint.com/help.html)
* [Google JavaScript style guide](https://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
