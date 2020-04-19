# PHP style guide

Version 1.0.0
Last updated: Wednesday 20 July 2016

The terms MUST, MUST NOT, SHOULD, SHOULD NOT, and MAY are used in this document with the meanings found in [RFC 2119: Key words for use in RFCs to indicate requirement levels](https://www.ietf.org/rfc/rfc2119.txt).


<!-- MarkdownTOC -->

- [1. Introduction](#1-introduction)
- [2. File format](#2-file-format)
    - [2.1 Unicode \(UTF-8\)](#21-unicode-utf-8)
    - [2.2 Use LF \(Unix\) line endings](#22-use-lf-unix-line-endings)
- [3. No shorthand PHP tags](#3-no-shorthand-php-tags)
- [4. PHP closing tag](#4-php-closing-tag)
- [5. General formatting](#5-general-formatting)
    - [5.1 Indentation](#51-indentation)
    - [5.2 Line width \(80 characters\)](#52-line-width-80-characters)
    - [5.3 One statement per line](#53-one-statement-per-line)
    - [5.4 Semicolons](#54-semicolons)
    - [5.5 Parentheses](#55-parentheses)
    - [5.6 Brace style](#56-brace-style)
    - [5.7 Single and double quotation marks](#57-single-and-double-quotation-marks)
- [6. Spaces](#6-spaces)
    - [6.1 Whitespace](#61-whitespace)
    - [6.2 Remove trailing spaces](#62-remove-trailing-spaces)
    - [6.3 Array items](#63-array-items)
    - [6.4 Blocks](#64-blocks)
    - [6.5 Functions](#65-functions)
    - [6.6 Logical comparisons](#66-logical-comparisons)
    - [6.7 String concatenation](#67-string-concatenation)
    - [6.8 Type casting](#68-type-casting)
- [7. Comments](#7-comments)
    - [7.1 DocBlock](#71-docblock)
        - [@package, @subpackage and @category](#package-subpackage-and-category)
        - [@version](#version)
        - [@since](#since)
    - [7.2 Class, method, and property declarations](#72-class-method-and-property-declarations)
        - [Classes](#classes)
        - [Methods](#methods)
        - [Property declarations](#property-declarations)
    - [7.3 Single-line comments](#73-single-line-comments)
    - [7.4 Magic numbers](#74-magic-numbers)
- [8. Naming conventions](#8-naming-conventions)
    - [8.1 Classes and methods](#81-classes-and-methods)
        - [Class names](#class-names)
        - [Class method names](#class-method-names)
    - [8.2 Constant names](#82-constant-names)
    - [8.3 Filenames](#83-filenames)
    - [8.4 Function names](#84-function-names)
    - [8.5 Variable names](#85-variable-names)
- [9. Language specifics](#9-language-specifics)
    - [9.1 Arrays](#91-arrays)
        - [Numerically-indexed arrays](#numerically-indexed-arrays)
        - [Associative arrays](#associative-arrays)
    - [9.2 elseif, not else if](#92-elseif-not-else-if)
    - [9.3 Logical operators](#93-logical-operators)
    - [9.4 Regular expressions](#94-regular-expressions)
    - [9.5 Ternary operator](#95-ternary-operator)
    - [9.6 TRUE, FALSE, and NULL](#96-true-false-and-null)
    - [9.7 Yoda conditions](#97-yoda-conditions)
- [10. Security](#10-security)
    - [10.1 Debug code](#101-debug-code)
- [Further reading](#further-reading)

<!-- /MarkdownTOC -->




---

## 1. Introduction

This style guide is based mainly around the assumption that we will be writing simple code and/or WordPress development, so it is based heavily on the [WordPress PHP coding standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/php/).

The most important thing when writing any code, particularly when collaborating on code within teams, is code consistency, readability, and comprehensibility. Remember that the only people actually reading your code are other humans: computers simply interpret it.

If you use another framework (such as CodeIgniter or Symphony) it is more important to write your code consistently with the parent framework than follow this guide to the letter.




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

## 3. No shorthand PHP tags

You must NEVER use shorthand PHP start tags; always choose full PHP tags.

```
// Correct
<?php ... ?>
<?php echo $var; ?>


// Incorrect
<? ... ?>
<?= $var ?>
```




---

## 4. PHP closing tag

The PHP closing tag (`?>`) is optional for the PHP parser. However, if used any whitespace following the closing tag can cause unexpected output, errors, or blank pages (if errors are suppressed).

For files that contain only PHP code you MUST omit the PHP closing tag. Remove any trailing whitespace and end the file with a single empty line.

```
// Wrong
<?php
    example () {
        // code        
    }
?>

// Correct
<?php
    example () {
        // code        
    }

```




---

## 5. General formatting

### 5.1 Indentation

PHP parsers do not care about indentation, it is solely used for the convenience of human readers. Indentation should be used to enhance readability of the source code.

* Do not indent code unnecessarily.
* Indent on purpose.
* Indent consistently.

Code indentation should always reflect the logical structure of the code.

* Use soft tabs with FOUR spaces. Spaces are the only way to guarantee code renders the same in any environment.
* Nested elements SHOULD be indented once (four spaces).


### 5.2 Line width (80 characters)

Where possible, limit PHP files' width to 80 characters. Reasons for this include:

* the ability to have multiple files open side by side;
* viewing PHP on sites like GitHub, or in a terminal window;
* providing a comfortable line length for comments.

Do not worry about unavoidable exceptions to this rule, such as URLs, or within a `heredoc`.


### 5.3 One statement per line

Statements SHOULD always be written one per line; do not combine statements on one line.

One statement per line makes code easier to read and compare using a diff tool.

At best multiple, combined statements makes code look messy and confusing, at worst it can contribute to the insertion of errors or missing something when reviewing code.

There MAY be some exceptions, such as `switch` statements, but readability and ease of debugging and code maintenance should take precidence over strict adherence to this rule, e.g.

```
<?php
switch ($_REQUEST['tag']) {
    default:   $string=FALSE;                     break; 
    case 1:    $string='first choice';            break; 
    case 2:    $string='another possible choice'; break; 
    case 3:    $string='maybe something else';    break; 
    case 4:    $string='yet another idea';        break; 
}
```


### 5.4 Semicolons

PHP generally uses semicolons (`;`) to mark the end of a statement. However, if the PHP closing tag is on the same line after a statement, the semicolon is optional and should not be used.

A code block, enclosed in braces `{...}` is not a statement, it is a group of statements. Each statement within the code block MUST be terminated with a semicolon, but the code block itself is NOT terminated with a semicolon.

<small>Source: MIT Sloan School of Management</small>


### 5.5 Parentheses

Parentheses SHOULD only be used where they are required. Additional parentheses may be used to clarify groupings in complex conditional constructs, but knowing operator precedence should eliminate their necessity.

Parentheses SHOULD NOT be used when using language constructs such as `echo`, `print`, `include`, or `require`. These are not functions and don't require parentheses around their parameters.

When calling class constructors with no arguments, always include parentheses: The constructors are functions, so constructor calls need to look like function calls.

<small>Source: MIT Sloan School of Management</small>


### 5.6 Brace style

You MUST use 1TBS (one true brace style) to indent braces, e.g.

```
if ( condition ) {
    action1();
    action2();
} elseif ( condition2 && condition3 ) {
    action3();
    action4();
} else {
    defaultaction();
}
```

Braces MUST always be used, even when they are not required. This means that single-statement inline control structures MUST NOT be used.

You MAY use alternative syntax for control structures (e.g. `if/endif`, `while/endwhile`) especially in your templates where PHP code is embedded within HTML, for instance in WordPress:

```
<?php if ( have_posts() ) : ?>
    <div class="hfeed">
        <?php while ( have_posts() ) : the_post(); ?>
            <article id="post-<?php the_ID() ?>" class="<?php post_class() ?>">
                <!-- ... -->
            </article>
        <?php endwhile; ?>
    </div>
<?php endif; ?>
```

<small>Source: WordPress</small>


### 5.7 Single and double quotation marks

Use single and double quotes when appropriate. If you’re not evaluating anything in the string, you SHOULD use single quotes.

You SHOULD almost never have to escape quotes in a string, because you can just alternate your quoting style, like so:

```
echo '<a href="/static/link" title="Yeah yeah!">Link name</a>';
echo "<a href='$link' title='$linktitle'>$linkname</a>";
```

In WordPress, text that goes into attributes should be run through `esc_attr()` so that single or double quotes do not end the attribute value and invalidate the HTML and cause a security issue.

<small>Source: WordPress</small>




---

## 6. Spaces

Spaces MUST always be inserted after commas, and on both sides of logical, comparison, string and assignment operators.


### 6.1 Whitespace

There MUST NOT be any whitespace before the opening PHP tag.


### 6.2 Remove trailing spaces

You MUST remove trailing whitespace at the end of each line of code.


### 6.3 Array items

Spaces MUST always be inserted after commas.

When referring to array items, one space MUST be inserted around the index ONLY if it is a variable.

```
x = array( 1, 2, 3 );  // Note no space after array keyword

$x = $foo['bar'];
$x = $foo[0];
$x = $foo[ $bar ];
```


### 6.4 Blocks

Spaces MUST be inserted on both sides of the opening and closing parenthesis of `if`, `elseif`, `foreach`, `for`, and `switch` blocks.

```
for ( expr1; expr2; expr3 ) {
    ... 
}

foreach ( $foo as $bar ) { 
    ... 
}

if ( x < 45 ) {
    elseif ( x > 45 ) {
}

switch ( $i ) { 
    ... 
}
```


### 6.5 Functions

When defining a function:

```
function my_function( $param1 = 'foo', $param2 = 'bar' ) {
    ...
}
```


When calling a function:

```
my_function( $param1, func_param( $param2 ) );
```


### 6.6 Logical comparisons

When performing logical comparisons:

```
if ( ! $foo ) { 
    ...
}

x == 23;
$baz === '-5';
$term .= 'X';
foo && bar;
! foo;

```


### 6.7 String concatenation

When concatenating strings using the `.` operator, a space MUST be inserted on both sides of the operator to improve readability.

```
$example = 'University' . ' of ' . 'St Andrews';
```


### 6.8 Type casting

When type casting:

```
foreach ( (array) $foo as $bar ) { 
    ...
}

$foo = (boolean) $bar;
```
 
<small>Source: WordPress</small>




---

## 7. Comments

In general, code needs more comments; comment your code prolifically.

Comments SHOULD be written as complete, grammatical sentences with an initial capital and a full-stop at the end.

You SHOULD comment anything that isn't immediately obvious from the code alone. These could be explaining:

* the structure and/or role of a file;
* the goal of a block of code;
* the idea behind a 'magic number';
* the thought process behind a way of doing things.

In situations where it would be useful for a developer to know exactly how a block of code applies to some HTML, you MAY include a snippet of HTML in a comment.

If you find an answer online (for example, on Stack Overflow, or a blog) then you SHOULD add the link to a comment so future developers know what's up.

You MUST keep comments up-to-date when code changes.

Comments MAY make their way into production environments as they are ignored when parsed.


### 7.1 DocBlock

Multi-line comments SHOULD use [phpDocumentor](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_phpDocumentor.pkg.html)-style comments.

```
/**
 * Comment heading
 * Comment about what the following piece of code is for and why.
 *
 * @package SomePackage name
 * @subpackage SubPackage name
 * @category Category name
 * @version 1.2.0 2016-07-04
 * @author Gareth J M Saunders <gjms1@st-andrews.ac.uk>
 * @copyright 2016
 * @license http://opensource.org/licenses/gpl-license.php, GNU Public License
 * @since 1.0.9
 */
```

Comments SHOULD be written as complete, grammatical sentences with an initial capital and a full-stop at the end.

All [phpDocumentor tags](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.pkg.html) are available but pay special attention to @package, @subpackage and @category, @version and @since.


#### @package, @subpackage and @category

Packages, subpackages and categories are used to help you logically group related elements.

* [@package](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.package.pkg.html) groups the class or elements in the file into a "package" in the documentation.
* [@subpackage](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.subpackage.pkg.html) groupings inside of a package, `@package` tag must also be present.
* [@category](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.category.pkg.html) organizes groups of packages.


```
/**
 * Class Class_Name
 * Class-level DocBlock example.
 * @package packageName
 * @subpackage singleWordName
 * @category categoryName
 */
```


#### @version

[@version](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.version.pkg.html) MUST be used on modules and elements to show the current revision. Use version numbering guidelines from [semantic versioning](http://semver.org/), which employs a MAJOR.MINOR.PATCH format.

```
@version 1.2.0]
```

You MAY also append a date after the version number.

```
@version 1.2.0 2016-07-04
```


#### @since

[@since](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_tags.since.pkg.html) MAY be used on modules and elements to show in which revision they were first implemented. Example:

```
@since 1.3.0
```


### 7.2 Class, method, and property declarations

You SHOULD use [DocBlock](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/phpDocumentor/tutorial_phpDocumentor.howto.pkg.html#basics.docblock) style comments before class, method, and property declarations. Some IDEs use these comments to infer information about the code.


#### Classes
```
/**
* Super Class
* Lorem ipsum dolor sit amet, consectetur adipisicing elit. Similique 
* veniam earum ipsa eaque doloremque tenetur commodi dolor molestias 
* non voluptatum sint minus quam quis culpa, praesentium distinctio id, 
* saepe natus!
*
* @package Package Name
* @subpackage Subpackage
* @category Category
* @author Author name
* @link http://example.com
* /
class Super_Class { ... }
```


#### Methods
```
/**
* Encodes string for use in XML 
*
* @param string $str Input string
* @return string
* /
function xml_encode($str) { ... }
```


#### Property declarations
```
/**
 * Data for class manipulation
 *
 * @var array
 */
public $data = array();
```


### 7.3 Single-line comments

Use single line comments within code, leaving a blank line between large comment blocks and code.

```
// Break up the string by new lines
$parts = explode("\n", $str);

// A longer comment that needs more detail
// on what is occurring and why can use multiple single-line comments.

$parts = $this -> foo($parts);
```


### 7.4 Magic numbers

"Magic number" is an old school programming term for an unnamed numerical constant. Basically, it's just a random number that happens to _just work_™ yet is not tied to any logical explanation.

Needless to say, magic numbers are a plague and should be avoided at all costs. When you cannot manage to find a reasonable explanation for why a number works, add an extensive comment explaining how you got there and why you think it works. Admitting you don’t know why something works is still more helpful to the next developer than them having to figure out what's going on from scratch.




---

## 8. Naming conventions

### 8.1 Classes and methods

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


### 8.2 Constant names

Regex pattern: `(([A-Z]+)_*)+`

Constants should only contain UPPERCASE letters, use underscore separators, and be reasonably named to indicate their purpose and contents. Numbers SHOULD NOT be used in constants.

```
define('MIN_VALUE', '0.0');
define('MAX_VALUE', '1.0');

class Constants {
  const MIN_VALUE = 0.0;      // RIGHT - Works INSIDE of a class definition.
  const MAX_VALUE = 1.0;      // RIGHT - Works INSIDE of a class definition.
}
```


### 8.3 Filenames

Regex pattern: `(([a-z])+-*)+(.inc)*.php`

Following the WordPress convention:

* Files SHOULD be named descriptively using lowercase letters.
* Words MUST be separated by hyphens.
* Filenames MUST never end with `.inc`. If you use an included file use a double suffix: `.inc.php`.

```
filename.php
my-plugin-name.php
helper-class-library.inc.php
```

Class file filenames should be based on the class name with `class-` prepended and the underscores in the class name replaced with hyphens, for example `WP_Error` becomes:

```
class-wp-error.php
```


### 8.4 Function names

Regex pattern: `(([a-z])+_*)+`

Function MUST contain only lowercase letters, use underscore separators, and be reasonably named to indicate their purpose and contents.

```
function write_message() {
    echo 'Hello world!';
}

function greet_fullname( $first_name, $last_name ) {
    echo "Hello $first_name $last_name";
}
```

### 8.5 Variable names

Regex pattern: `\$(([a-z])+_*)+`

Variable names MUST contain only lowercase letters, use underscore separators, and be reasonably named to indicate their purpose and contents. Very short, non-word variable should only used for iterations in `for()` loops.

```
for ( $j = 0; $j < 0; $j++ ) { ... }
$str
$buffer
$group_id
$last_city
```




---

## 9. Language specifics

### 9.1 Arrays

#### Numerically-indexed arrays

Arrays SHOULD always be created using the `array()` function rather than the square bracket notation (`$array = [ ... ]`).

* Negative numbers MUST not be used as indices.
* Base numbers other than zero (0) SHOULD NOT be used.
* A space SHOULD always be inserted after commas to aid readability. (See more about spaces, above).

When declaring multi-line index arrays the initial array item SHOULD begin on the line following the `array()`` function, indented by four spaces. Subsequent lines MUST have the same indentation. The closing parenthesis should be on a line by itself at the same indentation level as the line containing the array declaration:

```
$array = array(
    1, 2, 3, 4, 5,
    $a, $b, $c,
    'colour', 'shape',
);
```

A trailing comma MUST always be included after the final item in the array. This helps avoid errors should the array be appended to and the missing comma not restored.


#### Associative arrays

When declaring associative arrays, the statement SHOULD be broken into multiple lines, following the same guidelines as for numerically-indexed arrays.

Key and value pairs SHOULD be padded with whitespace so that they align.

```
$array = array(
    'first_key'  => 'first value',
    'second_key' => 'second value',
);
```

Again, a trailing comma MUST always be included after the final item in the array.

<small>Source: Zend</small>


### 9.2 elseif, not else if

`else if` is not compatible with the colon syntax for `if|elseif` blocks. For this reason, use `elseif` for conditionals.


### 9.3 Logical operators

Use of the `||` "or" comparison operator is discouraged as its clarity on some output devices is low (looking like the number 11 for instance). `&&` is preferred over `and` but either are acceptable. A space should always precede and follow `!`


### 9.4 Regular expressions

Perl compatible regular expressions (PCRE, `preg_` functions) SHOULD be used in preference to their POSIX counterparts.

Single-quoted strings SHOULD be used for regular expressions as they have only two metasequences (sequences of characters that have special meaning in a regular expression pattern): `\'` and `\\`.


### 9.5 Ternary operator

Ternary operators are fine, but always have them test if the statement is true, not false. Otherwise, it just gets confusing. (An exception would be using ! empty(), as testing for false here is generally more intuitive.)

For example:

```
// (if statement is true) ? (do this) : (else, do this);
$musictype = ( 'jazz' == $music ) ? 'cool' : 'blah';
```


### 9.6 TRUE, FALSE, and NULL

TRUE, FALSE, and NULL are PHP keywords that should always be written fully uppercase.


### 9.7 Yoda conditions

```
if ( true == $the_force ) {
    $victorious = you_will( $be );
}
```

When doing logical comparisons, always put the variable on the right side, constants or literals on the left.

In the above example, if you omit an equals sign (admit it, it happens even to the most seasoned of us), you'll get a parse error, because you can’t assign to a constant like true. If the statement were the other way around ( $the_force = true ), the assignment would be perfectly valid, returning 1, causing the `if` statement to evaluate to true, and you could be chasing that bug for a while.

A little bizarre it is to read. Get used to it you will.

This applies to `==`, `!=`, `===`, and `!==`. Yoda conditions for `<`, `>`, `<=` or `>=` are significantly more difficult to read and are best avoided.




---

## 10. Security

Ensure that your code is secure and does not make the web server vulnerable to attack.

Areas that you MUST address and actively test for include:

* Input validation
* Secure network connections (SSL)
* Cross-site scripting
* SQL, code or command injection
* Remote execution
* Session security
* Securing file access
* Securing via obscurity


### 10.1 Debug code

Debugging code MUST NOT be left in production code, even if commented out.

Functions such as `var_dump()`, `print_r()`, `die()`, or `exit()` SHOULD NOT remain in your code unless it serves a specific purpose other than debugging.



---

## Further reading

* [CodeIgniter PHP style guide](https://codeigniter.com/user_guide/general/styleguide.html)
* [MIT Sloan School of Management](http://mitsloan.mit.edu/shared/content/PHP_Code_Style_Guide.php)
* [phpDocumentor](https://manual.phpdoc.org/HTMLSmartyConverter/HandS/li_phpDocumentor.html)
* [Semantic versioning](http://semver.org/)
* [WordPress PHP coding standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/php/)
* [Zend framework coding standard for PHP](https://framework.zend.com/manual/1.11/en/coding-standard.html)
