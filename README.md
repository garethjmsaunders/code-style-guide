# Digital code style and standards guides

Version 2.0.0
Last updated: Sunday 19 April 2020

I wrote these style and standards guides while I was web architect at the University of St Andrews. This version reflects my current practices.

<!-- MarkdownTOC -->

- [Summary](#summary)
    - [Why use style guides](#why-use-style-guides)
    - [When to be inconsistent](#when-to-be-inconsistent)
- [1. Background](#1-background)
    - [1.1 Potential issues](#11-potential-issues)
- [2. Objective](#2-objective)
- [3. Benefits](#3-benefits)
- [4. Scope](#4-scope)
- [5. Constraints](#5-constraints)
    - [5.1 What stops us?](#51-what-stops-us)
    - [5.2 How do we enforce it?](#52-how-do-we-enforce-it)
- [6. Assumptions](#6-assumptions)
- [7. Risks](#7-risks)
    - [7.1 Not doing](#71-not-doing)
    - [7.2 Doing](#72-doing)
- [8. Deliverables](#8-deliverables)

<!-- /MarkdownTOC -->




---

<a id="summary"></a>
## Summary

<a id="why-use-style-guides"></a>
### Why use style guides

In working on large, long-running projects, with dozens of developers of differing specialities and abilities, it is important that we all work in a unified way in order to, among other things:

* **keep code maintainable**;
* **keep code transparent, sane, and readable**;
* **keep code scalable**.

These style and standards guides contain recommendations and approaches that will help us to acheive these goals.

These guides are valuable for developers who:

*   build and maintain products for a reasonable length of time;
*   have developers of differing abilities and specialisms;
*   have a number of different developers working on a product at any
    given time;
*   on-board new staff regularly;
*   have a number of codebases that developers dip in and out of.

While style guides are typically more suited to product teams—large codebases on long-lived and evolving projects, with multiple developers contributing over prolonged periods of time—all developers should strive for a degree of standardisation in their code.

A good style guide, when well followed, will:

* **set the standard for code quality across a codebase**;
* **promote consistency across codebases**;
* **give developers a feeling of familiarity across codebases**;
* **increase productivity**.

Style guides should be learned, understood, and implemented at all times on a project which is governed by one, and any deviation must be fully justified.


<a id="when-to-be-inconsistent"></a>
### When to be inconsistent

While consistency is important, equally important is knowing when to be inconsistent—sometimes the style guide just doesn’t apply.

Ask yourself if applying the rule would make the code less readable, even for someone who is used to reading code that follows the rules. When in doubt use your best judgment, look at other examples, and decide what looks best.

The ground rule is simple: **readability is preferential to strict adherence to rules**.


Source: [CSS guidelines](http://cssguidelin.es/#the-importance-of-a-styleguide "Harry Roberts")



---

<a id="1-background"></a>
## 1. Background


<a id="11-potential-issues"></a>
### 1.1 Potential issues

Currently every developer has their own way of doing things, which may be fine for small, stand-alone projects but within an enterprise-level project this can lead to issues such as:

* Inconsistent code in terms of organisation, syntax, formatting, and naming conventions.
* Code bloat in production systems, often including code that is either never used or is out-of-date (e.g. hacks for redundant versions of Internet Explorer).
* Multiple implementations of functionality, with the consequential maintenance overload due to multiple chunks of code that solve the same problem in different ways, and an inconsistent look-and-feel due to multiple implementations of similar features e.g. tabs, sliders.
* Bugs and typos.
* Uncommented or poorly documented code.
* Unreadable code.
* Code from one site linked to from other sites, that if updated at source runs the risk of breaking features implemented elsewhere.

While it's obvious that these inconsistencies and issues can result from multiple developers working across multiple projects, it can also be true for solo developers working on single projects. In other words, developers can be inconsistent even with themselves in the same project.

The consequences of this are many:

* Code that is difficult or impossible to maintain.
* Code that is fragile and easy to break in unknown ways.
* Fear of updating or improving code that leads to forked code and/or duplicating functionality using different resources.
* Maintenance overload.
* Slows down development




---

<a id="2-objective"></a>
## 2. Objective

Our objectives for introducing code standards and style guides are:

1. Develop an agreed standard for all code and ensure that code within scope adheres to these standards.
2. Use industry best practices.
3. Promote efficiency in maintaning code.
4. Continuously improve our code.




---

<a id="3-benefits"></a>
## 3. Benefits

Standard conventions will make it easier for developers to make decisions about how to code which should result in faster development, and make it easier to spot errors and typos.




---

<a id="4-scope"></a>
## 4. Scope

These standards and style guides apply to all new websites and applications for which the digital communications team is responsible (whether developed in-house or outsourced). Guidelines will be written for the following languages:

* Cascading Stylesheets (CSS), including pre-processors such as Sass.
* HTML
* JavaScript, including frameworks such as jQuery
* PHP
* XML, including RSS and XSLT

as well as 

* Commit messages (for version control software, e.g. Git.)
* Markdown (for writing documentation)
* Sublime Text packages (standard packages for developing the DPL).




---

<a id="5-constraints"></a>
## 5. Constraints

<a id="51-what-stops-us"></a>
### 5.1 What stops us?

* It's a lot of work to define and document exactly what we want.
* Building consensus with other developers.


<a id="52-how-do-we-enforce-it"></a>
### 5.2 How do we enforce it?

External standards, policies and regulations, e.g.

* HTML specifications (W3C)
* CSS specifications (W3C)
* ECMAScript (JavaScript) specifications
* PHP specifications
* XML specifications (W3C), including RSS/Atom and XSLT
* In-code documentation formatting standards such as PHPDoc, JSDoc, etc.
* Other relevant code standards such as Microformats (hCalendar, hCard), microdata, FOAF, DOAC, Dublin Core metadata, RDF, WordPress Codex, etc.

It is imperative that we introduce these code standards and style guides as soon as possible so that we may reduce existing code-debt (code that has been developed prior to the introduction of these standards) in the digital pattern library.




---

<a id="6-assumptions"></a>
## 6. Assumptions

* We're allowed to enforce governance on front-end code.
* Delivered in a digital manner.
* We will maintain and continuously improve the code standards guides.




---

<a id="7-risks"></a>
## 7. Risks

<a id="71-not-doing"></a>
### 7.1 Not doing

* Current issues (described in 1. Background) and consequences will continue or even get worse.


<a id="72-doing"></a>
### 7.2 Doing
* Code that is developed before the standard is completed will need to be refactored.
* May slow down some development.
* Developers refuse to use it because of personal coding preferences and habits.
* Developers may feel frustrated because their coding requirements are not addressed.




---

<a id="8-deliverables"></a>
## 8. Deliverables

Standards and/or style guide documentation for each language in scope, written in Markdown (which can be converted easily to HTML):

1. Commit messages style guide
2. CSS style and standards guide
3. HTML style guide
4. JavaScript style guide
5. Markdown style guide
6. PHP style guide
7. Sublime Text editor standards guide
8. XML style guide
