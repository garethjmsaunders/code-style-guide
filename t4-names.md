# T4 naming style guide

version 0.6.7
Last updated: Thursday 9 February 2017

The terms MUST, MUST NOT, SHOULD, SHOULD NOT, and MAY are used in this document with the meanings found in [RFC 2119: Key words for use in RFCs to indicate requirement levels](https://www.ietf.org/rfc/rfc2119.txt).

<!-- MarkdownTOC depth=2 -->

- [1. Introduction](#1-introduction)
- [2. Sections](#2-sections)
    - [2.1 Section names](#21-section-names)
    - [2.2 Output URIs](#22-output-uris)
- [3. Page layouts](#3-page-layouts)
- [4. Content types \(creating\)](#4-content-types-creating)
    - [4.1 Name and description](#41-name-and-description)
    - [4.2 Elements](#42-elements)
    - [4.3 Character limits](#43-character-limits)
    - [4.4 Layout](#44-layout)
- [5. Content types \(using\)](#5-content-types-using)
- [6. List items](#6-list-items)
    - [6.1 Name](#61-name)
    - [6.2 Value](#62-value)
- [7. Navigation objects](#7-navigation-objects)
    - [7.1 Breadcrumbs](#71-breadcrumbs)
    - [7.2 Generate file](#72-generate-file)
    - [7.3 Link menu](#73-link-menu)
    - [7.4 Related content](#74-related-content)
    - [7.5 Section details](#75-section-details)
- [8. Groups](#8-groups)
    - [8.1 Group names](#81-group-names)
- [9. Channel names](#9-channel-names)
- [10. Media content types](#10-media-content-types)
- [11. Media library](#11-media-library)
    - [11.1 Category folders](#111-category-folders)
    - [11.2 Asset subfolders](#112-asset-subfolders)
- [12. Filenames](#12-filenames)
- [13. Metadata](#13-metadata)
    - [13.1 DC.title](#131-dctitle)
    - [13.2 DC.description](#132-dcdescription)
- [14. References](#14-references)

<!-- /MarkdownTOC -->


## 1. Introduction

TERMINALFOUR is a software company based in Dublin, their primary product, an enterprise content management system is also called TERMINALFOUR. In this document the software will be refered to as T4 and the company as TERMINALFOUR. 

Any new T4 assets MUST use these guidelines for naming.




---

## 2. Sections

### 2.1 Section names

Section are normally equal to a web page. Section names are used in the creation of menu items and often in populating the `<title>` element on a page. Section names:

* MUST be descriptive. 
* MUST begin with a capital letter. 
* MUST use only A-Z, a-z, 0-9 and hyphen. 
* MUST NOT end with a full-stop. 
* MAY use abbreviations only if these are well known.


### 2.2 Output URIs

In T4, the URI of a section is created from the section name (unless an output URI is specified). It does this by stripping out punctuation, replacing spaces with hyphens and converting the result to lowercase.

So, for example, a section name of "Academic Schools and Departments" will become `academic-schools-and-departments`. Ideally the URI should be kept short so in this example it would be better to have the URI set to `schools`.

See the service manual [links policy](http://www.st-andrews.ac.uk/digital-standards/service-manual/links/) for more information about creating links.

Output URIs:

* SHOULD always be defined.
* MUST be meaningful.
* MUST use only a-z, 0-9 and hyphen. 
* MUST use hyphens to separate words.
* MAY use abbreviations only if these are well known.

Good examples

```
events
current-students
alumni-and-development
research-and-teaching
```

For subjects, output URIs MUST include the subject first, followed by speciality or otherwise

```
english
english-creative-writing
physics
physics-pod
```




---

## 3. Page layouts

Page layouts are used to standardise the appearance of content on your page. The number of page layouts SHOULD be kept to an absolute minimum: there may arise occasions where it's necessary to create more. Page layouts SHOULD always be reusable and not a one-off page layout. They MUST be named with sentence case.

Use a [BEM](http://getbem.com/naming/)-like naming convention that splits components' classes into three groups:

* Block: The root of the component (e.g. external website, school website, etc.).
* Element: A component part of the block (e.g. homepage, content page, etc.).
* Modifier: A variant or extension of the block or element.

Page layout names MUST use only one of the following formats:

```
block__element
block__element--modifier
block--modifier
```

* MUST use only a-z, 0-9, underscore or hyphen.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.
* MUST use two underscores (`__`) between block and element.
* MUST use two hyphens (`--`) between block and modifier, or element and modifier.

Good examples

```
// block__element
external__home

// block__element--modifier
external__content--full-width
external__content--aside
global__blank--html
school__home--arts
school__home--divinity
school__home--medicine
school__home--science

// block--modifier
htaccess--staff-only
htaccess--staff-student
```




---

## 4. Content types (creating)

### 4.1 Name and description

The name of a content type MUST correspond one-to-one with the name of its pattern in the [digital pattern library](https://www.st-andrews.ac.uk/dpl/). 

* Must begin with a capital letter.
* MUST use only A-Z, a-z, 0-9, spaces or hyphens.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.
* Deprecated patterns MUST be marked as `(deprecated)`.

The description of a content type MUST be added for every content type and be meaningful.

* Must begin with a capital letter.
* MUST use only A-Z, a-z, 0-9, spaces or hyphens.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.


Good examples

| DPL pattern name | Content type name | Description                 |
|:---------------- |:----------------- |:--------------------------- |
| Alert            | `Alert`           | Feedback message |
| Footer           | `Footer`          | Default option for bottom of all pages |
| Info bite (deprecated) | Info bite (deprecated) | Short snippet of information |


#### 4.1.1 More than one content type per pattern

One exception is when more than one content type is required to build the pattern. In this case the content type name SHOULD be prefixed with the pattern name followed by a space-hyphen-space and then the modifier or option.

For example, in `Navbox grid` because we need to wrap a number of individual Navbox content items with HTML we need to create separate content types to mark the start (`Navbox grid - start`) and end (`Navbox grid - end`) of the navbox grid.

| DPL pattern name | Content type name     | Description                 |
|:---------------- |:--------------------- |:--------------------------- |
| Navbox grid      | `Navbox grid - start` | Navbox grid - START - use this to start the row. |
| Navbox           | `Navbox`              | Flexible navbox allows different sizes and elements, including picture or solid colour background, text options. |
| Navbox grid      | `Navbox grid - end`   | Navbox grid - END - use this to end the row. |


### 4.2 Elements

Elements are the input fields that T4 editors see that get turned into the various bits of content in content items.

#### 4.2.1 Element names

Content type element names MUST be simple and easy to understand.

* Must begin with a capital letter.
* MUST use only A-Z, a-z, 0-9, spaces or hyphens.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.

Note that the default 'Name' element is required and cannot be deleted. T4 uses this as a user-friendly filename within the T4 admin interface. This MUST NOT be output onto the HTML page, see 4.4 below.


#### 4.2.2 Element descriptions

Descriptions MUST be completed for all elements.

* Must begin with a capital letter.
* MUST use only A-Z, a-z, 0-9, spaces or hyphens.
* MUST end with a full-stop.
* MAY use abbreviations only if these are well known.


### 4.3 Character limits

In general we have several levels of character limits.

| Usage                       | Character limit |
|:--------------------------- |:--------------- |
| Title / button text         | 80              |
| Links / small items         | 1024 to 2048    |
| Plain text                  | 25,000          |
| General / Large containers  | 96,000          |



### 4.4 Layout

The content type name MUST NOT be output onto the HTML page. In other words, never use the following T4 tag in a content type layout:

```
// Never use
<t4 type="content" name="Name" output="normal" modifiers=""  />
```

The content type name MUST be used solely as an identifier in the T4 backend.




---

## 5. Content types (using)

When using content types, content item names MUST include the content type name followed by a short description of its use. This makes it easier for users to understand the structure of the page.

* Must begin with the content type name.
* Content type and short description MUST be separated by a space, hyphen and space, thus: `Content type - Description`.
* Both content type and description MUST begin with a capital letter.
* MUST use only A-Z, a-z, 0-9, spaces, commas or hyphens.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.

Good examples

```
Code - Facts and figures page
General - Banner style
Navbox - Guardbridge energy project
Page title - Facts and figures
Staff profile - Professor Sally Mapstone, Principal
```




---

## 6. List items

Before creating a new list check to see if an existing list may be used or extended. 

Try to make lists as reusable as you can, and make the list and list items names simple and descriptive.


### 6.1 Name

The list item names should be user-centred and descriptive. This is what appears in the list in the content type in T4.

* MUST begin with a capital letter.
* MUST use only A-Z, a-z, 0-9, spaces, hyphens or parentheses.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.


### 6.2 Value

The value is what is inserted into the HTML code on the page.

* SHOULD begin with a capital letter.
* MUST use only a-z, 0-9, or hyphens.
* MUST NOT end with a full-stop.

Good examples

#### List: Alert

| Name               | Value         |
|:------------------ |:------------- |
| Success (green)    | alert-success |
| Information (blue) | alert-info    |
| Warning (yellow)    | alert-warning |
| Danger (red)       | alert-danger  |


#### List: Bootstrap sizing

| Name   | Value     |
|:------ |:--------- |
| Small  | col-sm-4  | 
| Medium | col-sm-6  |
| Large  | col-sm-8  |
| Full   | col-xs-12 |




---

## 7. Navigation objects

Navigation objects are largely used to create navigation structures and pull in content from other parts of a site.

Use a [BEM](http://getbem.com/naming/)-like naming convention that splits components' classes into three groups:

* Block: The root of the component (e.g. external website, school website, etc.).
* Element: A component part of the block (e.g. homepage, content page, etc.).
* Modifier: A variant or extension of the block or element.

Page layout names MUST use only one of the following formats:

```
block__element
block__element--modifier
block--modifier
```

* MUST use only a-z, 0-9, underscore or hyphen.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.
* MUST use two underscores (`__`) between block and element.
* MUST use two hyphens (`--`) between block and modifier, or element and modifier.
* Block MUST always be the name of the navigation object type.


### 7.1 Breadcrumbs

* Block MUST be `breadcrumbs`.
* Element MUST be the channel name.
* Modifier MUST be the breadcrumb length (with details).

```
breadcrumbs__external-website--full-path
breadcrumbs__external-website--level-1-to-4
breadcrumbs__external-website--max-length-3
```


### 7.2 Generate file

* Block MUST be `generate-file`.
* Element MUST be the name of the file to output, e.g. `.htaccess`.
* Modifier MUST be the name of the alternate formatter used, e.g. `text/htaccess` would be `text-htaccess`.

```
generate-file__htaccess--text-htaccess
```


### 7.3 Link menu

* Block MUST be `link-menu`.
* Element MUST be the menu type (`branch-at-level`, `children`, `siblings` or `children-and-siblings`).
* Modifier (`branch-at-level` only) MUST indicate the depth.

```
link-menu__branch-at-level--level-3
link-menu__children
link-menu__siblings
```


### 7.4 Related content

#### 7.4.1 Child sections

* Block MUST be `rel-content`.
* Element MUST be `child`.
* Modifier MUST be the name of the child section.

```
rel-content__child--aside
rel-content__child--aside-global
rel-content__child--footer
rel-content__child--footer-global
rel-content__child--hero-banner
```


#### 7.4.2 Specific sections

* Block MUST be `rel-content`.
* Element MUST be `section`.
* Modifier MUST be the specific name of the section.

```
rel-content__section--dpl-version
rel-content__section--footer-scripts
rel-content__section--footer-small
rel-content__section--head
rel-content__section--header-default
rel-content__section--header-external-homepage
rel-content__section--navigation-top-level
```


#### 7.4.3 Alternate content layout

* Block MUST be `rel-content`.
* Element MUST be `alt-layout`.
* Modifier MUST be the name of the alternate formatter used, e.g. `text/htaccess` would be `text-htaccess`.

```
rel-content__alt-layout--text-cta
rel-content__alt-layout--text-breadcrumbs
rel-content__alt-layout--text-footer
rel-content__alt-layout--text-header
rel-content__alt-layout--text-menu
rel-content__alt-layout--text-scripts
```


### 7.5 Section details

* Block MUST be `section-details`.
* Element MUST be the output detail. Options are:
    - Section ID - `id`
    - Section name - `name`
    - Section path - `path`
    - Link to section - `link`
* Modifier MUST be the specific name of the section, or in the case of `link` and `name` the level required.

```
section-details__id--facts-and-figures
section-details__link--level-2
section-details__name--level-2
section-details__path--about
section-details__path--business-services
section-details__path--community-facilities
section-details__path--external-homepage
```




---

## 8. Groups

Access to content and assets within T4 MUST be assigned on a group basis.

* Users MUST NOT be assigned to individual pages.
* Users MUST be assigned to groups.
* Groups must be assigned to sections, content types, page layouts, navigation objects, media library directories, etc.


### 8.1 Group names

Ideally, groups SHOULD be named by function (such as Orientation) rather than organisational structure (such as Student Services). Group names:

* MUST begin with a capital letter.
* MUST use only A-Z, a-z, 0-9 spaces and hyphens.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.

Good examples

```
External website
Visiting days
Alumni and donors
About - facts and figures
Service manual - corporate ID
```




---

## 9. Channel names

Channels are used to assemble content to publish to a website. Channel names:

* MUST be short and descriptive.
* MUST begin with a capital letter.
* MUST NOT include camelCase.
* MUST NOT end with a full-stop.

Good examples
```
External website
Internal website
Sandbox
RSS feed
```



---

## 10. Media content types

Media is a special, system-wide content type that determines how media items from the media library appear on a published webpage.

Content layouts for media content types MUST follow this pattern:

> file_type/*


* The file type MUST be descriptive using either a generic type (image, application, path) or the file extension (e.g. css, docx, pdf).
* The content layout name MUST be lowercase

Good examples

```
application/*
css/*
docx/*
image/*
js/*
path/*
pdf/*
pptx/*
xslx/*
xml/*
```




---

## 11. Media library

The structure of the media library SHOULD match the structure of the website—this makes it much easier to find assets

Asset subfolders MUST exist beneath each section to store different categories of assets.

For example:

```
Categorized
|-- University
|   |-- About
|   |   |-- documents
|   |   |-- images
|   |-- Digital standards
|   |   |-- Service manual
|   |   |   |-- documents
|   |   |   |-- images
|   |   |   |-- restricted
|   |-- About
|   |   |-- documents
|   |   |-- images
|   |   |   |-- 360x240
|   |   |   |-- graduating-students
|   |   |   |-- graduation-gallery
|   |   |   |-- hero-banner
|   |   |   |-- previous-ceremonies
|   |   |   |-- tiles
```


### 11.1 Category folders

When published, T4 converts all characters to lowercase and replaces spaces with hyphens.

* MUST begin with a capital letter.
* MUST use sentence case.
* MUST use only A-Z, a-z, 0-9 spaces and hyphens.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.

```
Categorized
|-- University
|   |-- About
|   |-- Digital standards
|   |   |-- Service manual
|   |-- About
```


### 11.2 Asset subfolders

* MUST use only a-z, 0-9 and hyphens.
* MUST NOT end with a full-stop.
* MAY use abbreviations only if these are well known.

```
360x240
documents
graduating-students
graduation-gallery
hero-banner
images
previous-ceremonies
restricted
tiles
```




---

## 12. Filenames

Regex pattern: `([a-z0-9\-]+).([a-z0-9]{3,})`

The following guidance is taken from the digital standard service manual page on [filenames](https://www.st-andrews.ac.uk/digital-standards/service-manual/filenames/).

Files MUST be named in a consistent way according to the guidelines below. This will ensure they are web safe.

* You MUST use only lowercase letters (`a-z`), numerals (`0-9`), and hyphens (`-`).
* You MUST NOT use special characters (e.g. `á`, `ê`, `ï`, `õ`, `ù`) or other punctuation marks, including underscores (`_`).
* You MUST NOT use spaces: instead you MUST use hyphens in place of spaces to delimit words.
* You MUST NOT include dates or version numbers in filenames.
* Filenames MUST be short, meaningful and descriptive.

Correct
```
guidance-notes-for-direct-applicants.pdf
visiting-day-programme.pdf
william-and-mary.docx
ug-prospectus.pdf
```

Incorrect
```
Guidance notes for direct applicants.pdf
VDprog.pdf
william-&-mary-version-2.1.docx
ug-prospectus-2016-2017.pdf
```

The digital communications team reserves the right to change (or request changes to) filenames if they do not meet digital best practice.




---

## 13. Metadata

Metadata MUST be completed for all new sections. 

There are currently only two [Dublin Core metadata](http://dublincore.org/documents/usageguide/) elements used in T4:

* `DC.title`
* `DC.description`


### 13.1 DC.title

Dublin Core defines [DC.title](http://dublincore.org/documents/usageguide/elements.shtml) as "the name given to the resource. Typically, a title will be a name by which the resource is formally known."

* This SHOULD be the page heading, which also SHOULD be the same as the section name.


### 13.2 DC.description

Dublin Core defines [DC.description](http://dublincore.org/documents/usageguide/elements.shtml) as "An account of the content of the resource. Description may include but is not limited to: an abstract, table of contents, reference to a graphical representation of content or a free-text account of the content."

* Full sentences MUST be used.
* House style MUST be adhered to.
* Sentences MUST NOT exceed 160 characters.




---

## 14. References

* [Dublin Core metadata](http://dublincore.org/documents/usageguide/elements.shtml)