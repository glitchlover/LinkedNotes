# Selectors Level 4

## Editor’s Draft, 14 September 2020

Specification Metadata

This version:

[https://drafts.csswg.org/selectors/](https://drafts.csswg.org/selectors/)

Latest published version:

[https://www.w3.org/TR/selectors-4/](https://www.w3.org/TR/selectors-4/)

Previous Versions:

[https://www.w3.org/TR/2018/WD-selectors-4-20180202/](https://www.w3.org/TR/2018/WD-selectors-4-20180202/)

[https://www.w3.org/TR/2018/WD-selectors-4-20180201/](https://www.w3.org/TR/2018/WD-selectors-4-20180201/)

[https://www.w3.org/TR/2013/WD-selectors4-20130502/](https://www.w3.org/TR/2013/WD-selectors4-20130502/)

[https://www.w3.org/TR/2012/WD-selectors4-20120823/](https://www.w3.org/TR/2012/WD-selectors4-20120823/)

[https://www.w3.org/TR/2011/WD-selectors4-20110929/](https://www.w3.org/TR/2011/WD-selectors4-20110929/)

Test Suite:

[http://test.csswg.org/suites/selectors-4\_dev/nightly-unstable/](http://test.csswg.org/suites/selectors-4_dev/nightly-unstable/)

Issue Tracking:

[Inline In Spec](https://drafts.csswg.org/selectors-4/#issues-index)

[GitHub Issues](https://github.com/w3c/csswg-drafts/labels/selectors-4)

Editors:

[Elika J. Etemad / fantasai](http://fantasai.inkedblade.net/contact) (Invited Expert)

[Tab Atkins Jr.](http://xanthir.com/contact/) (Google)

Former Editors:

[Tantek Çelik](http://www.tantek.com/)

Daniel Glazman

Ian Hickson

Peter Linss

John Williams

Suggest an Edit for this Spec:

[GitHub Editor](https://github.com/w3c/csswg-drafts/blob/master/selectors-4/Overview.bs)

[Copyright](https://www.w3.org/Consortium/Legal/ipr-notice#Copyright) © 2020 [W3C](https://www.w3.org/)<sup>®</sup> ([MIT](https://www.csail.mit.edu/), [ERCIM](https://www.ercim.eu/), [Keio](https://www.keio.ac.jp/), [Beihang](https://ev.buaa.edu.cn/)). W3C [liability](https://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](https://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks) and [permissive document license](https://www.w3.org/Consortium/Legal/2015/copyright-software-and-document) rules apply.

-

## Abstract

[Selectors](https://drafts.csswg.org/selectors-4/#selector) are patterns that match against elements in a tree, and as such form one of several technologies that can be used to select nodes in a document. Selectors have been optimized for use with HTML and XML, and are designed to be usable in performance-critical code. They are a core component of CSS (Cascading Style Sheets), which uses Selectors to bind style properties to elements in the document. Selectors Level 4 describes the selectors that already exist in [\[SELECT\]](https://drafts.csswg.org/selectors-4/#biblio-select), and further introduces new selectors for CSS and other languages that may need them.

[CSS](https://www.w3.org/TR/CSS/) is a language for describing the rendering of structured documents (such as HTML and XML) on screen, on paper, etc.

## Status of this document

This is a public copy of the editors’ draft. It is provided for discussion only and may change at any moment. Its publication here does not imply endorsement of its contents by W3C. Don’t cite this document other than as work in progress.

[GitHub Issues](https://github.com/w3c/csswg-drafts/issues) are preferred for discussion of this specification. When filing an issue, please put the text “selectors” in the title, preferably like this: “\[selectors\] _…summary of comment…_”. All issues and comments are [archived](https://lists.w3.org/Archives/Public/public-css-archive/), and there is also a [historical archive](https://lists.w3.org/Archives/Public/www-style/).

This document was produced by the [CSS Working Group](https://www.w3.org/Style/CSS/).

This document was produced by a group operating under the [W3C Patent Policy](https://www.w3.org/Consortium/Patent-Policy/). W3C maintains a [public list of any patent disclosures](https://www.w3.org/2004/01/pp-impl/32061/status) made in connection with the deliverables of the group; that page also includes instructions for disclosing a patent. An individual who has actual knowledge of a patent which the individual believes contains [Essential Claim(s)](https://www.w3.org/Consortium/Patent-Policy/#def-essential) must disclose the information in accordance with [section 6 of the W3C Patent Policy](https://www.w3.org/Consortium/Patent-Policy/#sec-Disclosure).

This document is governed by the [15 September 2020 W3C Process Document](https://www.w3.org/2020/Process-20200915/).

The following features are at-risk, and may be dropped during the CR period:

- the column combinator
- the [:read-write](https://drafts.csswg.org/selectors-4/#read-write-pseudo) pseudo-class
- the [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo) pseudo-class

“At-risk” is a W3C Process term-of-art, and does not necessarily imply that the feature is in danger of being dropped or delayed. It means that the WG believes the feature may have difficulty being interoperably implemented in a timely manner, and marking it as such allows the WG to drop the feature if necessary when transitioning to the Proposed Rec stage, without having to publish a new Candidate Rec without the feature first.

## Table of Contents

1. [1 Introduction](https://drafts.csswg.org/selectors-4/#context)
    1. [1.1 Module Interactions](https://drafts.csswg.org/selectors-4/#placement)
2. [2 Selectors Overview](https://drafts.csswg.org/selectors-4/#overview)
3. [3 Selector Syntax and Structure](https://drafts.csswg.org/selectors-4/#syntax)
    1. [3.1 Structure and Terminology](https://drafts.csswg.org/selectors-4/#structure)
    2. [3.2 Data Model](https://drafts.csswg.org/selectors-4/#data-model)
    3. [3.3 Scoped Selectors](https://drafts.csswg.org/selectors-4/#scoping)
    4. [3.4 Relative Selectors](https://drafts.csswg.org/selectors-4/#relative)
        1. [3.4.1 Absolutizing a Relative Selector](https://drafts.csswg.org/selectors-4/#absolutizing)
    5. [3.5 Pseudo-classes](https://drafts.csswg.org/selectors-4/#pseudo-classes)
    6. [3.6 Pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-elements)
        1. [3.6.1 Syntax](https://drafts.csswg.org/selectors-4/#pseudo-element-syntax)
        2. [3.6.2 Binding to the Document Tree](https://drafts.csswg.org/selectors-4/#pseudo-element-attachment)
        3. [3.6.3 Pseudo-classing Pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element-states)
        4. [3.6.4 Internal Structure](https://drafts.csswg.org/selectors-4/#pseudo-element-structure)
    7. [3.7 Characters and case sensitivity](https://drafts.csswg.org/selectors-4/#case-sensitive)
    8. [3.8 Declaring Namespace Prefixes](https://drafts.csswg.org/selectors-4/#namespaces)
    9. [3.9 Invalid Selectors and Error Handling](https://drafts.csswg.org/selectors-4/#invalid)
4. [4 Logical Combinations](https://drafts.csswg.org/selectors-4/#logical-combination)
    1. [4.1 Selector Lists](https://drafts.csswg.org/selectors-4/#grouping)
    2. [4.2 The Matches-Any Pseudo-class: :is()](https://drafts.csswg.org/selectors-4/#matches)
    3. [4.3 The Negation (Matches-None) Pseudo-class: :not()](https://drafts.csswg.org/selectors-4/#negation)
    4. [4.4 The Specificity-adjustment Pseudo-class: :where()](https://drafts.csswg.org/selectors-4/#zero-matches)
    5. [4.5 The Relational Pseudo-class: :has()](https://drafts.csswg.org/selectors-4/#relational)
5. [5 Elemental selectors](https://drafts.csswg.org/selectors-4/#elemental-selectors)
    1. [5.1 Type (tag name) selector](https://drafts.csswg.org/selectors-4/#type-selectors)
    2. [5.2 Universal selector](https://drafts.csswg.org/selectors-4/#the-universal-selector)
    3. [5.3 Namespaces in Elemental Selectors](https://drafts.csswg.org/selectors-4/#type-nmsp)
    4. [5.4 The Defined Pseudo-class: :defined](https://drafts.csswg.org/selectors-4/#the-defined-pseudo)
6. [6 Attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-selectors)
    1. [6.1 Attribute presence and value selectors](https://drafts.csswg.org/selectors-4/#attribute-representation)
    2. [6.2 Substring matching attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-substrings)
    3. [6.3 Case-sensitivity](https://drafts.csswg.org/selectors-4/#attribute-case)
    4. [6.4 Attribute selectors and namespaces](https://drafts.csswg.org/selectors-4/#attrnmsp)
    5. [6.5 Default attribute values in DTDs](https://drafts.csswg.org/selectors-4/#def-values)
    6. [6.6 Class selectors](https://drafts.csswg.org/selectors-4/#class-html)
    7. [6.7 ID selectors](https://drafts.csswg.org/selectors-4/#id-selectors)
7. [7 Linguistic Pseudo-classes](https://drafts.csswg.org/selectors-4/#linguistic-pseudos)
    1. [7.1 The Directionality Pseudo-class: :dir()](https://drafts.csswg.org/selectors-4/#the-dir-pseudo)
    2. [7.2 The Language Pseudo-class: :lang()](https://drafts.csswg.org/selectors-4/#the-lang-pseudo)
8. [8 Location Pseudo-classes](https://drafts.csswg.org/selectors-4/#location)
    1. [8.1 The Hyperlink Pseudo-class: :any-link](https://drafts.csswg.org/selectors-4/#the-any-link-pseudo)
    2. [8.2 The Link History Pseudo-classes: :link and :visited](https://drafts.csswg.org/selectors-4/#link)
    3. [8.3 The Local Link Pseudo-class: :local-link](https://drafts.csswg.org/selectors-4/#the-local-link-pseudo)
    4. [8.4 The Target Pseudo-class: :target](https://drafts.csswg.org/selectors-4/#the-target-pseudo)
    5. [8.5 The Target Container Pseudo-class: :target-within](https://drafts.csswg.org/selectors-4/#the-target-within-pseudo)
    6. [8.6 The Reference Element Pseudo-class: :scope](https://drafts.csswg.org/selectors-4/#the-scope-pseudo)
9. [9 User Action Pseudo-classes](https://drafts.csswg.org/selectors-4/#useraction-pseudos)
    1. [9.1 The Pointer Hover Pseudo-class: :hover](https://drafts.csswg.org/selectors-4/#the-hover-pseudo)
    2. [9.2 The Activation Pseudo-class: :active](https://drafts.csswg.org/selectors-4/#the-active-pseudo)
    3. [9.3 The Input Focus Pseudo-class: :focus](https://drafts.csswg.org/selectors-4/#the-focus-pseudo)
    4. [9.4 The Focus-Indicated Pseudo-class: :focus-visible](https://drafts.csswg.org/selectors-4/#the-focus-visible-pseudo)
    5. [9.5 The Focus Container Pseudo-class: :focus-within](https://drafts.csswg.org/selectors-4/#the-focus-within-pseudo)
10. [10 Time-dimensional Pseudo-classes](https://drafts.csswg.org/selectors-4/#time-pseudos)
    1. [10.1 The Current-element Pseudo-class: :current](https://drafts.csswg.org/selectors-4/#the-current-pseudo)
    2. [10.2 The Past-element Pseudo-class: :past](https://drafts.csswg.org/selectors-4/#the-past-pseudo)
    3. [10.3 The Future-element Pseudo-class: :future](https://drafts.csswg.org/selectors-4/#the-future-pseudo)
11. [11 Resource State Pseudos](https://drafts.csswg.org/selectors-4/#resource-pseudos)
    1. [11.1 Video/Audio Play State: the :playing and :paused pseudo-classes](https://drafts.csswg.org/selectors-4/#video-state)
12. [12 The Input Pseudo-classes](https://drafts.csswg.org/selectors-4/#input-pseudos)
    1. [12.1 Input Control States](https://drafts.csswg.org/selectors-4/#input-states)
        1. [12.1.1 The :enabled and :disabled Pseudo-classes](https://drafts.csswg.org/selectors-4/#enableddisabled)
        2. [12.1.2 The Mutability Pseudo-classes: :read-only and :read-write](https://drafts.csswg.org/selectors-4/#rw-pseudos)
        3. [12.1.3 The Placeholder-shown Pseudo-class: :placeholder-shown](https://drafts.csswg.org/selectors-4/#placeholder)
        4. [12.1.4 The Default-option Pseudo-class: :default](https://drafts.csswg.org/selectors-4/#the-default-pseudo)
    2. [12.2 Input Value States](https://drafts.csswg.org/selectors-4/#input-value-states)
        1. [12.2.1 The Selected-option Pseudo-class: :checked](https://drafts.csswg.org/selectors-4/#checked)
        2. [12.2.2 The Indeterminate-value Pseudo-class: :indeterminate](https://drafts.csswg.org/selectors-4/#indeterminate)
    3. [12.3 Input Value-checking](https://drafts.csswg.org/selectors-4/#ui-validity)
        1. [12.3.1 The Empty-Value Pseudo-class: :blank](https://drafts.csswg.org/selectors-4/#blank)
        2. [12.3.2 The Validity Pseudo-classes: :valid and :invalid](https://drafts.csswg.org/selectors-4/#validity-pseudos)
        3. [12.3.3 The Range Pseudo-classes: :in-range and :out-of-range](https://drafts.csswg.org/selectors-4/#range-pseudos)
        4. [12.3.4 The Optionality Pseudo-classes: :required and :optional](https://drafts.csswg.org/selectors-4/#opt-pseudos)
        5. [12.3.5 The User-interaction Pseudo-class: :user-invalid](https://drafts.csswg.org/selectors-4/#user-pseudos)
13. [13 Tree-Structural pseudo-classes](https://drafts.csswg.org/selectors-4/#structural-pseudos)
    1. [13.1 :root pseudo-class](https://drafts.csswg.org/selectors-4/#the-root-pseudo)
    2. [13.2 :empty pseudo-class](https://drafts.csswg.org/selectors-4/#the-empty-pseudo)
    3. [13.3 Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#child-index)
        1. [13.3.1 :nth-child() pseudo-class](https://drafts.csswg.org/selectors-4/#the-nth-child-pseudo)
        2. [13.3.2 :nth-last-child() pseudo-class](https://drafts.csswg.org/selectors-4/#the-nth-last-child-pseudo)
        3. [13.3.3 :first-child pseudo-class](https://drafts.csswg.org/selectors-4/#the-first-child-pseudo)
        4. [13.3.4 :last-child pseudo-class](https://drafts.csswg.org/selectors-4/#the-last-child-pseudo)
        5. [13.3.5 :only-child pseudo-class](https://drafts.csswg.org/selectors-4/#the-only-child-pseudo)
    4. [13.4 Typed Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#typed-child-index)
        1. [13.4.1 :nth-of-type() pseudo-class](https://drafts.csswg.org/selectors-4/#the-nth-of-type-pseudo)
        2. [13.4.2 :nth-last-of-type() pseudo-class](https://drafts.csswg.org/selectors-4/#the-nth-last-of-type-pseudo)
        3. [13.4.3 :first-of-type pseudo-class](https://drafts.csswg.org/selectors-4/#the-first-of-type-pseudo)
        4. [13.4.4 :last-of-type pseudo-class](https://drafts.csswg.org/selectors-4/#the-last-of-type-pseudo)
        5. [13.4.5 :only-of-type pseudo-class](https://drafts.csswg.org/selectors-4/#the-only-of-type-pseudo)
14. [14 Combinators](https://drafts.csswg.org/selectors-4/#combinators)
    1. [14.1 Descendant combinator ( )](https://drafts.csswg.org/selectors-4/#descendant-combinators)
    2. [14.2 Child combinator (`>`)](https://drafts.csswg.org/selectors-4/#child-combinators)
    3. [14.3 Next-sibling combinator (`+`)](https://drafts.csswg.org/selectors-4/#adjacent-sibling-combinators)
    4. [14.4 Subsequent-sibling combinator (`~`)](https://drafts.csswg.org/selectors-4/#general-sibling-combinators)
15. [15 Grid-Structural Selectors](https://drafts.csswg.org/selectors-4/#table-pseudos)
    1. [15.1 Column combinator (`||`)](https://drafts.csswg.org/selectors-4/#the-column-combinator)
    2. [15.2 :nth-col() pseudo-class](https://drafts.csswg.org/selectors-4/#the-nth-col-pseudo)
    3. [15.3 :nth-last-col() pseudo-class](https://drafts.csswg.org/selectors-4/#the-nth-last-col-pseudo)
16. [16 Calculating a selector’s specificity](https://drafts.csswg.org/selectors-4/#specificity-rules)
17. [17 Grammar](https://drafts.csswg.org/selectors-4/#grammar)
    1. [17.1 <forgiving-selector-list> and <forgiving-relative-selector-list>](https://drafts.csswg.org/selectors-4/#forgiving-selector)
18. [18 API Hooks](https://drafts.csswg.org/selectors-4/#api-hooks)
    1. [18.1 Parse A Selector](https://drafts.csswg.org/selectors-4/#parse-selector)
    2. [18.2 Parse A Relative Selector](https://drafts.csswg.org/selectors-4/#parse-relative-selector)
    3. [18.3 Match a Selector Against an Element](https://drafts.csswg.org/selectors-4/#match-against-element)
    4. [18.4 Match a Selector Against a Pseudo-element](https://drafts.csswg.org/selectors-4/#match-against-pseudo-element)
    5. [18.5 Match a Selector Against a Tree](https://drafts.csswg.org/selectors-4/#match-against-tree)
19. [Appendix A: Guidance on Mapping Source Documents & Data to an Element Tree](https://drafts.csswg.org/selectors-4/#dom-mapping)
20. [Appendix B: Obsolete but Required Parsing Quirks for Web Compat](https://drafts.csswg.org/selectors-4/#compat)
21. [19 Changes](https://drafts.csswg.org/selectors-4/#changes)
    1. [19.1 Changes since the 21 November 2018 Working Draft](https://drafts.csswg.org/selectors-4/#changes-2018-11)
    2. [19.2 Changes since the 2 February 2018 Working Draft](https://drafts.csswg.org/selectors-4/#changes-2018-02)
    3. [19.3 Changes since the 2 May 2013 Working Draft](https://drafts.csswg.org/selectors-4/#changes-2013)
    4. [19.4 Changes since the 23 August 2012 Working Draft](https://drafts.csswg.org/selectors-4/#changes-2012)
    5. [19.5 Changes since the 29 September 2011 Working Draft](https://drafts.csswg.org/selectors-4/#changes-2011)
    6. [19.6 Changes Since Level 3](https://drafts.csswg.org/selectors-4/#changes-level-3)
22. [20 Acknowledgements](https://drafts.csswg.org/selectors-4/#acknowledgements)
23. [21 Privacy and Security Considerations](https://drafts.csswg.org/selectors-4/#priv-sec)
24. [Conformance](https://drafts.csswg.org/selectors-4/#conformance)
    1. [Document conventions](https://drafts.csswg.org/selectors-4/#document-conventions)
    2. [Conformance classes](https://drafts.csswg.org/selectors-4/#conform-classes)
    3. [Requirements for Responsible Implementation of CSS](https://drafts.csswg.org/selectors-4/#conform-responsible)
        1. [Partial Implementations](https://drafts.csswg.org/selectors-4/#conform-partial)
        2. [Implementations of Unstable and Proprietary Features](https://drafts.csswg.org/selectors-4/#conform-future-proofing)
        3. [Implementations of CR-level Features](https://drafts.csswg.org/selectors-4/#conform-testing)
25. [Index](https://drafts.csswg.org/selectors-4/#index)
    1. [Terms defined by this specification](https://drafts.csswg.org/selectors-4/#index-defined-here)
    2. [Terms defined by reference](https://drafts.csswg.org/selectors-4/#index-defined-elsewhere)
26. [References](https://drafts.csswg.org/selectors-4/#references)
    1. [Normative References](https://drafts.csswg.org/selectors-4/#normative)
    2. [Informative References](https://drafts.csswg.org/selectors-4/#informative)
27. [Issues Index](https://drafts.csswg.org/selectors-4/#issues-index)

## 1\. Introduction

_This section is not normative._

A [selector](https://drafts.csswg.org/selectors-4/#selector) is a boolean predicate that takes an element in a tree structure and tests whether the element matches the selector or not.

These expressions may be used for many things:

- directly on an element to test whether it matches some criteria, such as in the `element.matches()` function defined in [\[DOM\]](https://drafts.csswg.org/selectors-4/#biblio-dom)
- applied to an entire tree of elements to filter it into a set of elements that match the criteria, such as in the `document.querySelectorAll()` function defined in [\[DOM\]](https://drafts.csswg.org/selectors-4/#biblio-dom) or the selector of a CSS style rule.
- used "in reverse" to generate markup that would match a given selector, such as in [HAML](http://haml.info/) or [Emmet](https://en.wikipedia.org/wiki/Emmet_(software)).

Selectors Levels 1, 2, and 3 are defined as the subsets of selector functionality defined in the [CSS1](https://www.w3.org/TR/REC-CSS1), [CSS2.1](https://www.w3.org/TR/CSS21/), and [Selectors Level 3](https://www.w3.org/TR/css3-selectors/) specifications, respectively. This module defines Selectors Level 4.

### 1.1. Module Interactions placement)

This module replaces the definitions of and extends the set of selectors defined for CSS in [\[SELECT\]](https://drafts.csswg.org/selectors-4/#biblio-select) and [\[CSS21\]](https://drafts.csswg.org/selectors-4/#biblio-css21).

Pseudo-element selectors, which define abstract elements in a rendering tree, are not part of this specification: their generic syntax is described here, but, due to their close integration with the rendering model and irrelevance to other uses such as DOM queries, they will be defined in other modules.

## 2\. Selectors Overview 

_This section is non-normative, as it merely summarizes the following sections._

A selector represents a structure. This structure can be used as a condition (e.g. in a CSS rule) that determines which elements a selector matches in the document tree, or as a flat description of the HTML or XML fragment corresponding to that structure.

Selectors may range from simple element names to rich contextual representations.

The following table summarizes the Selector syntax:

| Pattern | Represents | Section | Level |
| --- | --- | --- | --- |
| `*` | any element | [§ 5.2 Universal selector](https://drafts.csswg.org/selectors-4/#the-universal-selector) | 2 |
| `E` | an element of type E | [§ 5.1 Type (tag name) selector](https://drafts.csswg.org/selectors-4/#type-selectors) | 1 |
| `E:not(s1, s2, …)` | an E element that does not match either [compound selector](https://drafts.csswg.org/selectors-4/#compound) s1 or compound selector s2 | [§ 4.3 The Negation (Matches-None) Pseudo-class: :not()](https://drafts.csswg.org/selectors-4/#negation) | 3/4 |
| `E:is(s1, s2, …)` | an E element that matches [compound selector](https://drafts.csswg.org/selectors-4/#compound) s1 and/or compound selector s2 | [§ 4.2 The Matches-Any Pseudo-class: :is()](https://drafts.csswg.org/selectors-4/#matches) | 4 |
| `E:where(s1, s2, …)` | an E element that matches [compound selector](https://drafts.csswg.org/selectors-4/#compound) s1 and/or compound selector s2 but contributes no specificity. | [§ 4.4 The Specificity-adjustment Pseudo-class: :where()](https://drafts.csswg.org/selectors-4/#zero-matches) | 4 |
| `E:has(rs1, rs2, …)` | an E element, if either of the [relative selectors](https://drafts.csswg.org/selectors-4/#relative-selector) rs1 or rs2, when evaluated with E as the [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element), match an element | [§ 4.5 The Relational Pseudo-class: :has()](https://drafts.csswg.org/selectors-4/#relational) | 4 |
| `E.warning` | an E element belonging to the class `warning` (the document language specifies how class is determined). | [§ 6.6 Class selectors](https://drafts.csswg.org/selectors-4/#class-html) | 1 |
| `E#myid` | an E element with ID equal to `myid`. | [§ 6.7 ID selectors](https://drafts.csswg.org/selectors-4/#id-selectors) | 1 |
| `E[foo]` | an E element with a `foo` attribute | [§ 6 Attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-selectors) | 2 |
| `E[foo="bar"]` | an E element whose `foo` attribute value is exactly equal to `bar` | [§ 6 Attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-selectors) | 2 |
| `E[foo="bar" i]` | an E element whose `foo` attribute value is exactly equal to any (ASCII-range) case-permutation of `bar` | [§ 6.3 Case-sensitivity](https://drafts.csswg.org/selectors-4/#attribute-case) | 4 |
| `E[foo="bar" s]` | an E element whose `foo` attribute value is exactly and case-sensitively equal to `bar` | [§ 6.3 Case-sensitivity](https://drafts.csswg.org/selectors-4/#attribute-case) | 4 |
| `E[foo~="bar"]` | an E element whose `foo` attribute value is a list of whitespace-separated values, one of which is exactly equal to `bar` | [§ 6 Attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-selectors) | 2 |
| `E[foo^="bar"]` | an E element whose `foo` attribute value begins exactly with the string `bar` | [§ 6.2 Substring matching attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-substrings) | 3 |
| `E[foo$="bar"]` | an E element whose `foo` attribute value ends exactly with the string `bar` | [§ 6.2 Substring matching attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-substrings) | 3 |
| `E[foo*="bar"]` | an E element whose `foo` attribute value contains the substring `bar` | [§ 6.2 Substring matching attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-substrings) | 3 |
| `E[foo|="en"]` | an E element whose `foo` attribute value is a hyphen-separated list of values beginning with `en` | [§ 6 Attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-selectors) | 2 |
| `E:dir(ltr)` | an element of type E with left-to-right directionality (the document language specifies how directionality is determined) | [§ 7.1 The Directionality Pseudo-class: :dir()](https://drafts.csswg.org/selectors-4/#the-dir-pseudo) | 4 |
| `E:lang(zh, "*-hant")` | an element of type E tagged as being either in Chinese (any dialect or writing system) or otherwise written with traditional Chinese characters | [§ 7.2 The Language Pseudo-class: :lang()](https://drafts.csswg.org/selectors-4/#the-lang-pseudo) | 2/4 |
| `E:any-link` | an E element being the source anchor of a hyperlink | [§ 8.1 The Hyperlink Pseudo-class: :any-link](https://drafts.csswg.org/selectors-4/#the-any-link-pseudo) | 4 |
| `E:link` | an E element being the source anchor of a hyperlink of which the target is not yet visited | [§ 8.2 The Link History Pseudo-classes: :link and :visited](https://drafts.csswg.org/selectors-4/#link) | 1 |
| `E:visited` | an E element being the source anchor of a hyperlink of which the target is already visited | [§ 8.2 The Link History Pseudo-classes: :link and :visited](https://drafts.csswg.org/selectors-4/#link) | 1 |
| `E:local-link` | an E element being the source anchor of a hyperlink targetting the current URL | [§ 8.3 The Local Link Pseudo-class: :local-link](https://drafts.csswg.org/selectors-4/#the-local-link-pseudo) | 4 |
| `E:target` | an E element being the target of the current URL | [§ 8.4 The Target Pseudo-class: :target](https://drafts.csswg.org/selectors-4/#the-target-pseudo) | 3 |
| `E:target-within` | an E element that is the target of the current URL or contains an element that does. | [§ 8.5 The Target Container Pseudo-class: :target-within](https://drafts.csswg.org/selectors-4/#the-target-within-pseudo) | 4 |
| `E:scope` | an E element being a designated reference element | [§ 8.6 The Reference Element Pseudo-class: :scope](https://drafts.csswg.org/selectors-4/#the-scope-pseudo) | 4 |
| `E:current` | an E element that is currently presented in a time-dimensional canvas | [§ 10 Time-dimensional Pseudo-classes](https://drafts.csswg.org/selectors-4/#time-pseudos) | 4 |
| `E:current(s)` | an E element that is the deepest [:current](https://drafts.csswg.org/selectors-4/#current-pseudo) element that matches selector s | [§ 10 Time-dimensional Pseudo-classes](https://drafts.csswg.org/selectors-4/#time-pseudos) | 4 |
| `E:past` | an E element that is in the past in a time-dimensional canvas | [§ 10 Time-dimensional Pseudo-classes](https://drafts.csswg.org/selectors-4/#time-pseudos) | 4 |
| `E:future` | an E element that is in the future in a time-dimensional canvas | [§ 10 Time-dimensional Pseudo-classes](https://drafts.csswg.org/selectors-4/#time-pseudos) | 4 |
| `E:active` | an E element that is in an activated state | [§ 9 User Action Pseudo-classes](https://drafts.csswg.org/selectors-4/#useraction-pseudos) | 1 |
| `E:hover` | an E element that is under the cursor, or that has a descendant under the cursor | [§ 9 User Action Pseudo-classes](https://drafts.csswg.org/selectors-4/#useraction-pseudos) | 2 |
| `E:focus` | an E element that has user input focus | [§ 9 User Action Pseudo-classes](https://drafts.csswg.org/selectors-4/#useraction-pseudos) | 2 |
| `E:focus-within` | an E element that has user input focus or contains an element that has input focus. | [§ 9.5 The Focus Container Pseudo-class: :focus-within](https://drafts.csswg.org/selectors-4/#the-focus-within-pseudo) | 4 |
| `E:focus-visible` | an E element that has user input focus, and the UA has determined that a focus ring or other indicator should be drawn for that element | [§ 9 User Action Pseudo-classes](https://drafts.csswg.org/selectors-4/#useraction-pseudos) | 4 |
| `E:enabled  
E:disabled` | a user interface element E that is enabled or disabled, respectively | [§ 12.1.1 The :enabled and :disabled Pseudo-classes](https://drafts.csswg.org/selectors-4/#enableddisabled) | 3 |
| `E:read-write`  
`E:read-only` | a user interface element E that is user alterable, or not | [§ 12.1.2 The Mutability Pseudo-classes: :read-only and :read-write](https://drafts.csswg.org/selectors-4/#rw-pseudos) | 3-UI/4 |
| `E:placeholder-shown` | an input control currently showing placeholder text | [§ 12.1.3 The Placeholder-shown Pseudo-class: :placeholder-shown](https://drafts.csswg.org/selectors-4/#placeholder) | 3-UI/4 |
| `E:default` | a user interface element E that is the default item in a group of related choices | [§ 12.1.4 The Default-option Pseudo-class: :default](https://drafts.csswg.org/selectors-4/#the-default-pseudo) | 3-UI/4 |
| `E:checked` | a user interface element E that is checked/selected (for instance a radio-button or checkbox) | [§ 12.2.1 The Selected-option Pseudo-class: :checked](https://drafts.csswg.org/selectors-4/#checked) | 3 |
| `E:indeterminate` | a user interface element E that is in an indeterminate state (neither checked nor unchecked) | [§ 12.2.2 The Indeterminate-value Pseudo-class: :indeterminate](https://drafts.csswg.org/selectors-4/#indeterminate) | 4 |
| `E:valid`  
`E:invalid` | a user-input element E that meets, or doesn’t, its data validity semantics | [§ 12.3.2 The Validity Pseudo-classes: :valid and :invalid](https://drafts.csswg.org/selectors-4/#validity-pseudos) | 3-UI/4 |
| `E:in-range`  
`E:out-of-range` | a user-input element E whose value is in-range/out-of-range | [§ 12.3.3 The Range Pseudo-classes: :in-range and :out-of-range](https://drafts.csswg.org/selectors-4/#range-pseudos) | 3-UI/4 |
| `E:required`  
`E:optional` | a user-input element E that requires/does not require input | [§ 12.3.4 The Optionality Pseudo-classes: :required and :optional](https://drafts.csswg.org/selectors-4/#opt-pseudos) | 3-UI/4 |
| `E:blank` | a user-input element E whose value is blank (empty/missing) | [§ 12.3.1 The Empty-Value Pseudo-class: :blank](https://drafts.csswg.org/selectors-4/#blank) | 4 |
| `E:user-invalid` | a user-altered user-input element E with incorrect input (invalid, out-of-range, omitted-but-required) | [§ 12.3.5 The User-interaction Pseudo-class: :user-invalid](https://drafts.csswg.org/selectors-4/#user-pseudos) | 4 |
| `E:root` | an E element, root of the document | [§ 13 Tree-Structural pseudo-classes](https://drafts.csswg.org/selectors-4/#structural-pseudos) | 3 |
| `E:empty` | an E element that has no children (neither elements nor text) except perhaps white space | [§ 13 Tree-Structural pseudo-classes](https://drafts.csswg.org/selectors-4/#structural-pseudos) | 3 |
| `E:nth-child(n [of S]?)` | an E element, the n\-th child of its parent matching S | [§ 13.3 Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#child-index) | 3/4 |
| `E:nth-last-child(n [of S]?)` | an E element, the n\-th child of its parent matching S, counting from the last one | [§ 13.3 Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#child-index) | 3/4 |
| `E:first-child` | an E element, first child of its parent | [§ 13.3 Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#child-index) | 2 |
| `E:last-child` | an E element, last child of its parent | [§ 13.3 Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#child-index) | 3 |
| `E:only-child` | an E element, only child of its parent | [§ 13.3 Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#child-index) | 3 |
| `E:nth-of-type(n)` | an E element, the n\-th sibling of its type | [§ 13.4 Typed Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#typed-child-index) | 3 |
| `E:nth-last-of-type(n)` | an E element, the n\-th sibling of its type, counting from the last one | [§ 13.4 Typed Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#typed-child-index) | 3 |
| `E:first-of-type` | an E element, first sibling of its type | [§ 13.4 Typed Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#typed-child-index) | 3 |
| `E:last-of-type` | an E element, last sibling of its type | [§ 13.4 Typed Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#typed-child-index) | 3 |
| `E:only-of-type` | an E element, only sibling of its type | [§ 13.4 Typed Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#typed-child-index) | 3 |
| `E F` | an F element descendant of an E element | [§ 14.1 Descendant combinator ( )](https://drafts.csswg.org/selectors-4/#descendant-combinators) | 1 |
| `E > F` | an F element child of an E element | [§ 14.2 Child combinator (>)](https://drafts.csswg.org/selectors-4/#child-combinators) | 2 |
| `E + F` | an F element immediately preceded by an E element | [§ 14.3 Next-sibling combinator (+)](https://drafts.csswg.org/selectors-4/#adjacent-sibling-combinators) | 2 |
| `E ~ F` | an F element preceded by an E element | [§ 14.4 Subsequent-sibling combinator (~)](https://drafts.csswg.org/selectors-4/#general-sibling-combinators) | 3 |
| `F || E` | an E element that represents a cell in a grid/table belonging to a column represented by an element F | [§ 15 Grid-Structural Selectors](https://drafts.csswg.org/selectors-4/#table-pseudos) | 4 |
| `E:nth-col(n)` | an E element that represents a cell belonging to the nth column in a grid/table | [§ 15 Grid-Structural Selectors](https://drafts.csswg.org/selectors-4/#table-pseudos) | 4 |
| `E:nth-last-col(n)` | an E element that represents a cell belonging to the nth column in a grid/table, counting from the last one | [§ 15 Grid-Structural Selectors](https://drafts.csswg.org/selectors-4/#table-pseudos) | 4 |

Note: Some Level 4 selectors (noted above as "3-UI") were introduced in [\[CSS3UI\]](https://drafts.csswg.org/selectors-4/#biblio-css3ui).

## 3\. Selector Syntax and Structure 

### 3.1. Structure and Terminology 

A selector represents a particular pattern of element(s) in a tree structure. The term [selector](https://drafts.csswg.org/selectors-4/#selector) can refer to a [simple selector](https://drafts.csswg.org/selectors-4/#simple), [compound selector](https://drafts.csswg.org/selectors-4/#compound), [complex selector](https://drafts.csswg.org/selectors-4/#complex), or [selector list](https://drafts.csswg.org/selectors-4/#selector-list). The subject of a selector is any element that selector is defined to be about; that is, any element matching that selector.

A simple selector is a single condition on an element. A [type selector](https://drafts.csswg.org/selectors-4/#type-selector), [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector), [attribute selector](https://drafts.csswg.org/selectors-4/#attribute-selector), [class selector](https://drafts.csswg.org/selectors-4/#class-selector), [ID selector](https://drafts.csswg.org/selectors-4/#id-selector), or [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class) is a [simple selector](https://drafts.csswg.org/selectors-4/#simple). (It is represented by [<simple-selector>](https://drafts.csswg.org/selectors-4/#typedef-simple-selector) in the selectors [grammar](https://drafts.csswg.org/selectors-4/#grammar).) A given element is said to [match](https://drafts.csswg.org/selectors-4/#match) a simple selector when that simple selector, as defined in this specification and in accordance with the [document language](https://drafts.csswg.org/selectors-4/#document-language), accurately describes the element.

A compound selector is a sequence of [simple selectors](https://drafts.csswg.org/selectors-4/#simple) that are not separated by a [combinator](https://drafts.csswg.org/selectors-4/#selector-combinator), and represents a set of simultaneous conditions on a single element. If it contains a [type selector](https://drafts.csswg.org/selectors-4/#type-selector) or [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector), that selector must come first in the sequence. Only one type selector or universal selector is allowed in the sequence. (A [compound selector](https://drafts.csswg.org/selectors-4/#compound) is represented by [<compound-selector>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector) in the selectors [grammar](https://drafts.csswg.org/selectors-4/#grammar).) A given element is said to [match](https://drafts.csswg.org/selectors-4/#match) a compound selector when it matches all simple selectors in the compound selector.

Note: As whitespace represents the [descendant combinator](https://drafts.csswg.org/selectors-4/#descendant-combinator), no whitespace is allowed between the [simple selectors](https://drafts.csswg.org/selectors-4/#simple) in a [compound selector](https://drafts.csswg.org/selectors-4/#compound).

A combinator is a condition of relationship between two elements represented by the [compound selectors](https://drafts.csswg.org/selectors-4/#compound) on either side. Combinators in Selectors Level 4 include: the [descendant combinator](https://drafts.csswg.org/selectors-4/#descendant-combinator) (white space), the [child combinator](https://drafts.csswg.org/selectors-4/#child-combinator) (U+003E, `>`), the [next-sibling combinator](https://drafts.csswg.org/selectors-4/#next-sibling-combinator) (U+002B, `+`), and the [subsequent-sibling combinator](https://drafts.csswg.org/selectors-4/#subsequent-sibling-combinator) (U+007E, `~`). Two given elements are said to [match](https://drafts.csswg.org/selectors-4/#match) a [combinator](https://drafts.csswg.org/selectors-4/#selector-combinator) when the condition of relationship between these elements is true.

A complex selector is a sequence of one or more [compound selectors](https://drafts.csswg.org/selectors-4/#compound) separated by [combinators](https://drafts.csswg.org/selectors-4/#selector-combinator). It represents a set of simultaneous conditions on a set of elements in the particular relationships described by its combinators. (Complex selectors are represented by [<complex-selector>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector) in the selectors [grammar](https://drafts.csswg.org/selectors-4/#grammar).) A given element is said to [match](https://drafts.csswg.org/selectors-4/#match) a [complex selector](https://drafts.csswg.org/selectors-4/#complex) when there exists a list of elements, each matching a corresponding compound selector in the complex selector, with each pair of elements consecutive in the list matching the combinator between their corresponding compound selectors, and with the last element being the given element.

Note: Thus, a selector consisting of a single [compound selector](https://drafts.csswg.org/selectors-4/#compound) matches any element satisfying the requirements of its constituent [simple selectors](https://drafts.csswg.org/selectors-4/#simple). Prepending another compound selector and a [combinator](https://drafts.csswg.org/selectors-4/#selector-combinator) to a sequence imposes additional matching constraints, such that the [subjects](https://drafts.csswg.org/selectors-4/#selector-subject) of a [complex selector](https://drafts.csswg.org/selectors-4/#complex) are always a subset of the elements represented by its last compound selector.

A list of simple/compound/complex selectors is a comma-separated list of [simple](https://drafts.csswg.org/selectors-4/#simple), [compound](https://drafts.csswg.org/selectors-4/#compound), or [complex selectors](https://drafts.csswg.org/selectors-4/#complex). This is also called just a selector list when the type is either unimportant or specified in the surrounding prose; if the type is important and unspecified, it defaults to meaning a [list of complex selectors](https://drafts.csswg.org/selectors-4/#list-of-simple-selectors). (See [§ 4.1 Selector Lists](https://drafts.csswg.org/selectors-4/#grouping) for additional information on [selector lists](https://drafts.csswg.org/selectors-4/#selector-list) and the various <\*-selector-list> productions in the [grammar](https://drafts.csswg.org/selectors-4/#grammar) for their formal syntax.) A given element is said to [match](https://drafts.csswg.org/selectors-4/#match) a selector list when it matches any (at least one) of the [selectors](https://drafts.csswg.org/selectors-4/#selector) in that selector list.

 issue-5830d0c1)Pseudo-elements aren’t handled here, and should be.

### 3.2. Data Model 
Selectors are evaluated against an element tree such as the DOM. [\[DOM\]](https://drafts.csswg.org/selectors-4/#biblio-dom) Within this specification, this may be referred to as the "document tree" or "source document".

Each element may have any of the following five aspects, which can be selected against, all of which are matched as strings:

- The element’s type (also known as its tag name).
- The element’s namespace.
- An ID.
- Classes (named groups) to which it belongs.
- Attributes, which are name-value pairs.

While individual elements may lack any of the above features, some elements are featureless. A [featureless](https://drafts.csswg.org/selectors-4/#featureless) element does not match any selector at all, except those it is explicitly defined to match. If a given selector _is_ allowed to match a featureless element, it must do so while ignoring the default namespace. [\[CSS3NAMESPACE\]](https://drafts.csswg.org/selectors-4/#biblio-css3namespace)

 example-76c361e3)For example, the [shadow host](https://dom.spec.whatwg.org/#element-shadow-host) in a [shadow tree](https://dom.spec.whatwg.org/#concept-shadow-tree) is [featureless](https://drafts.csswg.org/selectors-4/#featureless), and can’t be matched by _any_ [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class) except for [:host](https://drafts.csswg.org/css-scoping-1/#selectordef-host) and [:host-context()](https://drafts.csswg.org/css-scoping-1/#selectordef-host-context).)

Many of the selectors depend on the semantics of the document language (i.e. the language and semantics of the document tree) and/or the semantics of the host language (i.e. the language that is using selectors syntax). For example, the [:lang()](https://drafts.csswg.org/selectors-4/#lang-pseudo) selector depends on the [document language](https://drafts.csswg.org/selectors-4/#document-language) (e.g. HTML) to define how an element is associated with a language. As a slightly different example, the [::first-line](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-line) pseudo-element depends on the [host language](https://drafts.csswg.org/selectors-4/#host-language) (e.g. CSS) to define what a ::first-line pseudo-element represents and what it can do.

### 3.3. Scoped Selectors 

Some host applications may choose to scope selectors to a particular subtree or fragment of the document. The root of the scoping subtree is called the scoping root, and may be either a true element (the scoping element scoping-element)) or a virtual one (such as a [DocumentFragment](https://dom.spec.whatwg.org/#documentfragment)).

When a selector is [scoped](https://drafts.csswg.org/selectors-4/#scoped-selector), it matches an element only if the element is a descendant of the [scoping root](https://drafts.csswg.org/selectors-4/#scoping-root). (The rest of the selector can match unrestricted; it’s only the final matched elements that must be within the scope.)

 example-d2142ebe)For example, the `element.querySelector()` function defined in [\[DOM\]](https://drafts.csswg.org/selectors-4/#biblio-dom) allows the author to evaluate a [scoped](https://drafts.csswg.org/selectors-4/#scoped-selector) selector relative to the `element` it’s called on.

A call like `widget.querySelector("a")` will thus only find `[a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element)` elements inside of the `widget` element, ignoring any other `[a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element)`s that might be scattered throughout the document.

Note: If the context does not explicitly define any [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element) for the selector, the [scoping root](https://drafts.csswg.org/selectors-4/#scoping-root) is the :scope element.

### 3.4. Relative Selectors 

Certain contexts may accept relative selectors, which are a shorthand for selectors that represent elements relative to a [:scope element](https://drafts.csswg.org/selectors-4/#scope-element) (i.e. an element that matches [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo)). In a [relative selector](https://drafts.csswg.org/selectors-4/#relative-selector), “:scope ” (the :scope pseudo-class followed by a space) is implied at the beginning of each [complex selector](https://drafts.csswg.org/selectors-4/#complex) that does not already contain the :scope pseudo-class. This allows the selector to begin syntactically with a [combinator](https://drafts.csswg.org/selectors-4/#selector-combinator). However, it must be [absolutized](https://drafts.csswg.org/selectors-4/#absolutize) before matching.

Relative selectors, once absolutized, can additionally be [scoped](https://drafts.csswg.org/selectors-4/#scoped-selector).

Relative selectors are represented by [<relative-selector>](https://drafts.csswg.org/selectors-4/#typedef-relative-selector) in the selectors [grammar](https://drafts.csswg.org/selectors-4/#grammar).

#### 3.4.1. Absolutizing a Relative Selector 

To absolutize a relative selector:

If there are no [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element) and the selector is [scoped](https://drafts.csswg.org/selectors-4/#scoped-selector) to a [virtual scoping root](https://drafts.csswg.org/selectors-4/#virtual-scoping-root):

 issue-28dbdaca)[This needs a sane definition.](https://github.com/w3c/csswg-drafts/issues/2199)

Otherwise:

1. If the selector starts with a [combinator](https://drafts.csswg.org/selectors-4/#selector-combinator) other than the white space form of the [descendant combinator](https://drafts.csswg.org/selectors-4/#descendant-combinator), prepend [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo) as the initial [compound selector](https://drafts.csswg.org/selectors-4/#compound).
2. Otherwise, if the selector does not contain any instance of the [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo) pseudo-class (either at the top-level or as an argument to a functional pseudo-class), prepend :scope followed by the white space form of the [descendant combinator](https://drafts.csswg.org/selectors-4/#descendant-combinator).
3. Otherwise, the selector is already absolute.

To absolutize a relative selector list, absolutize each relative selector in the list.

### 3.5. Pseudo-classes 

Pseudo-classes are [simple selectors](https://drafts.csswg.org/selectors-4/#simple) that permit selection based on information that lies outside of the document tree or that can be awkward or impossible to express using the other simple selectors. They can also be dynamic, in the sense that an element can acquire or lose a pseudo-class while a user interacts with the document, without the document itself changing. [Pseudo-classes](https://drafts.csswg.org/selectors-4/#pseudo-class) do not appear in or modify the document source or document tree.

The syntax of a [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class) consists of a ":" (U+003A COLON) followed by the name of the pseudo-class as a CSS [identifier](https://drafts.csswg.org/css-syntax-3/#identifier), and, in the case of a functional pseudo-class, a pair of parentheses containing its arguments.

 example-86ae2021)For example, [:valid](https://drafts.csswg.org/selectors-4/#valid-pseudo) is a regular pseudo-class, and [:lang()](https://drafts.csswg.org/selectors-4/#lang-pseudo) is a [functional pseudo-class](https://drafts.csswg.org/selectors-4/#functional-pseudo-class).

Like all CSS keywords, [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class) names are [ASCII case-insensitive](https://infra.spec.whatwg.org/#ascii-case-insensitive). No [white space](https://drafts.csswg.org/selectors-4/#whitespace) is allowed between the colon and the name of the pseudo-class, nor, as usual for CSS syntax, between a [functional pseudo-class](https://drafts.csswg.org/selectors-4/#functional-pseudo-class)’s name and its opening parenthesis (which thus form a CSS function token). Also as usual, white space is allowed around the arguments inside the parentheses of a functional pseudo-class unless otherwise specified.

Like other [simple selectors](https://drafts.csswg.org/selectors-4/#simple), [pseudo-classes](https://drafts.csswg.org/selectors-4/#pseudo-class) are allowed in all [compound selectors](https://drafts.csswg.org/selectors-4/#compound) contained in a selector, and must follow the [type selector](https://drafts.csswg.org/selectors-4/#type-selector) or [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector), if present.

Note: Some [pseudo-classes](https://drafts.csswg.org/selectors-4/#pseudo-class) are mutually exclusive (such that a [compound selector](https://drafts.csswg.org/selectors-4/#compound) containing them, while valid, will never match anything), while others can apply simultaneously to the same element.

### 3.6. Pseudo-elements
Similar to how certain [pseudo-classes](https://drafts.csswg.org/selectors-4/#pseudo-class) represent additional state information not directly present in the document tree, a pseudo-element represents an _element_ not directly present in the document tree. They are used to create abstractions about the document tree beyond those provided by the document tree. For example, pseudo-elements can be used to select portions of the document that do not correspond to a document-language element (including such ranges as don’t align to element boundaries or fit within its tree structure); that represent content not in the document tree or in an alternate projection of the document tree; or that rely on information provided by styling, layout, user interaction, and other processes that are not reflected in the document tree.

 example-6916597f)For instance, document languages do not offer mechanisms to access the first letter or first line of an element’s content, but there exist [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) ([::first-letter](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-letter) and [::first-line](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-line)) that allow those things to be styled. Notice especially that in the case of ::first-line, which portion of content is represented by the pseudo-element depends on layout information that cannot be inferred from the document tree.

[Pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) can also represent content that doesn’t exist in the source document at all, such as the [::before](https://drafts.csswg.org/css-pseudo-4/#selectordef-before) and [::after](https://drafts.csswg.org/css-pseudo-4/#selectordef-after) pseudo-elements which allow additional content to be inserted before or after the contents of any element.

Like [pseudo-classes](https://drafts.csswg.org/selectors-4/#pseudo-class) [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) do not appear in or modify the document source or document tree. Accordingly, they also do not affect the interpretation of [structural pseudo-classes](https://drafts.csswg.org/selectors-4/#structural-pseudo-classes) or other selectors pertaining to their [originating element](https://drafts.csswg.org/selectors-4/#originating-element) or its tree.

The host language defines which pseudo-elements exist, their type, and their abilities. Pseudo-elements that exist in CSS are defined in [\[CSS21\]](https://drafts.csswg.org/selectors-4/#biblio-css21) (Level 2), [\[SELECT\]](https://drafts.csswg.org/selectors-4/#biblio-select) (Level 3), and [\[CSS-PSEUDO-4\]](https://drafts.csswg.org/selectors-4/#biblio-css-pseudo-4) (Level 4).

#### 3.6.1. Syntax pseudo-element

The syntax of a [pseudo-element](https://drafts.csswg.org/selectors-4/#pseudo-element) is "::" (two U+003A COLON characters) followed by the name of the pseudo-element as an [identifier](https://drafts.csswg.org/css-syntax-3/#identifier). Pseudo-element names are [ASCII case-insensitive](https://infra.spec.whatwg.org/#ascii-case-insensitive). No [white space](https://drafts.csswg.org/selectors-4/#whitespace) is allowed between the two colons, or between the colons and the name.

Because [CSS Level 1](https://www.w3.org/TR/CSS1) and [CSS Level 2](https://www.w3.org/TR/CSS2) conflated pseudo-elements and pseudo-classes by sharing a single-colon syntax for both, user agents must also accept the previous one-colon notation for the Level 1 & 2 pseudo-elements ([::before](https://drafts.csswg.org/css-pseudo-4/#selectordef-before), [::after](https://drafts.csswg.org/css-pseudo-4/#selectordef-after), [::first-line](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-line), and [::first-letter](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-letter)). This compatibility notation is not allowed any other [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element). However, as this syntax is deprecated, authors should use the Level 3+ double-colon syntax for these pseudo-elements.

[Pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) are [featureless](https://drafts.csswg.org/selectors-4/#featureless), and so can’t be matched by any other selector.

#### 3.6.2. Binding to the Document Tree 

[Pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) do not exist independently in the tree: they are always bound to another element on the page, called their originating element. Syntactically, a pseudo-element immediately follows the [compound selector](https://drafts.csswg.org/selectors-4/#compound) representing its [originating element](https://drafts.csswg.org/selectors-4/#originating-element). If this compound selector is omitted, it is assumed to be the [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector) [\*](https://drafts.csswg.org/selectors-3/#x).

 example-e6d9ca44)For example, in the selector div a::before, the a elements matched by the selector are the [originating elements](https://drafts.csswg.org/selectors-4/#originating-element) for the [::before](https://drafts.csswg.org/css-pseudo-4/#selectordef-before) pseudo-elements attached to them.

The selector [::first-line](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-line) is equivalent to \*::first-line, which selects the ::first-line pseudo-element on _every_ element in the document.

When a [pseudo-element](https://drafts.csswg.org/selectors-4/#pseudo-element) is encountered in a selector, the part of the selector before the pseudo-element selects the [originating element](https://drafts.csswg.org/selectors-4/#originating-element) for the pseudo-element; the part of the selector after it, if any, applies to the pseudo-element itself. (See below.)

#### 3.6.3. Pseudo-classing Pseudo-elements

A [pseudo-element](https://drafts.csswg.org/selectors-4/#pseudo-element) may be immediately followed by any combination of the [user action pseudo-classes](https://drafts.csswg.org/selectors-4/#useraction-pseudos), in which case the pseudo-element is represented only when it is in the corresponding state. Whether these pseudo-classes can match on the pseudo-element depends on the [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class) and pseudo-element’s definitions: unless otherwise-specified, none of these pseudo-classes will match on the pseudo-element.

 issue-9f34fdb4)Clarify that [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo) and [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo) can be used when containing above-mentioned pseudos.

 example-01167664)For example, since the [:hover](https://drafts.csswg.org/selectors-4/#hover-pseudo) pseudo-class specifies that it can apply to any pseudo-element, ::first-line:hover will match when the first line is hovered. However, since neither [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo) nor [::first-line](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-line) define that :focus can apply to ::first-line, the selector ::first-line:focus will never match anything.

 issue-27c4806a)Does ::first-line:not(:focus) match anything?

Notice that ::first-line:hover is very different from :hover::first-line, which matches the first line of any originating element that is hovered! For example, :hover::first-line also matches the first line of a paragraph when the second line of the paragraph is hovered, whereas ::first-line:hover only matches if the first line itself is hovered.

Note: Note that, unless otherwise specified in a future specification, pseudo-classes other than the [user action pseudo-classes](https://drafts.csswg.org/selectors-4/#useraction-pseudos) are not valid when compounded to a pseudo-element; so, for example, ::before:first-child is an invalid selector.

#### 3.6.4. Internal Structure pseudo-element-structure)

Some [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) are defined to have internal structure. These pseudo-elements may be followed by child/descendant combinators to express those relationships. Selectors containing [combinators](https://drafts.csswg.org/selectors-4/#selector-combinator) after the pseudo-element are otherwise invalid.

 example-ed91d05b)For example, ::first-letter + span and ::first-letter em are invalid selectors. However, since [::shadow](https://www.w3.org/TR/css-scoping-1/#selectordef-shadow) is defined to have internal structure, ::shadow > p is a valid selector.

Note: A future specification may expand the capabilities of existing pseudo-elements, so some of these currently-invalid selectors (e.g. ::first-line :any-link) may become valid in the future.

The children of such [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) can simultaneously be children of other elements, too. However, at least in CSS, their rendering must be defined so as to maintain the tree-ness of the [box tree](https://drafts.csswg.org/css-display-3/#box-tree).

 example-5dddce2e)For example, the [::content](https://www.w3.org/TR/css-scoping-1/#selectordef-content) pseudo-element treats elements distributed to it as its children. This means that, given the following fragment:

<div>
  <span>foo</span>
  <"shadow root">
    <content></content>
  </"shadow root">
</div>

the selectors div > span and div::shadow ::content > span select the same element via different paths.

However, when rendered, the `<span>` element generates boxes as if it were the child of the `<content>` element, rather than the `<div>` element, so the tree structure of the [box tree](https://drafts.csswg.org/css-display-3/#box-tree) is maintained.

### 3.7. Characters and case sensitivity case-sensitive)

All Selectors syntax is [ASCII case-insensitive](https://infra.spec.whatwg.org/#ascii-case-insensitive) (i.e. \[a-z\] and \[A-Z\] are equivalent), except for the parts that are not under the control of Selectors: specifically, the case-sensitivity of document language element names, attribute names, and attribute values depends on the document language.

 example-5ac03fca)For example, [in HTML, element and attribute names are ASCII case-insensitive](https://html.spec.whatwg.org/multipage/semantics-other.html#selectors), but in XML, they are case-sensitive.

Case sensitivity of namespace prefixes is defined in [\[CSS3NAMESPACE\]](https://drafts.csswg.org/selectors-4/#biblio-css3namespace). Case sensitivity of [language ranges](https://drafts.csswg.org/selectors-4/#language-range) is defined in the [:lang()](https://drafts.csswg.org/selectors-4/#lang-pseudo) section.

White space in Selectors consists of the code points SPACE (U+0020), TAB (U+0009), LINE FEED (U+000A), CARRIAGE RETURN (U+000D), and FORM FEED (U+000C). Other space-like code points, such as EM SPACE (U+2003) and IDEOGRAPHIC SPACE (U+3000), are never considered syntactic white space.

Code points in Selectors can be escaped with a backslash according to the same [escaping rules](https://www.w3.org/TR/CSS21/syndata.html#characters) as CSS. [\[CSS21\]](https://drafts.csswg.org/selectors-4/#biblio-css21) Note that escaping a code point “cancels out” any special meaning it may have in Selectors. For example, the selector #foo>a contains a combinator, but #foo\\>a instead selects an element with the id `foo>a`.

### 3.8. Declaring Namespace Prefixes namespaces)

Certain selectors support namespace prefixes. The mechanism by which namespace prefixes are declared should be specified by the language that uses Selectors. If the language does not specify a namespace prefix declaration mechanism, then no prefixes are declared. In CSS, namespace prefixes are declared with the @namespace rule. [\[CSS3NAMESPACE\]](https://drafts.csswg.org/selectors-4/#biblio-css3namespace)

### 3.9. Invalid Selectors and Error Handling invalid)

User agents must observe the rules for handling invalid selectors:

- a parsing error in a selector, e.g. an unrecognized token or a token which is not allowed at the current parsing point (see overall [§ 17 Grammar](https://drafts.csswg.org/selectors-4/#grammar) and per-selector syntax definitions), causes that selector to be invalid.
- a simple selector containing an [undeclared namespace prefix](https://drafts.csswg.org/selectors-4/#namespaces) is invalid
- a selector containing an invalid simple selector, an invalid combinator or an invalid token is invalid.
- a selector list containing an invalid selector is invalid.
- an empty selector, i.e. one that contains no [compound selector](https://drafts.csswg.org/selectors-4/#compound), is invalid.

Note: Consistent with CSS’s forwards-compatible parsing principle, UAs _must_ treat as [invalid](https://drafts.csswg.org/selectors-4/#invalid-selector) any pseudo-classes, pseudo-elements, combinators, or other syntactic constructs for which they have no usable level of support. See [Partial Implementations](https://drafts.csswg.org/selectors-4/#conform-partial).

An [invalid selector](https://drafts.csswg.org/selectors-4/#invalid-selector) represents, and therefore matches, nothing.

## 4\. Logical Combinations logical-combination)

### 4.1. Selector Lists grouping)

**✔**MDN

[Selector\_list](https://developer.mozilla.org/en-US/docs/Web/CSS/Selector_list "The CSS selector list (,) selects all the matching nodes.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE3+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

A comma-separated list of selectors represents the union of all elements selected by each of the individual selectors in the [selector list](https://drafts.csswg.org/selectors-4/#selector-list). (A comma is U+002C.) For example, in CSS when several selectors share the same declarations, they may be grouped into a comma-separated list. White space may appear before and/or after the comma.

 example-1930da7e)CSS example: In this example, we condense three rules with identical declarations into one. Thus,

h1 { font-family: sans-serif }
h2 { font-family: sans-serif }
h3 { font-family: sans-serif }

is equivalent to:

h1, h2, h3 { font-family: sans-serif }

**Warning**: the equivalence is true in this example because all the selectors are valid selectors. If just one of these selectors were invalid, the entire [selector list](https://drafts.csswg.org/selectors-4/#selector-list) would be invalid. This would invalidate the rule for all three heading elements, whereas in the former case only one of the three individual heading rules would be invalidated.

 example-fd0daa05)Invalid CSS example:

h1 { font-family: sans-serif }
h2..foo { font-family: sans-serif }
h3 { font-family: sans-serif }

is not equivalent to:

h1, h2..foo, h3 { font-family: sans-serif } 

because the above selector (h1, h2..foo, h3) is entirely invalid and the entire style rule is dropped. (When the selectors are not grouped, only the rule for h2..foo is dropped.)

### 4.2. The Matches-Any Pseudo-class: [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo) matches)

MDN

[:is](https://developer.mozilla.org/en-US/docs/Web/CSS/:is "The :is() CSS pseudo-class function takes a selector list as its argument, and selects any element that can be selected by one of the selectors in that list. This is useful for writing large selectors in a more compact form.")

Firefox78+Safari?Chrome68+

-

Opera55+Edge79+

-

Edge (Legacy)NoneIENone

-

Firefox for AndroidNoneiOS Safari?Chrome for Android?Android WebViewNoneSamsung Internet?Opera Mobile48+

The matches-any pseudo-class, :is(), is a functional pseudo-class taking a [<forgiving-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-selector-list) as its sole argument.

If the argument, after parsing, is an empty list, the pseudo-class is valid but matches nothing. Otherwise, the pseudo-class matches any element that matches any of the selectors in the list.

Note: The specificity of the [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo) pseudo-class is replaced by the specificity of its most specific argument. Thus, a selector written with :is() does not necessarily have equivalent specificity to the equivalent selector written without :is() For example, if we have :is(ul, ol, .list) > \[hidden\] and ul > \[hidden\], ol > \[hidden\], .list > \[hidden\] a \[hidden\] child of an `[ol](https://html.spec.whatwg.org/multipage/grouping-content.html#the-ol-element)` matches the first selector with a specificity of (0,2,0) whereas it matches the second selector with a specificity of (0,1,1). See [§ 16 Calculating a selector’s specificity](https://drafts.csswg.org/selectors-4/#specificity-rules).

Pseudo-elements cannot be represented by the matches-any pseudo-class; they are not valid within [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo).

Default namespace declarations do not affect the [compound selector](https://drafts.csswg.org/selectors-4/#compound) representing the [subject](https://drafts.csswg.org/selectors-4/#selector-subject) of any selector within a [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo) pseudo-class, unless that compound selector contains an explicit [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector) or [type selector](https://drafts.csswg.org/selectors-4/#type-selector).

 example-2cab03ed)For example, the following selector matches any element that is being hovered or focused, regardless of its namespace. In particular, it is not limited to only matching elements in the default namespace that are being hovered or focused.

\*|\*:is(:hover, :focus) 

The following selector, however, represents only hovered or focused elements that are in the default namespace, because it uses an explicit universal selector within the [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo) notation:

\*|\*:is(\*:hover, \*:focus) 

As previous drafts of this specification used the name :matches() for this pseudo-class, UAs may additionally implement this obsolete name as an alias for [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo) if needed for backwards-compatibility.

### 4.3. The Negation (Matches-None) Pseudo-class: [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo) negation)

**✔**MDN

[:not](https://developer.mozilla.org/en-US/docs/Web/CSS/:not "The :not() CSS pseudo-class represents elements that do not match a list of selectors. Since it prevents specific items from being selected, it is known as the negation pseudo-class.")

In all current engines.

Firefox1+Safari3.2+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.2+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

The negation pseudo-class, :not(), is a functional pseudo-class taking a [selector list](https://drafts.csswg.org/selectors-4/#selector-list) as an argument. It represents an element that is not represented by its argument.

Note: In Selectors Level 3, only a single [simple selector](https://drafts.csswg.org/selectors-4/#simple) was allowed as the argument to [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo).

Note: The specificity of the [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo) pseudo-class is replaced by the specificity of the most specific selector in its argument; thus it has the exact behavior of :not(:is(argument)). See [§ 16 Calculating a selector’s specificity](https://drafts.csswg.org/selectors-4/#specificity-rules).

Pseudo-elements cannot be represented by the negation pseudo-class; they are not valid within [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo).

 example-2a176618)For example, the following selector matches all [button](https://html.spec.whatwg.org/multipage/form-elements.html#the-button-element) elements in an HTML document that are not disabled.

button:not(\[DISABLED\]) 

The following selector represents all but FOO elements.

\*:not(FOO)

The following compound selector represents all HTML elements except links.

html|\*:not(:link):not(:visited)

As with [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo), default namespace declarations do not affect the [compound selector](https://drafts.csswg.org/selectors-4/#compound) representing the [subject](https://drafts.csswg.org/selectors-4/#selector-subject) of any selector within a [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo) pseudo-class, unless that compound selector contains an explicit [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector) or [type selector](https://drafts.csswg.org/selectors-4/#type-selector). (See :is() for examples.)

Note: The [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo) pseudo-class allows useless selectors to be written. For instance :not(\*|\*), which represents no element at all, or div:not(span), which is equivalent to div but with a higher specificity.

### 4.4. The Specificity-adjustment Pseudo-class: [:where()](https://drafts.csswg.org/selectors-4/#where-pseudo) zero-matches)

MDN

[:where](https://developer.mozilla.org/en-US/docs/Web/CSS/:where "The :where() CSS pseudo-class function takes a selector list as its argument, and selects any element that can be selected by one of the selectors in that list.")

Firefox78+SafariNoneChrome🔰 72+

-

OperaNoneEdge🔰 79+

-

Edge (Legacy)NoneIENone

-

Firefox for AndroidNoneiOS SafariNoneChrome for Android🔰 72+Android WebViewNoneSamsung InternetNoneOpera MobileNone

The Specificity-adjustment pseudo-class, :where(), is a functional pseudo-class with the same syntax and functionality as [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo). Unlike :is(), neither the [:where()](https://drafts.csswg.org/selectors-4/#where-pseudo) pseudo-class, nor any of its arguments, contribute to the specificity of the selector—its specificity is always zero.

This is useful for introducing filters in a selector while keeping the associated style declarations easy to override.

 example-7ca50acf)Below is a common example where the specificity heuristic fails to match author expectations:

a:not(:hover) {
  text-decoration: none;
}

nav a {
  /\* Has no effect \*/
  text-decoration: underline;
}

However, by using [:where()](https://drafts.csswg.org/selectors-4/#where-pseudo) the author can explicitly declare their intent:

a:where(:not(:hover)) {
  text-decoration: none;
}

nav a {
  /\* Works now! \*/
  text-decoration: underline;
}

Note: Future levels of Selectors may introduce an additional argument to explicitly set the specificity of that instance of the pseudo-class.

### 4.5. The Relational Pseudo-class: [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo) relational)

**⚠**MDN

[:has](https://developer.mozilla.org/en-US/docs/Web/CSS/:has "The :has() CSS pseudo-class represents an element if any of the selectors passed as parameters (relative to the :scope of the given element) match at least one element.")

In no current engines.

FirefoxNoneSafariNoneChromeNone

-

OperaNoneEdgeNone

-

Edge (Legacy)NoneIENone

-

Firefox for AndroidNoneiOS SafariNoneChrome for AndroidNoneAndroid WebViewNoneSamsung InternetNoneOpera MobileNone

The relational pseudo-class, :has(), is a functional pseudo-class taking a [<forgiving-relative-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-relative-selector-list) as an argument. It represents an element if any of the [relative selectors](https://drafts.csswg.org/selectors-4/#relative-selector), when [absolutized](https://drafts.csswg.org/selectors-4/#absolutize) and evaluated with the element as the [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element), would match at least one element.

 example-8c66af53)For example, the following selector matches only `<a>` elements that contain an `<img>` child:

a:has(> img)

The following selector matches a `<dt>` element immediately followed by another `<dt>` element:

dt:has(+ dt)

The following selector matches `<section>` elements that don’t contain any heading elements:

section:not(:has(h1, h2, h3, h4, h5, h6))

Note that ordering matters in the above selector. Swapping the nesting of the two pseudo-classes, like:

section:has(:not(h1, h2, h3, h4, h5, h6))

...would result matching any `<section>` element which contains anything that’s not a heading element.

Supporting the [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo) pseudo-class is not required to conform to this specification.

## 5\. Elemental selectors elemental-selectors)

### 5.1. Type (tag name) selector type-selectors)

**✔**MDN

[Type\_selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Type_selectors "The CSS type selector matches elements by node name. In other words, it selects all elements of the given type within a document.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE3+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

A type selector is the name of a document language element type, and represents an instance of that element type in the document tree.

 example-087f4a77)For example, the selector h1 represents an h1 element in the document.

A [type selector](https://drafts.csswg.org/selectors-4/#type-selector) is written as a [CSS qualified name](https://drafts.csswg.org/css-namespaces-3/#css-qualified-name): an [identifier](https://drafts.csswg.org/css-syntax-3/#identifier) with an optional namespace prefix. [\[CSS3NAMESPACE\]](https://drafts.csswg.org/selectors-4/#biblio-css3namespace) (See [§ 5.3 Namespaces in Elemental Selectors](https://drafts.csswg.org/selectors-4/#type-nmsp).)

### 5.2. Universal selector the-universal-selector)

**✔**MDN

[Universal\_selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors "The CSS universal selector (*) matches elements of any type.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE7+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The universal selector is a special [type selector](https://drafts.csswg.org/selectors-4/#type-selector), that represents an element of any element type.

It is written as a [CSS qualified name](https://drafts.csswg.org/css-namespaces-3/#css-qualified-name) with an asterisk (`*` U+002A) as the local name. Like a [type selector](https://drafts.csswg.org/selectors-4/#type-selector), the [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector) can be qualified by a namespace, restricting it to only elements belonging to that namespace, and is affected by a default namespace as defined in [§ 5.3 Namespaces in Elemental Selectors](https://drafts.csswg.org/selectors-4/#type-nmsp).

Unless an element is [featureless](https://drafts.csswg.org/selectors-4/#featureless), the presence of a [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector) has no effect on whether the element matches the selector. (Featureless elements do not match any selector, including the universal selector.)

 example-0f5d51ca)

- \*\[hreflang|=en\] and \[hreflang|=en\] are equivalent,
- \*.warning and .warning are equivalent,
- \*#myid and #myid are equivalent.

The [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector) follows the same syntax rules as other [type selectors](https://drafts.csswg.org/selectors-4/#type-selector): only one can appear per [compound selector](https://drafts.csswg.org/selectors-4/#compound), and it must be the first [simple selector](https://drafts.csswg.org/selectors-4/#simple) in the compound selector.

Note: In some cases, adding a [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector) can make a selector easier to read, even though it has no effect on the matching behavior. For example, div :first-child and div:first-child are somewhat difficult to tell apart at a quick glance, but writing the former as div \*:first-child makes the difference obvious.

### 5.3. Namespaces in Elemental Selectors type-nmsp)

[Type selectors](https://drafts.csswg.org/selectors-4/#type-selector) and [universal selectors](https://drafts.csswg.org/selectors-4/#universal-selector) allow an optional namespace component: a namespace prefix that has been previously [declared](https://drafts.csswg.org/selectors-4/#nsdecl) may be prepended to the element name separated by the namespace separator “vertical bar” (`|` U+007C). (See, e.g., [\[XML-NAMES\]](https://drafts.csswg.org/selectors-4/#biblio-xml-names) for the use of namespaces in XML.) It has the following meaning in each form:

`ns|E`

elements with name E in namespace ns

`*|E`

elements with name E in any namespace, including those without a namespace

`|E`

elements with name E without a namespace

`E`

if no default namespace has been [declared](https://drafts.csswg.org/selectors-4/#nsdecl) for selectors, this is equivalent to \*|E. Otherwise it is equivalent to ns|E where ns is the default namespace.

 example-53e1ab95)CSS examples:

@namespace foo url(http://www.example.com);
foo|h1 { color: blue }  /\* first rule \*/
foo|\* { color: yellow } /\* second rule \*/
|h1 { color: red }      /\* ...\*/
\*|h1 { color: green }
h1 { color: green }

The first rule (not counting the @namespace at-rule) will match only h1 elements in the "http://www.example.com" namespace.

The second rule will match all elements in the "http://www.example.com" namespace.

The third rule will match only h1 elements with no namespace.

The fourth rule will match h1 elements in any namespace (including those without any namespace).

The last rule is equivalent to the fourth rule because no default namespace has been defined.

If a [default namespace](https://drafts.csswg.org/css-namespaces-3/#default-namespace) is declared, [compound selectors](https://drafts.csswg.org/selectors-4/#compound) without [type selectors](https://drafts.csswg.org/selectors-4/#type-selector) in them still only match elements in that default namespace.

 example-03281ceb)For example, in the following style sheet:

@namespace url("http://example.com/foo");

.special { ... }

The .special selector only matches elements in the "http://example.com/foo" namespace, even though no reference to the type name (which is paired with the namespace in the DOM) appeared.

A [type selector](https://drafts.csswg.org/selectors-4/#type-selector) or [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector) containing a namespace prefix that has not been previously [declared](https://drafts.csswg.org/selectors-4/#nsdecl) is an [invalid selector](https://drafts.csswg.org/selectors-4/#invalid-selector).

### 5.4. The Defined Pseudo-class: [:defined](https://drafts.csswg.org/selectors-4/#defined-pseudo) the-defined-pseudo)

In some host languages, elements can have a distinction between being “defined”/“constructed” or not. The :defined [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class) matches elements that are fully defined, as dictated by the host language.

If the host language does not have this sort of distinction, all elements in it match [:defined](https://drafts.csswg.org/selectors-4/#defined-pseudo).

 example-cd9dcdb2)In HTML, all built-in elements are always considered to be defined, so the following example will always match:

p:defined { ... }

[Custom elements](https://html.spec.whatwg.org/multipage/custom-elements.html#custom-element), on the other hand, start out _un_defined, and only become defined when [properly registered](https://html.spec.whatwg.org/multipage/custom-elements.html#element-definition). This means the [:defined](https://drafts.csswg.org/selectors-4/#defined-pseudo) pseudo-class can be used to hide a custom element until it has been registered:

custom-element { visibility: hidden }

custom-element:defined { visibility: visible }

## 6\. Attribute selectors attribute-selectors)

**✔**MDN

[Attribute\_selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors "The CSS attribute selector matches elements based on the presence or value of a given attribute.")

In all current engines.

Firefox1+Safari3+Chrome1+

-

Opera9+Edge79+

-

Edge (Legacy)12+IE7+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile14+

Selectors allow the representation of an element’s attributes. When a selector is used as an expression to match against an element, an attribute selector must be considered to match an element if that element has an attribute that matches the attribute represented by the attribute selector.

 issue-745ef775)Add comma-separated syntax for [multiple-value matching](http://lists.w3.org/Archives/Public/www-style/2011Mar/0215.html)? e.g. \[rel ~= next, prev, up, first, last\]

### 6.1. Attribute presence and value selectors attribute-representation)

CSS2 introduced four attribute selectors:

\[att\]

Represents an element with the `att` attribute, whatever the value of the attribute.

\[att=val\]

Represents an element with the `att` attribute whose value is exactly "val".

\[att~=val\]

Represents an element with the `att` attribute whose value is a [whitespace](https://drafts.csswg.org/selectors-4/#whitespace)\-separated list of words, one of which is exactly "val". If "val" contains whitespace, it will never represent anything (since the words are _separated_ by spaces). Also if "val" is the empty string, it will never represent anything.

\[att|=val\]

Represents an element with the `att` attribute, its value either being exactly "val" or beginning with "val" immediately followed by "-" (U+002D). This is primarily intended to allow language subcode matches (e.g., the `hreflang` attribute on the [a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element) element in HTML) as described in BCP 47 ([\[BCP47\]](https://drafts.csswg.org/selectors-4/#biblio-bcp47)) or its successor. For `lang` (or `xml:lang`) language subcode matching, please see the [:lang](https://drafts.csswg.org/css2/#selectordef-lang) pseudo-class.

Attribute values must be [<ident-token>](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token)s or [<string-token>](https://drafts.csswg.org/css-syntax-3/#typedef-string-token)s. [\[CSS3SYN\]](https://drafts.csswg.org/selectors-4/#biblio-css3syn)

 example-52ee808b)Examples:

The following attribute selector represents an h1 element that carries the `title` attribute, whatever its value:

h1\[title\]

In the following example, the selector represents a [span](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-span-element) element whose `class` attribute has exactly the value "example":

span\[class="example"\]

Multiple attribute selectors can be used to represent several attributes of an element, or several conditions on the same attribute. Here, the selector represents a [span](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-span-element) element whose `hello` attribute has exactly the value "Cleveland" and whose `goodbye` attribute has exactly the value "Columbus":

span\[hello="Cleveland"\]\[goodbye="Columbus"\]

The following CSS rules illustrate the differences between "=" and "~=". The first selector would match, for example, an [a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element) element with the value "copyright copyleft copyeditor" on a `rel` attribute. The second selector would only match an a element with an `href` attribute having the exact value "http://www.w3.org/".

a\[rel~="copyright"\] { ... }
a\[href="http://www.w3.org/"\] { ... }

The following selector represents an [a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element) element whose `hreflang` attribute is exactly "fr".

a\[hreflang=fr\] 

The following selector represents an [a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element) element for which the value of the `hreflang` attribute begins with "en", including "en", "en-US", and "en-scouse":

a\[hreflang|="en"\] 

The following selectors represent a DIALOGUE element whenever it has one of two different values for an attribute `character`:

DIALOGUE\[character=romeo\]
DIALOGUE\[character=juliet\]

### 6.2. Substring matching attribute selectors attribute-substrings)

Three additional attribute selectors are provided for matching substrings in the value of an attribute:

\[att^=val\]

Represents an element with the `att` attribute whose value begins with the prefix "val". If "val" is the empty string then the selector does not represent anything.

\[att$=val\]

Represents an element with the `att` attribute whose value ends with the suffix "val". If "val" is the empty string then the selector does not represent anything.

\[att\*=val\]

Represents an element with the `att` attribute whose value contains at least one instance of the substring "val". If "val" is the empty string then the selector does not represent anything.

Attribute values must be [<ident-token>](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token)s or [<string-token>](https://drafts.csswg.org/css-syntax-3/#typedef-string-token)s.

 example-d887e2c3)Examples: The following selector represents an HTML [object](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-object-element) element, referencing an image:

object\[type^="image/"\] 

The following selector represents an HTML [a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element) element with an `href` attribute whose value ends with ".html".

a\[href$=".html"\] 

The following selector represents an HTML paragraph with a `title` attribute whose value contains the substring "hello"

p\[title\*="hello"\] 

### 6.3. Case-sensitivity attribute-case)

By default case-sensitivity of attribute names and values in selectors depends on the document language.

To match attribute values [ASCII case-insensitively](https://infra.spec.whatwg.org/#ascii-case-insensitive) regardless of document language rules, the attribute selector may include the identifier `i` before the closing bracket (`]`). When this flag is present, UAs must match the attribute’s value ASCII case-insensitively (i.e. \[a-z\] and \[A-Z\] are considered equivalent).

Alternately, the attribute selector may include the identifier `s` before the closing bracket (`]`); in this case the UA must match the value case-sensitively regardless of document language rules.

Like the rest of Selectors syntax, the `i` and `s` identifiers themselves are [ASCII case-insensitive](https://infra.spec.whatwg.org/#ascii-case-insensitive).

 example-348bad1b)The following rule will style the `frame` attribute when it has a value of `hsides`, whether that value is represented as `hsides`, `HSIDES`, `hSides`, etc. even in an XML environment where attribute values are case-sensitive.

\[frame=hsides i\] { border-style: solid none; } 

 example-f596236d)The following rule will style lists with `type="a"` attributes differently than `type="A"` even though HTML defines the `type` attribute to be case-insensitive.

\[type="a" s\] { list-style: lower-alpha; }
\[type="A" s\] { list-style: upper-alpha; }

Note: Some document models normalize case-insensitive attribute values at parse time such that case-sensitive matching is impossible. Case-sensitive matching via `s` flags is only possible in systems that preserve the original case.

### 6.4. Attribute selectors and namespaces attrnmsp)

The attribute name in an attribute selector is given as a [CSS qualified name](https://www.w3.org/TR/css3-namespace/#css-qnames): a namespace prefix that has been previously [declared](https://drafts.csswg.org/selectors-4/#nsdecl) may be prepended to the attribute name separated by the namespace separator "vertical bar" (`|`). In keeping with the Namespaces in the XML recommendation, default namespaces do not apply to attributes, therefore attribute selectors without a namespace component apply only to attributes that have no namespace (equivalent to |attr). An asterisk may be used for the namespace prefix indicating that the selector is to match all attribute names without regard to the attribute’s namespace.

An attribute selector with an attribute name containing a namespace prefix that has not been previously [declared](https://drafts.csswg.org/selectors-4/#nsdecl) is an [invalid](https://drafts.csswg.org/selectors-4/#conformance) selector.

 example-a7ca2cb1)CSS examples:

@namespace foo "http://www.example.com";
\[foo|att=val\] { color: blue }
\[\*|att\] { color: yellow }
\[|att\] { color: green }
\[att\] { color: green }

The first rule will match only elements with the attribute `att` in the "http://www.example.com" namespace with the value "val".

The second rule will match only elements with the attribute `att` regardless of the namespace of the attribute (including no namespace).

The last two rules are equivalent and will match only elements with the attribute `att` where the attribute is not in a namespace.

### 6.5. Default attribute values in DTDs def-values)

Attribute selectors represent attribute values in the document tree. How that document tree is constructed is outside the scope of Selectors. In some document formats default attribute values can be defined in a DTD or elsewhere, but these can only be selected by attribute selectors if they appear in the document tree. Selectors should be designed so that they work whether or not the default values are included in the document tree.

For example, a XML UA may, but is _not_ required to, read an “external subset” of the DTD, but _is_ required to look for default attribute values in the document’s “internal subset”. (See, e.g., [\[XML10\]](https://drafts.csswg.org/selectors-4/#biblio-xml10) for definitions of these subsets.) Depending on the UA, a default attribute value defined in the external subset of the DTD might or might not appear in the document tree.

A UA that recognizes an XML namespace may, but is not required to use its knowledge of that namespace to treat default attribute values as if they were present in the document. (For example, an XHTML UA is not required to use its built-in knowledge of the XHTML DTD. See, e.g., [\[XML-NAMES\]](https://drafts.csswg.org/selectors-4/#biblio-xml-names) for details on namespaces in XML 1.0.)

Note: Typically, implementations choose to ignore external subsets. This corresponds to the behavior of non-validating processors as defined by the XML specification.

 example-2ffa5c63)Example:

Consider an element `EXAMPLE` with an attribute `radix` that has a default value of `"decimal"`. The DTD fragment might be

<!ATTLIST EXAMPLE radix (decimal,octal) "decimal"> 

If the style sheet contains the rules

EXAMPLE\[radix=decimal\] { /\*... default property settings ...\*/ }
EXAMPLE\[radix=octal\]   { /\*... other settings...\*/ }

the first rule might not match elements whose `radix` attribute is set by default, i.e. not set explicitly. To catch all cases, the attribute selector for the default value must be dropped:

EXAMPLE                { /\*... default property settings ...\*/ }
EXAMPLE\[radix=octal\]   { /\*... other settings...\*/ }

Here, because the selector ''EXAMPLE\[radix=octal\]'' is more specific than the type selector alone, the style declarations in the second rule will override those in the first for elements that have a `radix` attribute value of `"octal"`. Care has to be taken that all property declarations that are to apply only to the default case are overridden in the non-default cases' style rules.

### 6.6. Class selectors class-html)

**✔**MDN

[Class\_selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Class_selectors "The CSS class selector matches elements based on the contents of their class attribute.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE3+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The class selector is given as a full stop (. U+002E) immediately followed by an identifier. It represents an element belonging to the class identified by the identifier, as defined by the document language. For example, in [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5), [\[SVG11\]](https://drafts.csswg.org/selectors-4/#biblio-svg11), and [\[MATHML\]](https://drafts.csswg.org/selectors-4/#biblio-mathml) membership in a class is given by the `class` attribute: in these languages it is equivalent to the `~=` notation applied to the local `class` attribute (i.e. `[class~=identifier]`).

 example-f9c08b5b)CSS examples:

We can assign style information to all elements with `class~="pastoral"` as follows:

\*.pastoral { color: green }  /\* all elements with class~=pastoral \*/ 

or just

.pastoral { color: green }  /\* all elements with class~=pastoral \*/ 

The following assigns style only to H1 elements with `class~="pastoral"`:

H1.pastoral { color: green }  /\* H1 elements with class~=pastoral \*/ 

Given these rules, the first `H1` instance below would not have green text, while the second would:

<H1>Not green</H1>
<H1 class="pastoral">Very green</H1>

The following rule matches any [P](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element) element whose `class` attribute has been assigned a list of [whitespace](https://drafts.csswg.org/selectors-4/#whitespace)\-separated values that includes both `pastoral` and `marine`:

p.pastoral.marine { color: green } 

This rule matches when `class="pastoral blue aqua marine"` but does not match for `class="pastoral blue"`.

Note: Because CSS gives considerable power to the "class" attribute, authors could conceivably design their own "document language" based on elements with almost no associated presentation (such as [div](https://html.spec.whatwg.org/multipage/grouping-content.html#the-div-element) and [span](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-span-element) in HTML) and assigning style information through the "class" attribute. Authors should avoid this practice since the structural elements of a document language often have recognized and accepted meanings and author-defined classes may not.

Note: If an element has multiple class attributes, their values must be concatenated with spaces between the values before searching for the class. As of this time the working group is not aware of any manner in which this situation can be reached, however, so this behavior is explicitly non-normative in this specification.

When matching against a document which is in [quirks mode](https://dom.spec.whatwg.org/#concept-document-quirks), class names must be matched [ASCII case-insensitively](https://infra.spec.whatwg.org/#ascii-case-insensitive); class selectors are otherwise case-sensitive.

### 6.7. ID selectors id-selectors)

**✔**MDN

[ID\_selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/ID_selectors "The CSS ID selector matches an element based on the value of the element’s id attribute. In order for the element to be selected, its id attribute must match exactly the value given in the selector.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE3+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

Document languages may contain attributes that are declared to be of type ID. What makes attributes of type ID special is that no two such attributes can have the same value in a conformant document, regardless of the type of the elements that carry them; whatever the document language, an ID typed attribute can be used to uniquely identify its element. In HTML all ID attributes are named `id`; XML applications may name ID attributes differently, but the same restriction applies. Which attribute on an element is considered the “ID attribute“ is defined by the document language.

An ID selector consists of a “number sign” (U+0023, `#`) immediately followed by the ID value, which must be a CSS [identifier](https://www.w3.org/TR/CSS21/syndata.html#value-def-identifier). An ID selector represents an element instance that has an identifier that matches the identifier in the ID selector. (It is possible in non-conforming documents for multiple elements to match a single ID selector.)

 example-3e8dc597)Examples: The following ID selector represents an h1 element whose ID-typed attribute has the value "chapter1":

h1#chapter1 

The following ID selector represents any element whose ID-typed attribute has the value "chapter1":

#chapter1 

The following selector represents any element whose ID-typed attribute has the value "z98y".

\*#z98y 

Note: In XML 1.0 [\[XML10\]](https://drafts.csswg.org/selectors-4/#biblio-xml10), the information about which attribute contains an element’s IDs is contained in a DTD or a schema. When parsing XML, UAs do not always read the DTD, and thus may not know what the ID of an element is (though a UA may have namespace-specific knowledge that allows it to determine which attribute is the ID attribute for that namespace). If a style sheet author knows or suspects that a UA may not know what the ID of an element is, he should use normal attribute selectors instead: ''\[name=p371\] instead of #p371''.

If an element has multiple ID attributes, all of them must be treated as IDs for that element for the purposes of the ID selector. Such a situation could be reached using mixtures of xml:id, DOM3 Core, XML DTDs, and namespace-specific knowledge.

When matching against a document which is in [quirks mode](https://dom.spec.whatwg.org/#concept-document-quirks), IDs must be matched [ASCII case-insensitively](https://infra.spec.whatwg.org/#ascii-case-insensitive); ID selectors are otherwise case-sensitive.

## 7\. Linguistic Pseudo-classes linguistic-pseudos)

### 7.1. The Directionality Pseudo-class: [:dir()](https://drafts.csswg.org/selectors-4/#dir-pseudo) the-dir-pseudo)

**⚠**MDN

[:dir](https://developer.mozilla.org/en-US/docs/Web/CSS/:dir "The :dir() CSS pseudo-class matches elements based on the directionality of the text contained in them.")

In only one current engine.

Firefox49+SafariNoneChromeNone

-

OperaNoneEdgeNone

-

Edge (Legacy)NoneIENone

-

Firefox for Android49+iOS SafariNoneChrome for AndroidNoneAndroid WebViewNoneSamsung InternetNoneOpera MobileNone

The :dir() pseudo-class allows the author to write selectors that represent an element based on its directionality as determined by the [document language](https://drafts.csswg.org/selectors-4/#document-language). For example, [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5) defines [how to determine the directionality of an element](https://html.spec.whatwg.org/multipage/dom.html#the-directionality), based on a combination of the `dir` attribute, the surrounding text, and other factors. As another example, the `its:dir` and `dirRule` element of the Internationalization Tag Set [\[ITS20\]](https://drafts.csswg.org/selectors-4/#biblio-its20) are able to define the directionality of an element in [\[XML10\]](https://drafts.csswg.org/selectors-4/#biblio-xml10).

The [:dir()](https://drafts.csswg.org/selectors-4/#dir-pseudo) pseudo-class does not select based on stylistic states—for example, the CSS [direction](https://drafts.csswg.org/css-writing-modes-3/#propdef-direction) property does not affect whether it matches.

The pseudo-class :dir(ltr) represents an element that has a directionality of left-to-right (`ltr`). The pseudo-class :dir(rtl) represents an element that has a directionality of right-to-left (`rtl`). The argument to [:dir()](https://drafts.csswg.org/selectors-4/#dir-pseudo) must be a single identifier, otherwise the selector is invalid. White space is optionally allowed between the identifier and the parentheses. Values other than `ltr` and `rtl` are not invalid, but do not match anything. (If a future markup spec defines other directionalities, then Selectors may be extended to allow corresponding values.)

The difference between :dir(C) and ''\[dir=C\]'' is that ''\[dir=C\]'' only performs a comparison against a given attribute on the element, while the :dir(C) pseudo-class uses the UAs knowledge of the document’s semantics to perform the comparison. For example, in HTML, the directionality of an element inherits so that a child without a `dir` attribute will have the same directionality as its closest ancestor with a valid `dir` attribute. As another example, in HTML, an element that matches ''\[dir=auto\]'' will match either :dir(ltr) or :dir(rtl) depending on the resolved directionality of the elements as determined by its contents. [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5)

### 7.2. The Language Pseudo-class: [:lang()](https://drafts.csswg.org/selectors-4/#lang-pseudo) the-lang-pseudo)

**✔**MDN

[:lang](https://developer.mozilla.org/en-US/docs/Web/CSS/:lang "The :lang() CSS pseudo-class matches elements based on the language they are determined to be in.")

In all current engines.

Firefox1+Safari3.1+Chrome1+

-

Opera8+Edge79+

-

Edge (Legacy)12+IE8+

-

Firefox for Android4+iOS Safari3.1+Chrome for Android18+Android WebView1+Samsung Internet1.0+Opera Mobile10.1+

If the document language specifies how the (human) [content language](https://drafts.csswg.org/css-text-3/#content-language) of an element is determined, it is possible to write selectors that represent an element based on its content language. The :lang() pseudo-class represents an element that is in one of the languages listed in its argument. It accepts a comma-separated list of one or more [language ranges](https://drafts.csswg.org/selectors-4/#language-range) as its argument. Each language range in [:lang()](https://drafts.csswg.org/selectors-4/#lang-pseudo) must be a valid CSS [<ident>](https://drafts.csswg.org/css-values-4/#typedef-ident) or [<string>](https://drafts.csswg.org/css-values-3/#string-value). (Language ranges containing asterisks, for example, must be either correctly escaped or quoted as strings, e.g. :lang(\\\*-Latn) or :lang("\*-Latn"))

Note: The [content language](https://drafts.csswg.org/css-text-3/#content-language) of an element is defined by the document language. For example, in HTML [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5), the content language is determined by a combination of the `lang` attribute, information from [meta](https://html.spec.whatwg.org/multipage/semantics.html#meta) elements, and possibly also the protocol (e.g. from HTTP headers). XML languages can use the `xml:lang` attribute to indicate language information for an element. [\[XML10\]](https://drafts.csswg.org/selectors-4/#biblio-xml10)

The element’s [content language](https://drafts.csswg.org/css-text-3/#content-language) matches a [language range](https://drafts.csswg.org/selectors-4/#language-range) if its content language, as represented in BCP 47 syntax, matches the given language range in an extended filtering operation per [\[RFC4647\]](https://drafts.csswg.org/selectors-4/#biblio-rfc4647) Matching of Language Tags (section 3.3.2). The matching is performed [ASCII case-insensitively](https://infra.spec.whatwg.org/#ascii-case-insensitive). The language range does not need to be a valid language code to perform this comparison.

Note: It is recommended that documents and protocols indicate language using codes from BCP 47 [\[BCP47\]](https://drafts.csswg.org/selectors-4/#biblio-bcp47) or its successor, and by means of `xml:lang` attributes in the case of XML-based documents [\[XML10\]](https://drafts.csswg.org/selectors-4/#biblio-xml10). See ["FAQ: Two-letter or three-letter language codes."](http://www.w3.org/International/questions/qa-lang-2or3.html)

 example-91142d84)Examples: The two following selectors represent an HTML document that is in Belgian French or German. The two next selectors represent [q](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-q-element) quotations in an arbitrary element in Belgian French or German.

html:lang(fr-be)
html:lang(de)
:lang(fr-be) > q
:lang(de) > q

Note: One difference between :lang(C) and the ''|='' operator is that the ''|='' operator only performs a comparison against a given attribute on the element, while the :lang(C) pseudo-class uses the UAs knowledge of the document’s semantics to perform the comparison.

 example-c45712e2)In this HTML example, only the BODY matches ''\[lang|=fr\]'' (because it has a LANG attribute) but both the BODY and the P match :lang(fr) (because both are in French). The P does not match the ''\[lang|=fr\]'' because it does not have a LANG attribute.

<body lang=fr>
  <p>Je suis français.</p>
</body>

 example-c3df9362)Another difference between :lang(C) and the ''|='' operator is that :lang(C) performs implicit wildcard matching.

For example, :lang(de-DE) will match all of de-DE, de-DE-1996, de-Latn-DE, de-Latf-DE, de-Latn-DE-1996, whereas of those ''\[lang|=de-DE\] will only match de-DE'' and de-DE-1996.

To perform wildcard matching on the first subtag (the primary language), an asterisk must be used: \*-CH will match all of de-CH, it-CH, fr-CH, and rm-CH.

To select against an element’s lang attribute value using this type of language range match, use both the attribute selector and language pseudo-class together, e.g. \[lang\]:lang(de-DE).

Note: Wildcard language matching and comma-separated lists are new in Level 4.

## 8\. Location Pseudo-classes location)

### 8.1. The Hyperlink Pseudo-class: [:any-link](https://drafts.csswg.org/selectors-4/#any-link-pseudo) the-any-link-pseudo)

**✔**MDN

[:any-link](https://developer.mozilla.org/en-US/docs/Web/CSS/:any-link "The :any-link CSS pseudo-class selector represents an element that acts as the source anchor of a hyperlink, independent of whether it has been visited. In other words, it matches every <a>, <area>, or <link> element that has an href attribute. Thus, it matches all elements that match :link or :visited.")

In all current engines.

Firefox50+Safari9+Chrome65+

-

Opera52+Edge79+

-

Edge (Legacy)NoneIENone

-

Firefox for Android50+iOS Safari9+Chrome for Android65+Android WebView65+Samsung Internet9.0+Opera Mobile47+

The :any-link pseudo-class represents an element that acts as the source anchor of a hyperlink. For example, in [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5), any [a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element), [area](https://html.spec.whatwg.org/multipage/image-maps.html#the-area-element), or [link](https://html.spec.whatwg.org/multipage/semantics.html#the-link-element) elements with an `href` attribute are hyperlinks, and thus match `:any-link`. It matches an element if the element would match either [:link](https://drafts.csswg.org/selectors-4/#link-pseudo) or [:visited](https://drafts.csswg.org/selectors-4/#visited-pseudo), and is equivalent to :is(:link, :visited).

### 8.2. The Link History Pseudo-classes: [:link](https://drafts.csswg.org/selectors-4/#link-pseudo) and [:visited](https://drafts.csswg.org/selectors-4/#visited-pseudo) link)

**✔**MDN

[:link](https://developer.mozilla.org/en-US/docs/Web/CSS/:link "The :link CSS pseudo-class represents an element that has not yet been visited. It matches every unvisited <a>, <area>, or <link> element that has an href attribute.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE3+

-

Firefox for Android4+iOS Safari3.2+Chrome for Android18+Android WebView1.5+Samsung Internet1.0+Opera Mobile14+

[:visited](https://developer.mozilla.org/en-US/docs/Web/CSS/:visited "The :visited CSS pseudo-class represents links that the user has already visited. For privacy reasons, the styles that can be modified using this selector are very limited.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE4+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView4.4+Samsung Internet1.0+Opera Mobile10.1+

User agents commonly display unvisited [hyperlinks](https://drafts.csswg.org/selectors-4/#the-any-link-pseudo) differently from previously visited ones. Selectors provides the pseudo-classes :link and :visited to distinguish them:

- The [:link](https://drafts.csswg.org/selectors-4/#link-pseudo) pseudo-class applies to links that have not yet been visited.
- The [:visited](https://drafts.csswg.org/selectors-4/#visited-pseudo) pseudo-class applies once the link has been visited by the user.

After some amount of time, user agents may choose to return a visited link to the (unvisited) [:link](https://drafts.csswg.org/selectors-4/#link-pseudo) state.

The two states are mutually exclusive.

 example-0fcef6cd)The following selector represents links carrying class `footnote` and already visited:

.footnote:visited 

Since it is possible for style sheet authors to abuse the :link and :visited pseudo-classes to determine which sites a user has visited without the user’s consent, UAs may treat all links as unvisited links or implement other measures to preserve the user’s privacy while rendering visited and unvisited links differently.

### 8.3. The Local Link Pseudo-class: [:local-link](https://drafts.csswg.org/selectors-4/#local-link-pseudo) the-local-link-pseudo)

The :local-link pseudo-class allows authors to style [hyperlinks](https://drafts.csswg.org/selectors-4/#the-any-link-pseudo) based on the users current location within a site. It represents an element that is the source anchor of a hyperlink whose target’s absolute URL matches the element’s own document URL. If the hyperlink’s target includes a fragment URL, then the fragment URL of the current URL must also match; if it does not, then the fragment URL portion of the current URL is not taken into account in the comparison.

 example-f0a37344)For example, the following rule prevents links targetting the current page from being underlined when they are part of the navigation list:

nav :local-link { text-decoration: none; } 

Note: The current URL of a page can change as a result of user actions such as activating a link targetting a different fragment within the same page; or by use of the `pushState` API; as well as by the more obvious actions of navigating to a different page or following a redirect (which could be initiated by protocols such as HTTP, markup instructions such as `<meta http-equiv="...">`, or scripting instructions ). UAs must ensure that [:local-link](https://drafts.csswg.org/selectors-4/#local-link-pseudo), as well as the [:target](https://drafts.csswg.org/selectors-4/#target-pseudo) and [:target-within](https://drafts.csswg.org/selectors-4/#target-within-pseudo) pseudo-classes below, respond correctly to all such changes in state.

### 8.4. The Target Pseudo-class: [:target](https://drafts.csswg.org/selectors-4/#target-pseudo) the-target-pseudo)

**✔**MDN

[:target](https://developer.mozilla.org/en-US/docs/Web/CSS/:target "The :target CSS pseudo-class represents a unique element (the target element) with an id matching the URL's fragment.")

In all current engines.

Firefox1+Safari1.3+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari2+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

In some document languages, the document’s URL can further point to specific elements _within_ the document via the URL’s [fragment](https://url.spec.whatwg.org/#concept-url-fragment). The elements pointed to in this way are the target elements of the document.

 example-b8c5336f)In HTML the fragment points to the element in the page with the same ID. The url `https://example.com/index.html#section2`, for example, points to the element with `id="section2"` in the document at `https://example.com/index.html`.

The :target pseudo-class matches the document’s target elements. If the document’s URL has no fragment identifier, then the document has no target elements.

 example-8a386e7c)Example:

p.note:target 

This selector represents a `[p](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element)` element of class `note` that is the target element of the referring URL.

 example-af403697)CSS example: Here, the [:target](https://drafts.csswg.org/selectors-4/#target-pseudo) pseudo-class is used to make the target element red and place an image before it, if there is one:

:target { color : red }
:target::before { content : url(target.png) }

### 8.5. The Target Container Pseudo-class: [:target-within](https://drafts.csswg.org/selectors-4/#target-within-pseudo) the-target-within-pseudo)

The :target-within pseudo-class applies to elements for which the [:target](https://drafts.csswg.org/selectors-4/#target-pseudo) pseudo class applies as well as to an element whose descendant in the [flat tree](https://drafts.csswg.org/css-scoping-1/#flat-tree) (including non-element nodes, such as text nodes) matches the conditions for matching [:target-within](https://drafts.csswg.org/selectors-4/#target-within-pseudo).

### 8.6. The Reference Element Pseudo-class: [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo) the-scope-pseudo)

**✔**MDN

[:scope](https://developer.mozilla.org/en-US/docs/Web/CSS/:scope "The :scope CSS pseudo-class represents elements that are a reference point for selectors to match against.")

In all current engines.

Firefox32+Safari7+Chrome27+

-

Opera15+Edge79+

-

Edge (Legacy)NoneIENone

-

Firefox for Android32+iOS Safari7+Chrome for Android27+Android WebView37+Samsung Internet1.5+Opera Mobile15+

In some contexts, selectors can be matched with an explicit set of :scope elements. This is is a (potentially empty) set of elements that provide a reference point for selectors to match against, such as that specified by the `querySelector()` call in [\[DOM\]](https://drafts.csswg.org/selectors-4/#biblio-dom).

The :scope pseudo-class represents any element that is a [:scope element](https://drafts.csswg.org/selectors-4/#scope-element). If the :scope elements are not explicitly specified, but the selector is [scoped](https://drafts.csswg.org/selectors-4/#scoped-selector) and the [scoping root](https://drafts.csswg.org/selectors-4/#scoping-root) is an element, then [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo) represents the scoping root; otherwise, it represents the root of the document (equivalent to [:root](https://drafts.csswg.org/selectors-4/#root-pseudo)). Specifications intending for this pseudo-class to match specific elements rather than the document’s root element must define either a scoping root (if using scoped selectors) or an explicit set of :scope elements.

## 9\. User Action Pseudo-classes useraction-pseudos)

Interactive user interfaces sometimes change the rendering in response to user actions. Selectors provides several user action pseudo-classes for the selection of an element the user is acting on. (In non-interactive user agents, these pseudo-classes are valid, but never match any element.)

These pseudo-classes are not mutually exclusive. An element can match several such pseudo-classes at the same time.

 example-eaf585d5)Examples:

a:link    /\* unvisited links \*/
a:visited /\* visited links \*/
a:hover   /\* user hovers \*/
a:active  /\* active links \*/

An example of combining dynamic pseudo-classes:

a:focus
a:focus:hover

The last selector matches [a](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element) elements that are in the pseudo-class :focus and in the pseudo-class :hover.

Note: The specifics of hit-testing, necessary to know when several of the pseudo-classes defined in this section apply, are not yet defined, but will be in the future.

### 9.1. The Pointer Hover Pseudo-class: [:hover](https://drafts.csswg.org/selectors-4/#hover-pseudo) the-hover-pseudo)

**✔**MDN

[:hover](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover "The :hover CSS pseudo-class matches when the user interacts with an element with a pointing device, but does not necessarily activate it. It is generally triggered when the user hovers over an element with the cursor (mouse pointer).")

In all current engines.

Firefox1+Safari2+Chrome1+

-

Opera4+Edge79+

-

Edge (Legacy)12+IE4+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The :hover pseudo-class applies while the user designates an element with a pointing device, but does not necessarily activate it. For example, a visual user agent could apply this pseudo-class when the cursor (mouse pointer) hovers over a box generated by the element. Interactive user agents that cannot detect hovering due to hardware limitations (e.g., a pen device that does not detect hovering) are still conforming; the selector will simply never match in such a UA.

An element also matches [:hover](https://drafts.csswg.org/selectors-4/#hover-pseudo) if one of its descendants in the [flat tree](https://drafts.csswg.org/css-scoping-1/#flat-tree) (including non-element nodes, such as text nodes) matches the above conditions.

Document languages may define additional ways in which an element can match [:hover](https://drafts.csswg.org/selectors-4/#hover-pseudo). For example, [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5) defines a labeled control element as [matching `:hover`](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-hover) when its [label](https://html.spec.whatwg.org/multipage/forms.html#the-label-element) is hovered.

Note: Since the [:hover](https://drafts.csswg.org/selectors-4/#hover-pseudo) state can apply to an element because its child is designated by a pointing device, it is possible for :hover to apply to an element that is not underneath the pointing device.

The [:hover](https://drafts.csswg.org/selectors-4/#hover-pseudo) pseudo-class can apply to any pseudo-element.

### 9.2. The Activation Pseudo-class: [:active](https://drafts.csswg.org/selectors-4/#active-pseudo) the-active-pseudo)

**✔**MDN

[:active](https://developer.mozilla.org/en-US/docs/Web/CSS/:active "The :active CSS pseudo-class represents an element (such as a button) that is being activated by the user.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera5+Edge79+

-

Edge (Legacy)12+IE4+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView1+Samsung Internet1.0+Opera Mobile10.1+

The :active pseudo-class applies while an element is being activated by the user. For example, between the times the user presses the mouse button and releases it. On systems with more than one mouse button, [:active](https://drafts.csswg.org/selectors-4/#active-pseudo) applies only to the primary or primary activation button (typically the "left" mouse button), and any aliases thereof.

There may be document-language or implementation-specific limits on which elements can become [:active](https://drafts.csswg.org/selectors-4/#active-pseudo). For example, [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5) defines a [list of activatable elements](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-active).

An element also matches [:active](https://drafts.csswg.org/selectors-4/#active-pseudo) if one of its descendants in the [flat tree](https://drafts.csswg.org/css-scoping-1/#flat-tree) (including non-element nodes, such as text nodes) matches the above conditions.

Document languages may define additional ways in which an element can match [:active](https://drafts.csswg.org/selectors-4/#active-pseudo).

Note: An element can be both [:visited](https://drafts.csswg.org/selectors-4/#visited-pseudo) and [:active](https://drafts.csswg.org/selectors-4/#active-pseudo) (or [:link](https://drafts.csswg.org/selectors-4/#link-pseudo) and :active).

### 9.3. The Input Focus Pseudo-class: [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo) the-focus-pseudo)

**✔**MDN

[:focus](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus "The :focus CSS pseudo-class represents an element (such as a form input) that has received focus. It is generally triggered when the user clicks or taps on an element or selects it with the keyboard's Tab key.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera7+Edge79+

-

Edge (Legacy)12+IE8+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView1+Samsung Internet1.0+Opera Mobile10.1+

The :focus pseudo-class applies while an element has the focus (accepts keyboard or mouse events, or other forms of input).

There may be document language or implementation specific limits on which elements can acquire [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo). For example, [\[HTML\]](https://drafts.csswg.org/selectors-4/#biblio-html) defines a list of [focusable areas](https://html.spec.whatwg.org/multipage/interaction.html#focusable-area).

Document languages may define additional ways in which an element can match [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo), except that the :focus pseudo class must not automatically propagate to the parent element—see [:focus-within](https://drafts.csswg.org/selectors-4/#focus-within-pseudo) if matching on the parent is desired. (It may still apply to the parent element if made to propagate due to other mechanisms, but not merely due to being the parent.)

 issue-1416193e)There’s a desire from authors to propagate [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo) from a form control to its associated `[label](https://html.spec.whatwg.org/multipage/forms.html#the-label-element)` element; the main objection seems to be implementation difficulty. See [CSSWG issue (CSS)](https://github.com/w3c/csswg-drafts/issues/397) and [WHATWG issue (HTML)](https://github.com/whatwg/html/issues/1632).

### 9.4. The Focus-Indicated Pseudo-class: [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo) the-focus-visible-pseudo)

**⚠**MDN

[:focus-visible](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible "The :focus-visible pseudo-class applies while an element matches the :focus pseudo-class and the UA (User Agent) determines via heuristics that the focus should be made evident on the element. (Many browsers show a “focus ring” by default in this case.)")

In only one current engine.

FirefoxNoneSafariNoneChrome🔰 67+

-

Opera🔰 54+Edge🔰 79+

-

Edge (Legacy)NoneIENone

-

Firefox for AndroidNoneiOS SafariNoneChrome for Android🔰 67+Android WebViewNoneSamsung InternetNoneOpera Mobile🔰 48+

The :focus-visible pseudo-class applies while an element matches the [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo) pseudo-class _and_ the user agent determines via heuristics that the focus should be made evident on the element.

Note: The intent of [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo) is to allow authors to provide _clearly identifiable_ focus styles which are visible when a user is likely to need to understand where focus is, and not visible in other cases.

 example-c40d8011)In this example, all focusable elements get a strong yellow outline on [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo), and links get both a yellow outline and a yellow background on :focus-visible. These styles are consistent throughout the page and are easily visible due to their bold styling, but do not appear unless the user is likely to need to understand where page focus is.

:root {
  \--focus-gold: #ffbf47;
}

:focus-visible  {
  outline: 3px solid var(\--focus-gold);
}

a:focus-visible {
  background-color: var(\--focus-gold);
}

User agents can choose their own heuristics for when to match [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo); however, the following (non-normative) suggestions can be used as a starting point:

- If a user has expressed a preference (such as via a system preference or a browser setting) to always see a visible focus indicator, the user agent should honor this by having [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo) always match on the active element, regardless of any other factors. (Another option may be for the user agent to show its own focus indicator regardless of author styles.)
    
- Any element which supports keyboard input (such as an `[input](https://html.spec.whatwg.org/multipage/input.html#the-input-element)` element, or any other element which may trigger a virtual keyboard to be shown on focus if a physical keyboard is not present) should **always** match [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo) when focused.
    
- If the user interacts with the page via the keyboard, the currently focused element should match [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo) (i.e. keyboard usage may change whether this pseudo-class matches even if it doesn’t affect [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo)).
    
- If the user interacts with the page via a pointing device, such that the focus is moved to a new element which does _not_ support user input, the newly focused element should **not** match [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo).
    
- If the active element matches [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo), and a script causes focus to move elsewhere, the newly focused element should match :focus-visible.
    
- Conversely, if the active element does not match [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo), and a script causes focus to move elsewhere, the newly focused element should **not** match :focus-visible.
    

User agents should also use [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo) to specify the default focus style, so that authors using :focus-visible will not also need to disable the default [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo) style.

 example-cd595a08)In this example, authors use a [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo) pseudo-class to remove default user agent focus styling if [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo) is supported, and provide enhanced focus styling via :focus-visible.

:focus:not(:focus-visible) {
  outline: 0;
}

:focus-visible {
  outline: 3px solid var(\--focus-gold);
}

### 9.5. The Focus Container Pseudo-class: [:focus-within](https://drafts.csswg.org/selectors-4/#focus-within-pseudo) the-focus-within-pseudo)

**✔**MDN

[:focus-within](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-within "The :focus-within CSS pseudo-class represents an element that has received focus or contains an element that has received focus. In other words, it represents an element that is itself matched by the :focus pseudo-class or has a descendant that is matched by :focus. (This includes descendants in shadow trees.)")

In all current engines.

Firefox52+Safari10.1+Chrome60+

-

Opera47+Edge79+

-

Edge (Legacy)NoneIENone

-

Firefox for Android52+iOS Safari10.3+Chrome for Android60+Android WebView60+Samsung Internet8.0+Opera Mobile44+

The :focus-within pseudo-class applies to any element for which the [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo) pseudo class applies as well as to an element whose descendant in the [flat tree](https://drafts.csswg.org/css-scoping-1/#flat-tree) (including non-element nodes, such as text nodes) matches the conditions for matching :focus.

## 10\. Time-dimensional Pseudo-classes time-pseudos)

These pseudo-classes classify elements with respect to the currently-displayed or active position in some timeline, such as during speech rendering of a document, or during the display of a video using WebVTT to render subtitles.

CSS does not define this timeline; the host language must do so. If there is no timeline defined for an element, these pseudo-classes must not match the element.

Note: Ancestors of a [:current](https://drafts.csswg.org/selectors-4/#current-pseudo) element are also :current, but ancestors of a [:past](https://drafts.csswg.org/selectors-4/#past-pseudo) or [:future](https://drafts.csswg.org/selectors-4/#future-pseudo) element are not necessarily :past or :future as well. A given element matches at most one of :current, :past, or :future.

### 10.1. The Current-element Pseudo-class: [:current](https://drafts.csswg.org/selectors-4/#current-pseudo) the-current-pseudo)

The :current pseudo-class represents the element, or an ancestor of the element, that is currently being displayed.

Its alternate form :current() selectordef-current), like [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo), takes a list of [compound selectors](https://drafts.csswg.org/selectors-4/#compound) as its argument: it represents the [:current](https://drafts.csswg.org/selectors-4/#current-pseudo) element that matches the argument or, if that does not match, the innermost ancestor of the :current element that does. (If neither the :current element nor its ancestors match the argument, then the selector does not represent anything.)

 example-34db2617)For example, the following rule will highlight whichever paragraph or list item is being read aloud in a speech rendering of the document:

:current(p, li, dt, dd) {
  background: yellow;
}

### 10.2. The Past-element Pseudo-class: [:past](https://drafts.csswg.org/selectors-4/#past-pseudo) the-past-pseudo)

The :past pseudo-class represents any element that is defined to occur entirely prior to a [:current](https://drafts.csswg.org/selectors-4/#current-pseudo) element. For example, the WebVTT spec defines the [:past](https://drafts.csswg.org/selectors-4/#past-pseudo) pseudo-class [relative to the current playback position of a media element](http://dev.w3.org/html5/webvtt/#the-past-and-future-pseudo-classes). If a time-based order of elements is not defined by the document language, then this represents any element that is a (possibly indirect) previous sibling of a :current element.

### 10.3. The Future-element Pseudo-class: [:future](https://drafts.csswg.org/selectors-4/#future-pseudo) the-future-pseudo)

The :future pseudo-class represents any element that is defined to occur entirely after a [:current](https://drafts.csswg.org/selectors-4/#current-pseudo) element. For example, the WebVTT spec defines the [:future](https://drafts.csswg.org/selectors-4/#future-pseudo) pseudo-class [relative to the current playback position of a media element](http://dev.w3.org/html5/webvtt/#the-past-and-future-pseudo-classes). If a time-based order of elements is not defined by the document language, then this represents any element that is a (possibly indirect) next sibling of a :current element.

## 11\. Resource State Pseudos resource-pseudos)

The pseudo-classes in this section apply to elements that represent loaded resources, particularly images/videos, and allow authors to select them based on some quality of their state.

### 11.1. Video/Audio Play State: the [:playing](https://drafts.csswg.org/selectors-4/#selectordef-playing) and [:paused](https://drafts.csswg.org/selectors-4/#selectordef-paused) pseudo-classes video-state)

The :playing pseudo-class represents an element representing an audio, video, or similar resource that is capable of being “played” or “paused”, when that element is “playing”. (This includes both when the element is explicitly playing, and when it’s temporarily stopped for some reason not connected to user intent, but will automatically resume when that reason is resolved, such as a “buffering” state.)

The :paused pseudo-class represents the same elements, but instead match when the element is _not_ “playing”. (This includes both an explicit “paused” state, and other non-playing states like “loaded, hasn’t been activated yet”, etc.)

## 12\. The Input Pseudo-classes input-pseudos)

The pseudo-classes in this section mostly apply to elements that take user input, such as HTML’s [input](https://html.spec.whatwg.org/multipage/input.html#the-input-element) element.

### 12.1. Input Control States input-states)

#### 12.1.1. The [:enabled](https://drafts.csswg.org/selectors-4/#enabled-pseudo) and [:disabled](https://drafts.csswg.org/selectors-4/#disabled-pseudo) Pseudo-classes enableddisabled)

**✔**MDN

[:disabled](https://developer.mozilla.org/en-US/docs/Web/CSS/:disabled "The :disabled CSS pseudo-class represents any disabled element. An element is disabled if it can't be activated (selected, clicked on, typed into, etc.) or accept focus. The element also has an enabled state, in which it can be activated or accept focus.")

In all current engines.

Firefox1+Safari3.1+Chrome1+

-

Opera9+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.1+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

[:enabled](https://developer.mozilla.org/en-US/docs/Web/CSS/:enabled "The :enabled CSS pseudo-class represents any enabled element. An element is enabled if it can be activated (selected, clicked on, typed into, etc.) or accept focus. The element also has a disabled state, in which it can't be activated or accept focus.")

In all current engines.

Firefox1+Safari3.1+Chrome1+

-

Opera9+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.1+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

The :enabled pseudo-class represents user interface elements that are in an enabled state; such elements must have a corresponding disabled state.

Conversely, the :disabled pseudo-class represents user interface elements that are in a disabled state; such elements must have a corresponding enabled state.

What constitutes an enabled state, a disabled state, and a user interface element is host-language-dependent. In a typical document most elements will be neither [:enabled](https://drafts.csswg.org/selectors-4/#enabled-pseudo) nor [:disabled](https://drafts.csswg.org/selectors-4/#disabled-pseudo). For example, [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5) defines [non-disabled interactive elements](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-enabled) to be :enabled, and any such elements that are [explicitly disabled](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-enabled) to be :disabled.

Note: CSS properties that might affect a user’s ability to interact with a given user interface element do not affect whether it matches [:enabled](https://drafts.csswg.org/selectors-4/#enabled-pseudo) or [:disabled](https://drafts.csswg.org/selectors-4/#disabled-pseudo); e.g., the [display](https://drafts.csswg.org/css-display-3/#propdef-display) and [visibility](https://drafts.csswg.org/css2/#propdef-visibility) properties have no effect on the enabled/disabled state of an element.

#### 12.1.2. The Mutability Pseudo-classes: [:read-only](https://drafts.csswg.org/selectors-4/#read-only-pseudo) and [:read-write](https://drafts.csswg.org/selectors-4/#read-write-pseudo) rw-pseudos)

**✔**MDN

[:read-only](https://developer.mozilla.org/en-US/docs/Web/CSS/:read-only "The :read-only CSS pseudo-class represents an element (such as input or textarea) that is not editable by the user.")

In all current engines.

Firefox78+Safari4+Chrome1+

-

Opera9+Edge79+

-

Edge (Legacy)13+IENone

-

Firefox for AndroidNoneiOS Safari3.2+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

[:read-write](https://developer.mozilla.org/en-US/docs/Web/CSS/:read-write "The :read-write CSS pseudo-class represents an element (such as input or textarea) that is editable by the user.")

In all current engines.

Firefox78+Safari4+Chrome1+

-

Opera9+Edge79+

-

Edge (Legacy)13+IENone

-

Firefox for AndroidNoneiOS Safari3.2+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

An element matches :read-write if it is user-alterable, as defined by the document language. Otherwise, it is :read-only.

For example, in [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5) a [non-disabled non-readonly `<input>` element](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-read-only) is [:read-write](https://drafts.csswg.org/selectors-4/#read-write-pseudo), as is any element with the `contenteditable` attribute set to the true state.

#### 12.1.3. The Placeholder-shown Pseudo-class: [:placeholder-shown](https://drafts.csswg.org/selectors-4/#placeholder-shown-pseudo) placeholder)

**✔**MDN

[:placeholder-shown](https://developer.mozilla.org/en-US/docs/Web/CSS/:placeholder-shown "The :placeholder-shown CSS pseudo-class represents any <input> or <textarea> element that is currently displaying placeholder text.")

In all current engines.

Firefox51+Safari9+Chrome47+

-

Opera34+Edge79+

-

Edge (Legacy)NoneIENone

-

Firefox for Android51+iOS Safari9+Chrome for Android47+Android WebView47+Samsung Internet5.0+Opera Mobile34+

Input elements can sometimes show placeholder text as a hint to the user on what to type in. See, for example, the `placeholder` attribute in [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5). The :placeholder-shown pseudo-class matches an input element that is showing such placeholder text, whether that text is given by an attribute or a real element, or is otherwise implied by the UA.

 example-8b59d4ec)For example, according to the semantics of [\[HTML\]](https://drafts.csswg.org/selectors-4/#biblio-html) the `[placeholder](https://html.spec.whatwg.org/multipage/input.html#attr-input-placeholder)` attribute on the `[input](https://html.spec.whatwg.org/multipage/input.html#the-input-element)` element provide placeholder text, as does the first `[option](https://html.spec.whatwg.org/multipage/form-elements.html#the-option-element)` element of a `[select](https://html.spec.whatwg.org/multipage/form-elements.html#the-select-element)` under certain conditions. The [:placeholder-shown](https://drafts.csswg.org/selectors-4/#placeholder-shown-pseudo) class thus applies whenever such placeholder text is shown.

#### 12.1.4. The Default-option Pseudo-class: [:default](https://drafts.csswg.org/selectors-4/#default-pseudo) the-default-pseudo)

**✔**MDN

[:default](https://developer.mozilla.org/en-US/docs/Web/CSS/:default "The :default CSS pseudo-class selects form elements that are the default in a group of related elements.")

In all current engines.

Firefox4+Safari5+Chrome10+

-

Opera10+Edge79+

-

Edge (Legacy)NoneIENone

-

Firefox for Android4+iOS Safari5+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The :default pseudo-class applies to the one or more UI elements that are the default among a set of similar elements. Typically applies to context menu items, buttons and select lists/menus.

One example is the default submit button among a set of buttons. Another example is the default option from a popup menu. In a select-many group (such as for pizza toppings), multiple elements can match [:default](https://drafts.csswg.org/selectors-4/#default-pseudo). For example, [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5) defines that :default matches [the “default button” in a form, the initially-selected `<option>`(s) in a `<select>`, and a few other elements.](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-default)

### 12.2. Input Value States input-value-states)

#### 12.2.1. The Selected-option Pseudo-class: [:checked](https://drafts.csswg.org/selectors-4/#checked-pseudo) checked)

**✔**MDN

[:checked](https://developer.mozilla.org/en-US/docs/Web/CSS/:checked "The :checked CSS pseudo-class selector represents any radio (<input type="radio">), checkbox (<input type="checkbox">), or option (<option> in a <select>) element that is checked or toggled to an on state.")

In all current engines.

Firefox1+Safari3.1+Chrome1+

-

Opera9+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.1+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

Radio and checkbox elements can be toggled by the user. Some menu items are “checked” when the user selects them. When such elements are toggled “on” the :checked pseudo-class applies. For example, [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5) defines that [checked checkboxes, radio buttons, and selected `<option>` elements](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-checked) match [:checked](https://drafts.csswg.org/selectors-4/#checked-pseudo).

While the [:checked](https://drafts.csswg.org/selectors-4/#checked-pseudo) pseudo-class is dynamic in nature, and can altered by user action, since it can also be based on the presence of semantic attributes in the document (such as the `selected` and `checked` attributes in [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5)), it applies to all media.

 example-a6c4964c)An unchecked checkbox can be selected by using the negation pseudo-class:

input\[type=checkbox\]:not(:checked)

#### 12.2.2. The Indeterminate-value Pseudo-class: [:indeterminate](https://drafts.csswg.org/selectors-4/#indetermine-pseudo) indeterminate)

**✔**MDN

[:indeterminate](https://developer.mozilla.org/en-US/docs/Web/CSS/:indeterminate "The :indeterminate CSS pseudo-class represents any form element whose state is indeterminate, such as checkboxes which have their HTML indeterminate attribute set to true, radio buttons which are members of a group in which all radio buttons are unchecked, and indeterminate <progress> elements.")

In all current engines.

Firefox2+Safari3+Chrome1+

-

Opera9+Edge79+

-

Edge (Legacy)12+IE10+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The :indeterminate pseudo-class applies to UI elements whose value is in an indeterminate state. For example, radio and checkbox elements can be toggled between checked and unchecked states, but are sometimes in an indeterminate state, neither checked nor unchecked. Similarly a progress meter can be in an indeterminate state when the percent completion is unknown. For example, [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5) defines how [checkboxes](https://html.spec.whatwg.org/multipage/semantics-other.html#selector-indeterminate) can be made to match [:indeterminate](https://drafts.csswg.org/selectors-4/#indetermine-pseudo).

Like the [:checked](https://drafts.csswg.org/selectors-4/#checked-pseudo) pseudo-class, [:indeterminate](https://drafts.csswg.org/selectors-4/#indetermine-pseudo) applies to all media. Components of a radio-group initialized with no pre-selected choice, for example, would be :indeterminate even in a static display.

### 12.3. Input Value-checking ui-validity)

#### 12.3.1. The Empty-Value Pseudo-class: [:blank](https://drafts.csswg.org/selectors-4/#blank-pseudo) blank)

**⚠**MDN

[:blank](https://developer.mozilla.org/en-US/docs/Web/CSS/:blank "The :blank CSS pseudo-class selects empty user input elements (eg. <input> or <textarea>).")

In no current engines.

FirefoxNoneSafariNoneChromeNone

-

OperaNoneEdgeNone

-

Edge (Legacy)NoneIENone

-

Firefox for AndroidNoneiOS SafariNoneChrome for AndroidNoneAndroid WebViewNoneSamsung InternetNoneOpera MobileNone

The :blank pseudo-class applies to user-input elements whose input value is empty (consists of the empty string or otherwise null input).

 example-e34400f8)Examples of [:blank](https://drafts.csswg.org/selectors-4/#blank-pseudo) user-input elements would be a `[textarea](https://html.spec.whatwg.org/multipage/form-elements.html#the-textarea-element)` element whose contents are empty, or an `[input](https://html.spec.whatwg.org/multipage/input.html#the-input-element)` field whose value is empty. Note that the value under consideration here is the value that would be submitted (see [A form control’s value](https://html.spec.whatwg.org/multipage/form-control-infrastructure.html#a-form-control%E2%80%99s-value) in [\[HTML\]](https://drafts.csswg.org/selectors-4/#biblio-html)), which in HTML does not necessarily correspond to the value of the element’s `[value](https://html.spec.whatwg.org/multipage/input.html#attr-input-value)` attribute.

Note: This selector is at-risk.

#### 12.3.2. The Validity Pseudo-classes: [:valid](https://drafts.csswg.org/selectors-4/#valid-pseudo) and [:invalid](https://drafts.csswg.org/selectors-4/#invalid-pseudo) validity-pseudos)

**✔**MDN

[:invalid](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid "The :invalid CSS pseudo-class represents any <input> or other <form> element whose contents fail to validate.")

In all current engines.

Firefox4+Safari5+Chrome10+

-

Opera10+Edge79+

-

Edge (Legacy)12+IE10+

-

Firefox for Android4+iOS Safari5+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

[:valid](https://developer.mozilla.org/en-US/docs/Web/CSS/:valid "The :valid CSS pseudo-class represents any <input> or other <form> element whose contents validate successfully. This allows to easily make valid fields adopt an appearance that helps the user confirm that their data is formatted properly.")

In all current engines.

Firefox4+Safari5+Chrome10+

-

Opera10+Edge79+

-

Edge (Legacy)12+IE10+

-

Firefox for Android4+iOS Safari5+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

An element is :valid or :invalid when its contents or value is, respectively, valid or invalid with respect to data validity semantics defined by the document language (e.g. [\[XFORMS11\]](https://drafts.csswg.org/selectors-4/#biblio-xforms11) or [\[HTML5\]](https://drafts.csswg.org/selectors-4/#biblio-html5)). An element which lacks data validity semantics is neither [:valid](https://drafts.csswg.org/selectors-4/#valid-pseudo) nor [:invalid](https://drafts.csswg.org/selectors-4/#invalid-pseudo).

Note: There is a difference between an element which has no constraints, and thus would always be [:valid](https://drafts.csswg.org/selectors-4/#valid-pseudo), and one which has no data validity semantics at all, and thus is neither :valid nor [:invalid](https://drafts.csswg.org/selectors-4/#invalid-pseudo). In HTML, for example, an `<input type="text">` element may have no constraints, but a [p](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element) element has no validity semantics at all, and so it never matches either of these pseudo-classes.

#### 12.3.3. The Range Pseudo-classes: [:in-range](https://drafts.csswg.org/selectors-4/#in-range-pseudo) and [:out-of-range](https://drafts.csswg.org/selectors-4/#out-of-range-pseudo) range-pseudos)

**✔**MDN

[:in-range](https://developer.mozilla.org/en-US/docs/Web/CSS/:in-range "The :in-range CSS pseudo-class represents an <input> element whose current value is within the range limits specified by the min and max attributes.")

In all current engines.

Firefox29+Safari5.1+Chrome10+

-

Opera11+Edge79+

-

Edge (Legacy)13+IENone

-

Firefox for Android16+iOS Safari5+Chrome for Android18+Android WebView2.3+Samsung Internet1.0+Opera Mobile11+

[:out-of-range](https://developer.mozilla.org/en-US/docs/Web/CSS/:out-of-range "The :out-of-range CSS pseudo-class represents an <input> element whose current value is outside the range limits specified by the min and max attributes.")

In all current engines.

Firefox29+Safari5.1+Chrome10+

-

Opera11+Edge79+

-

Edge (Legacy)13+IENone

-

Firefox for Android16+iOS Safari5+Chrome for Android18+Android WebView2.3+Samsung Internet1.0+Opera Mobile11+

The :in-range and :out-of-range pseudo-classes apply only to elements that have range limitations. An element is [:in-range](https://drafts.csswg.org/selectors-4/#in-range-pseudo) or [:out-of-range](https://drafts.csswg.org/selectors-4/#out-of-range-pseudo) when the value that the element is bound to is in range or out of range with respect to its range limits as defined by the document language. An element that lacks data range limits or is not a form control is neither :in-range nor :out-of-range. E.g. a slider element with a value of 11 presented as a slider control that only represents the values from 1-10 is :out-of-range. Another example is a menu element with a value of "E" that happens to be presented in a popup menu that only has choices "A", "B" and "C".

#### 12.3.4. The Optionality Pseudo-classes: [:required](https://drafts.csswg.org/selectors-4/#required-pseudo) and [:optional](https://drafts.csswg.org/selectors-4/#optional-pseudo) opt-pseudos)

**✔**MDN

[:optional](https://developer.mozilla.org/en-US/docs/Web/CSS/:optional "The :optional CSS pseudo-class represents any <input>, <select>, or <textarea> element that does not have the required attribute set on it.")

In all current engines.

Firefox4+Safari5+Chrome10+

-

Opera10+Edge79+

-

Edge (Legacy)12+IE10+

-

Firefox for Android4+iOS Safari5+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

[:required](https://developer.mozilla.org/en-US/docs/Web/CSS/:required "The :required CSS pseudo-class represents any <input>, <select>, or <textarea> element that has the required attribute set on it.")

In all current engines.

Firefox4+Safari5+Chrome10+

-

Opera10+Edge79+

-

Edge (Legacy)12+IE10+

-

Firefox for Android4+iOS Safari5+Chrome for Android18+Android WebView4.4.3+Samsung Internet1.0+Opera Mobile10.1+

A form element is :required or :optional if a value for it is, respectively, required or optional before the form it belongs to can be validly submitted. Elements that are not form elements are neither required nor optional.

#### 12.3.5. The User-interaction Pseudo-class: [:user-invalid](https://drafts.csswg.org/selectors-4/#user-invalid-pseudo) user-pseudos)

**⚠**MDN

[:-moz-ui-invalid](https://developer.mozilla.org/en-US/docs/Web/CSS/:-moz-ui-invalid "The :-moz-ui-invalid CSS pseudo-class represents any validated form element whose value isn't valid based on their validation constraints, in certain circumstances. This pseudo-class is applied according to the following rules:")

In only one current engine.

Firefox4+SafariNoneChromeNone

-

OperaNoneEdgeNone

-

Edge (Legacy)NoneIENone

-

Firefox for Android4+iOS SafariNoneChrome for AndroidNoneAndroid WebViewNoneSamsung InternetNoneOpera MobileNone

The :user-invalid pseudo-class represents an element with incorrect input, but only _after_ the user has significantly interacted with it. The [:user-invalid](https://drafts.csswg.org/selectors-4/#user-invalid-pseudo) pseudo-class must match an [:invalid](https://drafts.csswg.org/selectors-4/#invalid-pseudo), [:out-of-range](https://drafts.csswg.org/selectors-4/#out-of-range-pseudo), or blank-but-[:required](https://drafts.csswg.org/selectors-4/#required-pseudo) elements between the time the user has attempted to submit the form and before the user has interacted again with the form element. User-agents may allow it to match such elements at other times, as would be appropriate for highlighting an error to the user. For example, a UA may choose to have :user-invalid match an :invalid element once the user has typed some text into it and changed the focus to another element, and to stop matching only after the user has successfully corrected the input.

 example-42eddba4)For example, the input in the following document fragment would match [:invalid](https://drafts.csswg.org/selectors-4/#invalid-pseudo) as soon as the page is loaded (because it the initial value violates the max-constraint), but it won’t match [:user-invalid](https://drafts.csswg.org/selectors-4/#user-invalid-pseudo) until the user significantly interacts with the element, or attempts to submit the form it’s part of.

<form>
  <label>
    Volume:
    <input name='vol' type=number min=0 max=10 value=11>
  </label>
  ...
</form>

 issue-b776312b)Cross-check with [:-moz-ui-invalid](https://developer.mozilla.org/en-US/docs/Web/CSS/%3A-moz-ui-invalid).

 issue-fcbee641)Add [:-moz-ui-valid](https://developer.mozilla.org/en-US/docs/Web/CSS/%3A-moz-ui-valid) as :user-valid per WG resolution.

 issue-a71d9d5b)Evaluate proposed [:dirty pseudo-class](https://lists.w3.org/Archives/Public/www-style/2014Feb/0511.html)

 issue-df919919)Clarify that this (and [:invalid](https://drafts.csswg.org/selectors-4/#invalid-pseudo)/[:valid](https://drafts.csswg.org/selectors-4/#valid-pseudo)) can apply to form and fieldset elements.

## 13\. Tree-Structural pseudo-classes structural-pseudos)

Selectors introduces the concept of structural pseudo-classes to permit selection based on extra information that lies in the document tree but cannot be represented by other simple selectors or combinators.

Standalone text and other non-element nodes are not counted when calculating the position of an element in the list of children of its parent. When calculating the position of an element in the list of children of its parent, the index numbering starts at 1.

The [structural pseudo-classes](https://drafts.csswg.org/selectors-4/#structural-pseudo-classes) only apply to elements in the document tree; they must never match [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element).

### 13.1. [:root](https://drafts.csswg.org/selectors-4/#root-pseudo) pseudo-class the-root-pseudo)

**✔**MDN

[:root](https://developer.mozilla.org/en-US/docs/Web/CSS/:root "The :root CSS  pseudo-class matches the root element of a tree representing the document. In HTML, :root represents the <html> element and is identical to the selector html, except that its specificity is higher.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile14+

The :root pseudo-class represents an element that is the root of the document.

For example, in a DOM document, the [:root](https://drafts.csswg.org/selectors-4/#root-pseudo) pseudo-class matches the root element of the [Document](https://dom.spec.whatwg.org/#document) object. In HTML, this would be the [html](https://html.spec.whatwg.org/multipage/semantics.html#the-html-element) element (unless scripting has been used to modify the document).

### 13.2. [:empty](https://drafts.csswg.org/selectors-4/#empty-pseudo) pseudo-class the-empty-pseudo)

**✔**MDN

[:empty](https://developer.mozilla.org/en-US/docs/Web/CSS/:empty "The :empty CSS pseudo-class represents any element that has no children. Children can be either element nodes or text (including whitespace). Comments, processing instructions, and CSS content do not affect whether an element is considered empty.")

In all current engines.

Firefox1+Safari3.1+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.1+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

The :empty pseudo-class represents an element that has no children except, optionally, [document white space characters](https://drafts.csswg.org/css-text-3/#white-space). In terms of the document tree, only element nodes and content nodes (such as [\[DOM\]](https://drafts.csswg.org/selectors-4/#biblio-dom) text nodes, and entity references) whose data has a non-zero length must be considered as affecting emptiness; comments, processing instructions, and other nodes must not affect whether an element is considered empty or not.

 example-3846287b)Examples: p:empty is a valid representation of the `[p](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element)` elements in the following HTML fragment:

<p></p>
<p>
<p> </p>
<p></p>

div:empty is not a valid representation of the `<div>` elements in the following fragment:

<div>text</div>
<div><p></p></div>
<div>&nbsp;</div>
<div><p>bla</p></div>
<div>this is not <p>:empty</p></div>

Note: In Level 2 and Level 3 of Selectors, [:empty](https://drafts.csswg.org/selectors-4/#empty-pseudo) did not match elements that contained only white space. This was changed so that that—given white space is largely collapsible in HTML and is therefore used for source code formatting, and especially because elements with omitted end tags are likely to absorb such white space into their DOM text contents—elements which authors perceive of as empty can be selected by this selector, as they expect.

### 13.3. Child-indexed Pseudo-classes child-index)

The pseudo-classes defined in this section select elements based on their index amongst their [inclusive siblings](https://dom.spec.whatwg.org/#concept-tree-inclusive-sibling).

Note: Selectors 3 described these selectors as selecting elements based on their index in the child list of their parents. (This description survives in the name of this very section, and the names of several of the pseudo-classes.) As there was no reason to exclude them from matching elements without parents, or with non-element parents, they have been rephrased to refer to an element’s relative index amongst its siblings.

#### 13.3.1. [:nth-child()](https://drafts.csswg.org/selectors-4/#nth-child-pseudo) pseudo-class the-nth-child-pseudo)

**✔**MDN

[:nth-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child "The :nth-child() CSS pseudo-class matches elements based on their position in a group of siblings.")

In all current engines.

Firefox3.5+Safari3.1+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The :nth-child(An+B \[of S\]? ) pseudo-class notation represents elements that are among An+Bth elements from the list composed of their [inclusive siblings](https://dom.spec.whatwg.org/#concept-tree-inclusive-sibling) that match the [selector list](https://drafts.csswg.org/selectors-4/#selector-list) S. If S is omitted, it defaults to \*|\*.

The An+B notation and its interpretation are defined in [CSS Syntax 3 §6 The An+B microsyntax](https://www.w3.org/TR/css-syntax-3/#anb-microsyntax); it represents any index i = An + B for any non-negative integer n.

Note: For these purposes, the list of elements is **1-indexed**; that is, the first child of an element has index 1, and will be matched by :nth-child(2n+1), because when `n=0` the expression evaluates to 1.

For example, this selector could address every other row in a table, and could be used to alternate the color of paragraph text in a cycle of four.

 example-b8d691c9)Examples:

:nth-child(even)   /\* represents the 2nd, 4th, 6th, etc elements
:nth-child(10n-1)  /\* represents the 9th, 19th, 29th, etc elements \*/
:nth-child(10n+9)  /\* Same \*/
:nth-child(10n+-1) /\* Syntactically invalid, and would be ignored \*/

Note: The specificity of the [:nth-child()](https://drafts.csswg.org/selectors-4/#nth-child-pseudo) pseudo-class is the specificity of a single pseudo-class plus, if S is specified, the specificity of the most specific [complex selector](https://drafts.csswg.org/selectors-4/#complex) in S. See [§ 16 Calculating a selector’s specificity](https://drafts.csswg.org/selectors-4/#specificity-rules). Thus S:nth-child(An+B) and :nth-child(An+B of S) have the exact same specificity, although they do differ in behavior (see example below).

 example-3c07f717)By passing a selector argument, we can select the Nth element that matches that selector. For example, the following selector matches the first three “important” list items, denoted by the .important class:

:nth-child(-n+3 of li.important)

Note that this is different from moving the selector outside of the function, like:

li.important:nth-child(-n+3)

This selector instead just selects the first three children if they also happen to be "important" list items.

 example-48f80a26)Here’s another example of using the selector argument, to ensure that zebra-striping a table works correctly.

Normally, to zebra-stripe a table’s rows, an author would use CSS similar to the following:

tr {
  background: white;
}
tr:nth-child(even) {
  background: silver;
}

However, if some of the rows are hidden and not displayed, this can break up the pattern, causing multiple adjacent rows to have the same background color. Assuming that rows are hidden with the \[hidden\] attribute in HTML, the following CSS would zebra-stripe the table rows robustly, maintaining a proper alternating background regardless of which rows are hidden:

tr {
  background: white;
}
tr:nth-child(even of :not(\[hidden\])) {
  background: silver;
}

#### 13.3.2. [:nth-last-child()](https://drafts.csswg.org/selectors-4/#nth-last-child-pseudo) pseudo-class the-nth-last-child-pseudo)

**✔**MDN

[:nth-last-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-last-child "The :nth-last-child() CSS pseudo-class matches elements based on their position among a group of siblings, counting from the end.")

In all current engines.

Firefox3.5+Safari3.2+Chrome4+

-

Opera9+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.2+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The :nth-last-child(An+B \[of S\]? ) pseudo-class notation represents elements that are among An+Bth elements from the list composed of their [inclusive siblings](https://dom.spec.whatwg.org/#concept-tree-inclusive-sibling) that match the [selector list](https://drafts.csswg.org/selectors-4/#selector-list) S, counting backwards from the end. If S is omitted, it defaults to \*|\*.

Note: The specificity of the [:nth-last-child()](https://drafts.csswg.org/selectors-4/#nth-last-child-pseudo) pseudo-class, like the [:nth-child()](https://drafts.csswg.org/selectors-4/#nth-child-pseudo) pseudo-class, combines the specificity of a regular pseudo-class with that of its selector argument S. See [§ 16 Calculating a selector’s specificity](https://drafts.csswg.org/selectors-4/#specificity-rules).

The CSS Syntax Module [\[CSS3SYN\]](https://drafts.csswg.org/selectors-4/#biblio-css3syn) defines the [An+B notation](https://drafts.csswg.org/css-syntax/#anb).

 example-bee68ad4)Examples:

tr:nth-last-child(-n+2)    /\* represents the two last rows of an HTML table \*/

foo:nth-last-child(odd)    /\* represents all odd foo elements in their parent element,
                              counting from the last one \*/

#### 13.3.3. [:first-child](https://drafts.csswg.org/selectors-4/#first-child-pseudo) pseudo-class the-first-child-pseudo)

**✔**MDN

[:first-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:first-child "The :first-child CSS pseudo-class represents the first element among a group of sibling elements.")

In all current engines.

Firefox3+Safari3.1+Chrome4+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE7+

-

Firefox for Android4+iOS Safari4+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The :first-child pseudo-class represents an element that if first among its [inclusive siblings](https://dom.spec.whatwg.org/#concept-tree-inclusive-sibling). Same as :nth-child(1).

 example-72934891)Examples: The following selector represents a [p](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element) element that is the first child of a [div](https://html.spec.whatwg.org/multipage/grouping-content.html#the-div-element) element:

div > p:first-child

This selector can represent the `p` inside the `div` of the following fragment:

<p> The last P before the note.</p>
<div class="note">
   <p> The first P inside the note.</p>
</div>

but cannot represent the second `p` in the following fragment:

<p> The last P before the note.</p>
<div class="note">
   <h2> Note </h2>
   <p> The first P inside the note.</p>
</div>

The following two selectors are usually equivalent:

\* > a:first-child /\* a is first child of any element \*/
a:first-child /\* Same (assuming a is not the root element) \*/

#### 13.3.4. [:last-child](https://drafts.csswg.org/selectors-4/#last-child-pseudo) pseudo-class the-last-child-pseudo)

**✔**MDN

[:last-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:last-child "The :last-child CSS pseudo-class represents the last element among a group of sibling elements.")

In all current engines.

Firefox1+Safari3.2+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.2+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The :last-child pseudo-class represents an element that is last among its [inclusive siblings](https://dom.spec.whatwg.org/#concept-tree-inclusive-sibling). Same as :nth-last-child(1).

 example-48137186)Example: The following selector represents a list item `li` that is the last child of an ordered list `ol`.

ol > li:last-child

#### 13.3.5. [:only-child](https://drafts.csswg.org/selectors-4/#only-child-pseudo) pseudo-class the-only-child-pseudo)

**✔**MDN

[:only-child](https://developer.mozilla.org/en-US/docs/Web/CSS/:only-child "The :only-child CSS pseudo-class represents an element without any siblings. This is the same as :first-child:last-child or :nth-child(1):nth-last-child(1), but with a lower specificity.")

In all current engines.

Firefox1.5+Safari3.1+Chrome2+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The :only-child pseudo-class represents an element that has no siblings. Same as :first-child:last-child or :nth-child(1):nth-last-child(1), but with a lower specificity.

### 13.4. Typed Child-indexed Pseudo-classes typed-child-index)

The pseudo-elements in this section are similar to the [Child Index Pseudo-classes](https://drafts.csswg.org/selectors-4/#child-index), but they resolve based on an element’s index **among elements of the same [type (tag name)](https://drafts.csswg.org/selectors-4/#type-selectors)** in their sibling list.

#### 13.4.1. [:nth-of-type()](https://drafts.csswg.org/selectors-4/#nth-of-type-pseudo) pseudo-class the-nth-of-type-pseudo)

**✔**MDN

[:nth-of-type](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-of-type "The :nth-of-type() CSS pseudo-class matches elements of a given type (tag name), based on their position among a group of siblings.")

In all current engines.

Firefox3.5+Safari3.1+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.1+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

The :nth-of-type(An+B) pseudo-class notation represents the same elements that would be matched by :nth-child(|An+B| of S), where S is a [type selector](https://drafts.csswg.org/selectors-4/#type-selector) and namespace prefix matching the element in question. For example, when considering whether an HTML `[img](https://html.spec.whatwg.org/multipage/embedded-content.html#the-img-element)` element matches this [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class), the S in question is html|img (assuming an appropriate `html` namespace is declared).

 example-3d09bf4d)CSS example: This allows an author to alternate the position of floated images:

img:nth-of-type(2n+1) { float: right; }
img:nth-of-type(2n) { float: left; }

Note: If the type of the element is known ahead of time, this pseudo-class is equivalent to using [:nth-child()](https://drafts.csswg.org/selectors-4/#nth-child-pseudo) with a type selector. That is, img:nth-of-type(2) is equivalent to \*:nth-child(2 of img).

#### 13.4.2. [:nth-last-of-type()](https://drafts.csswg.org/selectors-4/#nth-last-of-type-pseudo) pseudo-class the-nth-last-of-type-pseudo)

**✔**MDN

[:nth-last-of-type](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-last-of-type "The :nth-last-of-type() CSS pseudo-class matches elements of a given type, based on their position among a group of siblings, counting from the end.")

In all current engines.

Firefox3.5+Safari3.2+Chrome4+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.2+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

The :nth-last-of-type(An+B) pseudo-class notation represents the same elements that would be matched by :nth-last-child(|An+B| of S), where S is a [type selector](https://drafts.csswg.org/selectors-4/#type-selector) and namespace prefix matching the element in question. For example, when considering whether an HTML `[img](https://html.spec.whatwg.org/multipage/embedded-content.html#the-img-element)` element matches this [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class), the S in question is html|img (assuming an appropriate `html` namespace is declared).

 example-b89418c8)Example: To represent all `h2` children of an XHTML `body` except the first and last, one could use the following selector:

body > h2:nth-of-type(n+2):nth-last-of-type(n+2) 

In this case, one could also use [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo), although the selector ends up being just as long:

body > h2:not(:first-of-type):not(:last-of-type) 

#### 13.4.3. [:first-of-type](https://drafts.csswg.org/selectors-4/#first-of-type-pseudo) pseudo-class the-first-of-type-pseudo)

**✔**MDN

[:first-of-type](https://developer.mozilla.org/en-US/docs/Web/CSS/:first-of-type "The :first-of-type CSS pseudo-class represents the first element of its type among a group of sibling elements.")

In all current engines.

Firefox3.5+Safari3.2+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.2+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

The :first-of-type pseudo-class represents the same element as :nth-of-type(1).

 example-16f73753)Example: The following selector represents a definition title `dt` inside a definition list `dl`, this `dt` being the first of its type in the list of children of its parent element.

dl dt:first-of-type

It is a valid description for the first two `dt` elements in the following example but not for the third one:

<dl>
  <dt>gigogne</dt>
  <dd>
    <dl>
      <dt>fusée</dt>
      <dd>multistage rocket</dd>
      <dt>table</dt>
      <dd>nest of tables</dd>
    </dl>
  </dd>
</dl>

#### 13.4.4. [:last-of-type](https://drafts.csswg.org/selectors-4/#last-of-type-pseudo) pseudo-class the-last-of-type-pseudo)

**✔**MDN

[:last-of-type](https://developer.mozilla.org/en-US/docs/Web/CSS/:last-of-type "The :last-of-type CSS pseudo-class represents the last element of its type among a group of sibling elements.")

In all current engines.

Firefox3.5+Safari3.2+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.2+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

The :last-of-type pseudo-class represents the same element as :nth-last-of-type(1).

 example-fee30007)Example: The following selector represents the last data cell `td` of a table row `tr`.

tr > td:last-of-type

#### 13.4.5. [:only-of-type](https://drafts.csswg.org/selectors-4/#only-of-type-pseudo) pseudo-class the-only-of-type-pseudo)

**✔**MDN

[:only-of-type](https://developer.mozilla.org/en-US/docs/Web/CSS/:only-of-type "The :only-of-type CSS pseudo-class represents an element that has no siblings of the same type.")

In all current engines.

Firefox3.5+Safari3.2+Chrome1+

-

Opera9.5+Edge79+

-

Edge (Legacy)12+IE9+

-

Firefox for Android4+iOS Safari3.2+Chrome for Android18+Android WebView2+Samsung Internet1.0+Opera Mobile10.1+

The :only-of-type pseudo-class represents the same element as :first-of-type:last-of-type.

## 14\. Combinators combinators)

### 14.1. Descendant combinator ( ) descendant-combinators)

**✔**MDN

[Descendant\_combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_combinator "The descendant combinator — typically represented by a single space ( ) character — combines two selectors such that elements matched by the second selector are selected if they have an ancestor (parent, parent's parent, parent's parent's parent, etc) element matching the first selector. Selectors that utilize a descendant combinator are called descendant selectors.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE3+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

At times, authors may want selectors to describe an element that is the descendant of another element in the document tree (e.g., "an [em](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-em-element) element that is contained within an H1 element"). The descendant combinator expresses such a relationship.

A descendant combinator is whitespace that separates two [compound selectors](https://drafts.csswg.org/selectors-4/#compound).

A selector of the form A B represents an element `B` that is an arbitrary descendant of some ancestor element `A`.

 example-13246ba1)Examples: For example, consider the following selector:

h1 em

It represents an [em](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-em-element) element being the descendant of an h1 element. It is a correct and valid, but partial, description of the following fragment:

<h1>This <span class="myclass">headline
is <em>very</em> important</span></h1>

The following selector:

div \* p

represents a [p](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element) element that is a grandchild or later descendant of a [div](https://html.spec.whatwg.org/multipage/grouping-content.html#the-div-element) element. Note the whitespace on either side of the "\*" is not part of the universal selector; the whitespace is a combinator indicating that the `div` must be the ancestor of some element, and that that element must be an ancestor of the `p`. The following selector, which combines descendant combinators and [attribute selectors](https://drafts.csswg.org/selectors-4/#attribute-selectors), represents an element that (1) has the `href` attribute set and (2) is inside a `p` that is itself inside a `div`:

div p \*\[href\]

### 14.2. Child combinator (`>`) child-combinators)

**✔**MDN

[Child\_combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_combinator "The child combinator (>) is placed between two CSS selectors. It matches only those elements matched by the second selector that are the direct children of elements matched by the first.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera4+Edge79+

-

Edge (Legacy)12+IE7+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

A child combinator describes a childhood relationship between two elements. A child combinator is made of the "greater-than sign" (U+003E, \> selectordef-child)) code point and separates two [compound selectors](https://drafts.csswg.org/selectors-4/#compound).

 example-63e612ba)Examples: The following selector represents a [p](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element) element that is child of `body`:

body > p

The following example combines descendant combinators and child combinators.

div ol>li p

It represents a [p](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element) element that is a descendant of an [li](https://html.spec.whatwg.org/multipage/grouping-content.html#the-li-element) element; the li element must be the child of an [ol](https://html.spec.whatwg.org/multipage/grouping-content.html#the-ol-element) element; the ol element must be a descendant of a `div`. Notice that the optional white space around the ">" combinator has been left out.

For information on selecting the first child of an element, please see the section on the [:first-child](https://drafts.csswg.org/selectors-4/#first-child-pseudo) pseudo-class above.

### 14.3. Next-sibling combinator (`+`) adjacent-sibling-combinators)

**✔**MDN

[Adjacent\_sibling\_combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_combinator "The adjacent sibling combinator (+) separates two selectors and matches the second element only if it immediately follows the first element, and both are children of the same parent element.")

In all current engines.

Firefox1+Safari1+Chrome1+

-

Opera3.5+Edge79+

-

Edge (Legacy)12+IE7+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile10.1+

The next-sibling combinator is made of the “plus sign” (U+002B, + selectordef-adjacent)) code point that separates two [compound selectors](https://drafts.csswg.org/selectors-4/#compound). The elements represented by the two compound selectors share the same parent in the document tree and the element represented by the first compound selector immediately precedes the element represented by the second one. Non-element nodes (e.g. text between elements) are ignored when considering the adjacency of elements.

 example-0f0597d9)Examples: The following selector represents a [p](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element) element immediately following a math element:

math + p

The following selector is conceptually similar to the one in the previous example, except that it adds an attribute selector — it adds a constraint to the h1 element, that it must have `class="opener"`:

h1.opener + h2

### 14.4. Subsequent-sibling combinator (`~`) general-sibling-combinators)

**✔**MDN

[General\_sibling\_combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/General_sibling_combinator "The general sibling combinator (~) separates two selectors and matches all iterations of the second element, that are following the first element (though not necessarily immediately), and are children of the same parent element.")

In all current engines.

Firefox1+Safari3+Chrome1+

-

Opera9+Edge79+

-

Edge (Legacy)12+IE7+

-

Firefox for Android4+iOS Safari1+Chrome for Android18+Android WebView37+Samsung Internet1.0+Opera Mobile14+

The subsequent-sibling combinator is made of the "tilde" (U+007E, ~ selectordef-sibling)) code point that separates two [compound selectors](https://drafts.csswg.org/selectors-4/#compound). The elements represented by the two compound selectors share the same parent in the document tree and the element represented by the first compound selector precedes (not necessarily immediately) the element represented by the second one.

 example-ae614b62)

h1 ~ pre

represents a [pre](https://html.spec.whatwg.org/multipage/grouping-content.html#the-pre-element) element following an `h1`. It is a correct and valid, but partial, description of:

<h1>Definition of the function a</h1>
<p>Function a(x) has to be applied to all figures in the table.</p>
<pre>function a(x) = 12x/13.5</pre>

## 15\. Grid-Structural Selectors table-pseudos)

The double-association of a cell in a 2D grid (to its row and column) cannot be represented by parentage in a hierarchical markup language. Only one of those associations can be represented hierarchically: the other must be explicitly or implicitly defined in the document language semantics. In both HTML and DocBook, two of the most common hierarchical markup languages, the markup is row-primary (that is, the row associations are represented hierarchically); the columns must be implied. To be able to represent such implied column-based relationships, the [column combinator](https://drafts.csswg.org/selectors-4/#column-combinator) and the [:nth-col()](https://drafts.csswg.org/selectors-4/#nth-col-pseudo) and [:nth-last-col()](https://drafts.csswg.org/selectors-4/#nth-last-col-pseudo) pseudo-classes are defined. In a column-primary format, these pseudo-classes match against row associations instead.

### 15.1. Column combinator (`||`) the-column-combinator)

**⚠**MDN

[Column\_combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Column_combinator "The column combinator (||) is placed between two CSS selectors. It matches only those elements matched by the second selector that belong to the column elements matched by the first.")

In no current engines.

FirefoxNoneSafariNoneChromeNone

-

OperaNoneEdgeNone

-

Edge (Legacy)NoneIENone

-

Firefox for AndroidNoneiOS SafariNoneChrome for AndroidNoneAndroid WebViewNoneSamsung InternetNoneOpera MobileNone

The column combinator, which consists of two pipes (|| selectordef-column)) represents the relationship of a column element to a cell element belonging to the column it represents. Column membership is determined based on the semantics of the document language only: whether and how the elements are presented is not considered. If a cell element belongs to more than one column, it is represented by a selector indicating membership in any of those columns.

 example-60f47339)The following example makes cells C, E, and G gray.

col.selected || td {
  background: gray;
  color: white;
  font-weight: bold;
}

<table>
  <col span="2">
  <col class="selected">
  <tr><td>A <td>B <td>C
  <tr><td colspan="2">D <td>E
  <tr><td>F <td colspan="2">G
</table>

### 15.2. [:nth-col()](https://drafts.csswg.org/selectors-4/#nth-col-pseudo) pseudo-class the-nth-col-pseudo)

The :nth-col(An+B) pseudo-class notation represents a cell element belonging to a column that has An+B\-1 columns **before** it, for any positive integer or zero value of `n`. Column membership is determined based on the semantics of the document language only: whether and how the elements are presented is not considered. If a cell element belongs to more than one column, it is represented by a selector indicating any of those columns.

The CSS Syntax Module [\[CSS3SYN\]](https://drafts.csswg.org/selectors-4/#biblio-css3syn) defines the [An+B notation](https://drafts.csswg.org/css-syntax/#anb).

### 15.3. [:nth-last-col()](https://drafts.csswg.org/selectors-4/#nth-last-col-pseudo) pseudo-class the-nth-last-col-pseudo)

The :nth-last-col(An+B) pseudo-class notation represents a cell element belonging to a column that has An+B\-1 columns **after** it, for any positive integer or zero value of `n`. Column membership is determined based on the semantics of the document language only: whether and how the elements are presented is not considered. If a cell element belongs to more than one column, it is represented by a selector indicating any of those columns.

The CSS Syntax Module [\[CSS3SYN\]](https://drafts.csswg.org/selectors-4/#biblio-css3syn) defines the [An+B notation](https://drafts.csswg.org/css-syntax/#anb).

## 16\. Calculating a selector’s specificity specificity-rules)

A selector’s specificity is calculated for a given element as follows:

- count the number of ID selectors in the selector (= A)
- count the number of class selectors, attributes selectors, and pseudo-classes in the selector (= B)
- count the number of type selectors and pseudo-elements in the selector (= C)
- ignore the universal selector

If the selector is a [selector list](https://drafts.csswg.org/selectors-4/#selector-list), this number is calculated for each selector in the list. For a given matching process against the list, the specificity in effect is that of the most specific selector in the list that matches.

A few pseudo-classes provide “evaluation contexts” for other selectors, and so have their specificity defined specially:

- The specificity of an [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo), [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo), or [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo) pseudo-class is replaced by the specificity of the most specific [complex selector](https://drafts.csswg.org/selectors-4/#complex) in its [selector list](https://drafts.csswg.org/selectors-4/#selector-list) argument.
- Analogously, the specificity of an [:nth-child()](https://drafts.csswg.org/selectors-4/#nth-child-pseudo) or [:nth-last-child()](https://drafts.csswg.org/selectors-4/#nth-last-child-pseudo) selector is the specificity of the pseudo class itself (counting as one pseudo-class selector) plus the specificity of the most specific [complex selector](https://drafts.csswg.org/selectors-4/#complex) in its [selector list](https://drafts.csswg.org/selectors-4/#selector-list) argument (if any).
- The specificity of a [:where()](https://drafts.csswg.org/selectors-4/#where-pseudo) pseudo-class is replaced by zero.

 example-bd54871c)For example:

- :is(em, `#foo`) has a specificity of (1,0,0)—like an ID selector (`#foo`)—when matched against any of `<em>`, `<p id=foo>`, or `<em id=foo>`.
- .qux:where(em, ``#foo#bar#baz``) has a specificity of (0,1,0): only the .qux outside the [:where()](https://drafts.csswg.org/selectors-4/#where-pseudo) contributes to selector specificity.
- :nth-child(even of li, .item) has a specificity of (0,2,0)—like a class selector (.item) plus a pseudo-class—when matched against any of `<li>`, `<ul class=item>`, or `<li class=item id=foo>`.
- :not(em, strong#foo) has a specificity of (1,0,1)—like a tag selector ([strong](https://drafts.csswg.org/css-speech-1/#valdef-pause-before-strong)) combined with an ID selector (#foo)—when matched against any element.

Specificities are compared by comparing the three components in order: the specificity with a larger A value is more specific; if the two A values are tied, then the specificity with a larger B value is more specific; if the two B values are also tied, then the specificity with a larger C value is more specific; if all the values are tied, the two specificities are equal.

Due to storage limitations, implementations may have limitations on the size of A, B, or C. If so, values higher than the limit must be clamped to that limit, and not overflow.

 example-d97bd125)Examples:

\*               /\* a=0 b=0 c=0 \*/
LI              /\* a=0 b=0 c=1 \*/
UL LI           /\* a=0 b=0 c=2 \*/
UL OL+LI        /\* a=0 b=0 c=3 \*/
H1 + \*\[REL=up\]  /\* a=0 b=1 c=1 \*/
UL OL LI.red    /\* a=0 b=1 c=3 \*/
LI.red.level    /\* a=0 b=2 c=1 \*/
#x34y           /\* a=1 b=0 c=0 \*/
#s12:not(FOO)   /\* a=1 b=0 c=1 \*/
.foo :is(.bar, #baz)
                /\* a=1 b=1 c=0 \*/

Note: Repeated occurrences of the same simple selector are allowed and do increase specificity.

Note: The specificity of the styles specified in an HTML `style` attribute [is described in CSS Style Attributes](https://www.w3.org/TR/css-style-attr/#interpret). [\[CSSSTYLEATTR\]](https://drafts.csswg.org/selectors-4/#biblio-cssstyleattr)

## 17\. Grammar grammar)

Selectors are [parsed](https://drafts.csswg.org/css-syntax-3/#css-parse-something-according-to-a-css-grammar) according to the following grammar:

<selector-list> = [<complex-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector-list)

<complex-selector-list> = [<complex-selector>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector)[#](https://drafts.csswg.org/css-values-4/#mult-comma)

<compound-selector-list> typedef-compound-selector-list) = [<compound-selector>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector)[#](https://drafts.csswg.org/css-values-4/#mult-comma)

<simple-selector-list> typedef-simple-selector-list) = [<simple-selector>](https://drafts.csswg.org/selectors-4/#typedef-simple-selector)[#](https://drafts.csswg.org/css-values-4/#mult-comma)

<relative-selector-list> = [<relative-selector>](https://drafts.csswg.org/selectors-4/#typedef-relative-selector)[#](https://drafts.csswg.org/css-values-4/#mult-comma)

<complex-selector> = [<compound-selector>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector) \[ [<combinator>](https://drafts.csswg.org/selectors-4/#typedef-combinator)[?](https://drafts.csswg.org/css-values-4/#mult-opt) [<compound-selector>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector) \][\*](https://drafts.csswg.org/css-values-4/#mult-zero-plus)

<relative-selector> = [<combinator>](https://drafts.csswg.org/selectors-4/#typedef-combinator)[?](https://drafts.csswg.org/css-values-4/#mult-opt) [<complex-selector>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector)

<compound-selector> = \[ [<type-selector>](https://drafts.csswg.org/selectors-4/#typedef-type-selector)[?](https://drafts.csswg.org/css-values-4/#mult-opt) [<subclass-selector>](https://drafts.csswg.org/selectors-4/#typedef-subclass-selector)[\*](https://drafts.csswg.org/css-values-4/#mult-zero-plus)
                        \[ [<pseudo-element-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-element-selector) [<pseudo-class-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-class-selector)[\*](https://drafts.csswg.org/css-values-4/#mult-zero-plus) \][\*](https://drafts.csswg.org/css-values-4/#mult-zero-plus) \][!](https://drafts.csswg.org/css-values-4/#mult-req)

<simple-selector> = [<type-selector>](https://drafts.csswg.org/selectors-4/#typedef-type-selector) [|](https://drafts.csswg.org/css-values-4/#comb-one) [<subclass-selector>](https://drafts.csswg.org/selectors-4/#typedef-subclass-selector)

<combinator> = '>' [|](https://drafts.csswg.org/css-values-4/#comb-one) '+' [|](https://drafts.csswg.org/css-values-4/#comb-one) '~' [|](https://drafts.csswg.org/css-values-4/#comb-one) \[ '|' '|' \]

<type-selector> = [<wq-name>](https://drafts.csswg.org/selectors-4/#typedef-wq-name) [|](https://drafts.csswg.org/css-values-4/#comb-one) [<ns-prefix>](https://drafts.csswg.org/selectors-4/#typedef-ns-prefix)[?](https://drafts.csswg.org/css-values-4/#mult-opt) '\*'

<ns-prefix> = \[ [<ident-token>](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token) [|](https://drafts.csswg.org/css-values-4/#comb-one) '\*' \][?](https://drafts.csswg.org/css-values-4/#mult-opt) '|'

<wq-name> = [<ns-prefix>](https://drafts.csswg.org/selectors-4/#typedef-ns-prefix)[?](https://drafts.csswg.org/css-values-4/#mult-opt) [<ident-token>](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token)

<subclass-selector> = [<id-selector>](https://drafts.csswg.org/selectors-4/#typedef-id-selector) [|](https://drafts.csswg.org/css-values-4/#comb-one) [<class-selector>](https://drafts.csswg.org/selectors-4/#typedef-class-selector) [|](https://drafts.csswg.org/css-values-4/#comb-one)
                      [<attribute-selector>](https://drafts.csswg.org/selectors-4/#typedef-attribute-selector) [|](https://drafts.csswg.org/css-values-4/#comb-one) [<pseudo-class-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-class-selector)

<id-selector> = [<hash-token>](https://drafts.csswg.org/css-syntax-3/#typedef-hash-token)

<class-selector> = '.' [<ident-token>](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token)

<attribute-selector> = '\[' [<wq-name>](https://drafts.csswg.org/selectors-4/#typedef-wq-name) '\]' [|](https://drafts.csswg.org/css-values-4/#comb-one)
                       '\[' [<wq-name>](https://drafts.csswg.org/selectors-4/#typedef-wq-name) [<attr-matcher>](https://drafts.csswg.org/selectors-4/#typedef-attr-matcher) \[ [<string-token>](https://drafts.csswg.org/css-syntax-3/#typedef-string-token) [|](https://drafts.csswg.org/css-values-4/#comb-one) [<ident-token>](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token) \] [<attr-modifier>](https://drafts.csswg.org/selectors-4/#typedef-attr-modifier)[?](https://drafts.csswg.org/css-values-4/#mult-opt) '\]'

<attr-matcher> = \[ '~' [|](https://drafts.csswg.org/css-values-4/#comb-one) '|' [|](https://drafts.csswg.org/css-values-4/#comb-one) '^' [|](https://drafts.csswg.org/css-values-4/#comb-one) '$' [|](https://drafts.csswg.org/css-values-4/#comb-one) '\*' \][?](https://drafts.csswg.org/css-values-4/#mult-opt) '='

<attr-modifier> = i [|](https://drafts.csswg.org/css-values-4/#comb-one) s

<pseudo-class-selector> = ':' [<ident-token>](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token) [|](https://drafts.csswg.org/css-values-4/#comb-one)
                          ':' [<function-token>](https://drafts.csswg.org/css-syntax-3/#typedef-function-token) [<any-value>](https://drafts.csswg.org/css-syntax-3/#typedef-any-value) ')'

<pseudo-element-selector> = ':' [<pseudo-class-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-class-selector)

In interpreting the above grammar, the following rules apply:

-  white-space)White space is forbidden:
    - Between any of the top-level components of a [<compound-selector>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector) (that is, forbidden between the [<type-selector>](https://drafts.csswg.org/selectors-4/#typedef-type-selector) and [<subclass-selector>](https://drafts.csswg.org/selectors-4/#typedef-subclass-selector), or between the <subclass-selector> and [<pseudo-element-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-element-selector), etc).
        
    - Between _any_ of the components of a [<type-selector>](https://drafts.csswg.org/selectors-4/#typedef-type-selector) or a [<class-selector>](https://drafts.csswg.org/selectors-4/#typedef-class-selector).
        
    - Between the ':'s, or between the ':' and [<ident-token>](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token) or [<function-token>](https://drafts.csswg.org/css-syntax-3/#typedef-function-token), of a [<pseudo-element-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-element-selector) or a [<pseudo-class-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-class-selector).
        
    - Between _any_ of the components of a [<wq-name>](https://drafts.csswg.org/selectors-4/#typedef-wq-name).
        
    - Between the components of an [<attr-matcher>](https://drafts.csswg.org/selectors-4/#typedef-attr-matcher).
        
    - Between the components of a [<combinator>](https://drafts.csswg.org/selectors-4/#typedef-combinator).
        
-  single-colon-pseudos)The four [Level 2](https://www.w3.org/TR/CSS2/selectors.html#pseudo-element-selectors) [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) ([::before](https://drafts.csswg.org/css-pseudo-4/#selectordef-before), [::after](https://drafts.csswg.org/css-pseudo-4/#selectordef-after), [::first-line](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-line), and [::first-letter](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-letter)) may, for legacy reasons, be represented using the [<pseudo-class-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-class-selector) grammar, with only a single ":" character at their start.
- In [<id-selector>](https://drafts.csswg.org/selectors-4/#typedef-id-selector), the [<hash-token>](https://drafts.csswg.org/css-syntax-3/#typedef-hash-token)’s value must be an [identifier](https://drafts.csswg.org/css-syntax-3/#identifier).

Note: A selector is also subject to a variety of more specific syntactic constraints, and adherence to the grammar above is necessary _but not sufficient_ for the selector to be considered valid. See [§ 3.9 Invalid Selectors and Error Handling](https://drafts.csswg.org/selectors-4/#invalid) for additional rules for parsing selectors.

Note: The grammar above states that a combinator is optional between two [<compound-selector>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector)s in a [<complex-selector>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector). This is only for grammatical purposes, as the CSS Value Definition Syntax’s lax treatment of whitespace makes it difficult to indicate that a grammar term can _be_ whitespace. "Omitting" a combinator is actually just specifying the [descendant combinator](https://drafts.csswg.org/selectors-4/#descendant-combinator).

Note: In general, a [<pseudo-element-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-element-selector) is only valid if placed at the end of the last [<compound-selector>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector) in a [<complex-selector>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector). In some circumstances, however, it can be followed by more <pseudo-element-selector>s or [<pseudo-class-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-class-selector)s; but these are specified on a case-by-case basis. (For example, the [user action pseudo-classes](https://drafts.csswg.org/selectors-4/#user-action-pseudo-class) are allowed after any [pseudo-element](https://drafts.csswg.org/selectors-4/#pseudo-element), and the [tree-abiding pseudo-elements](https://drafts.csswg.org/css-pseudo-4/#tree-abiding) are allowed after the [::slotted()](https://drafts.csswg.org/css-scoping-1/#selectordef-slotted) pseudo-element.)

### 17.1. [<forgiving-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-selector-list) and [<forgiving-relative-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-relative-selector-list) forgiving-selector)

For legacy reasons, the general behavior of a selector list is that if any selector in the list fails to parse (because it uses new or UA-specific selector features, for instance), the entire selector list becomes invalid. This can make it hard to write CSS that uses new selectors and still works correctly in older user agents.

The [<forgiving-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-selector-list) production instead parses each selector in the list individually, simply ignoring ones that fail to parse, so the remaining selectors can still be used.

Note: Style rules still use the normal, unforgiving selector list behavior. [<forgiving-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-selector-list) is used in some functions, like [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo), which are similarly generic. Although it does have some minor implications on specificity, simply wrapping a style rule’s selector in :is() effectively "upgrades" it to become forgiving.

Syntactically, [<forgiving-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-selector-list) is equivalent to `[<any-value>](https://drafts.csswg.org/css-syntax-3/#typedef-any-value)?`. It is then [parsed as a forgiving selector list](https://drafts.csswg.org/selectors-4/#parse-as-a-forgiving-selector-list) to obtain its actual value.

To parse as a forgiving selector list given an input input:

1. [Parse a list](https://drafts.csswg.org/css-syntax-3/#css-parse-a-comma-separated-list-according-to-a-css-grammar) of [<complex-selector>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector)s from input, and let selector list be the result.
    
2. Remove all failure items from selector list, and all items that are [invalid selectors](https://drafts.csswg.org/selectors-4/#invalid-selector), then return a [<selector-list>](https://drafts.csswg.org/selectors-4/#typedef-selector-list) representing the remaining items in selector list. (This might be empty.)
    

[<forgiving-relative-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-relative-selector-list) is identical to [<forgiving-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-selector-list), except it parses its components as [<relative-selector>](https://drafts.csswg.org/selectors-4/#typedef-relative-selector) rather than [<complex-selector>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector).

## 18\. API Hooks api-hooks)

To aid in the writing of specs that use Selectors concepts, this section defines several API hooks that can be invoked by other specifications.

 issue-55d7bd68)Are these still necessary now that we have more rigorous definitions for [match](https://drafts.csswg.org/selectors-4/#match) and [invalid selector](https://drafts.csswg.org/selectors-4/#invalid-selector)? Nouns are a lot easier to coordinate across specification than predicates, and details like the exact order of elements returned from `querySelector` seem to make more sense being defined in the DOM specification than in Selectors.

### 18.1. Parse A Selector parse-selector)

This section defines how to parse a selector parse-a-selector) from a string source. It returns either a complex selector list, or failure.

1. Let selector be the result of [parsing](https://drafts.csswg.org/css-syntax-3/#css-parse-something-according-to-a-css-grammar) source as a [<selector-list>](https://drafts.csswg.org/selectors-4/#typedef-selector-list). If this returns failure, it’s an [invalid selector](https://drafts.csswg.org/selectors-4/#invalid-selector); return failure.
2. If selector is an [invalid selector](https://drafts.csswg.org/selectors-4/#invalid-selector) for any other reason (such as, for example, containing an undeclared namespace prefix), return failure.
3. Otherwise, return selector.

### 18.2. Parse A Relative Selector parse-relative-selector)

This section defines how to parse a relative selector parse-a-relative-selector) from a string source, against [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element) refs. It returns either a complex selector list, or failure.

1. Let selector be the result of [parsing](https://drafts.csswg.org/css-syntax-3/#css-parse-something-according-to-a-css-grammar) source as a [<relative-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-relative-selector-list). If this return failure, return failure.
2. Otherwise, if any simple selectors in selector are not recognized by the user agent, or selector is otherwise invalid in some way (such as, for example, containing an undeclared namespace prefix), return failure.
3. Otherwise, [absolutize selector](https://drafts.csswg.org/selectors-4/#absolutize-list) with refs as the [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element).
4. Return selector.

### 18.3. Match a Selector Against an Element match-against-element)

This section defines how to match a selector against an element.

APIs using this algorithm must provide a selector and an element.

Callers may optionally provide:

- a set of [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element), for resolving the [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo) pseudo-class against. If not specified, the set defaults to being empty.
    
     issue-8e6907ff)Should it instead default to the root element, to match the definition of [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo)?
    
    If the selector is a [relative selector](https://drafts.csswg.org/selectors-4/#relative-selector), the set of [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element) must not be empty.
    

This algorithm returns either success or failure.

For each [complex selector](https://drafts.csswg.org/selectors-4/#complex) in the given selector (which is taken to be a [list of complex selectors](https://drafts.csswg.org/selectors-4/#list-of-simple-selectors)), match the complex selector against element, as described in the following paragraph. If the matching returns success for any complex selector, then the algorithm return success; otherwise it returns failure.

To match a complex selector against an element, process it [compound selector](https://drafts.csswg.org/selectors-4/#compound) at a time, in right-to-left order. This process is defined recursively as follows:

- If any simple selectors in the rightmost compound selector does not match the element, return failure.
- Otherwise, if there is only one compound selector in the complex selector, return success.
- Otherwise, consider all possible elements that could be related to this element by the rightmost [combinator](https://drafts.csswg.org/selectors-4/#selector-combinator). If the operation of matching the selector consisting of this selector with the rightmost compound selector and rightmost combinator removed against any one of these elements returns success, then return success. Otherwise, return failure.

### 18.4. Match a Selector Against a Pseudo-element match-against-pseudo-element)

This section defines how to match a selector against a pseudo-element.

APIs using this algorithm must provide a selector and a pseudo-element. They may optionally provide the same things they may optionally provide to the algorithm to [match a selector against an element](https://drafts.csswg.org/selectors-4/#match-a-selector-against-an-element).

This algorithm returns success or failure.

For each [complex selector](https://drafts.csswg.org/selectors-4/#complex) in the given selector, if both:

- the rightmost [simple selector](https://drafts.csswg.org/selectors-4/#simple) in the complex selector matches pseudo-element, and
- the result of running [match a complex selector against an element](https://drafts.csswg.org/selectors-4/#match-a-complex-selector-against-an-element) on the remainder of the [complex selector](https://drafts.csswg.org/selectors-4/#complex) (with just the rightmost simple selector of its rightmost complex selector removed), pseudo-element’s corresponding element, and any optional parameters provided to this algorithm returns success,

then return success.

Otherwise (that is, if this doesn’t happen for any of the complex selectors in selector), return failure.

### 18.5. Match a Selector Against a Tree match-against-tree)

This section defines how to match a selector against a tree.

APIs using this algorithm must provide a selector, and one or more root elements indicating the [trees](https://dom.spec.whatwg.org/#concept-tree) that will be searched by the selector. All of the root elements must share the same [root](https://dom.spec.whatwg.org/#concept-tree-root), or else calling this algorithm is invalid.

They may optionally provide:

- A [scoping root](https://drafts.csswg.org/selectors-4/#scoping-root) indicating the selector is [scoped](https://drafts.csswg.org/selectors-4/#scoped-selector). If not specified, the selector defaults to being unscoped.
    
     issue-298e030f)This is now redundant with the root elements.
    
- A set of [:scope elements](https://drafts.csswg.org/selectors-4/#scope-element), which will match the [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo) pseudo-class. If not specified, then if the selector is a [scoped selector](https://drafts.csswg.org/selectors-4/#scoped-selector), the set of :scope elements default to the [scoping root](https://drafts.csswg.org/selectors-4/#scoping-root); otherwise, it defaults to the root elements.
    
    Note: Note that if the selector is scoped, the scoping root is automatically taken as the [:scope element](https://drafts.csswg.org/selectors-4/#scope-element), so it doesn’t have to be provided explicitly unless a different result is desired.
    
- Which [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) are allowed to show up in the match list. If not specified, this defaults to allowing all pseudo-elements.
    
     issue-eaeaf8e2)Only the [::before](https://drafts.csswg.org/css-pseudo-4/#selectordef-before) and [::after](https://drafts.csswg.org/css-pseudo-4/#selectordef-after) pseudo-elements are really handled in any way remotely like this.
    

This algorithm returns a (possibly empty) list of elements.

1. Start with a list of candidate elements, which are the the root elements and all of their descendant elements, sorted in [shadow-including tree order](https://dom.spec.whatwg.org/#concept-shadow-including-tree-order), unless otherwise specified.
2. If an optional scoping root was provided, then remove from the candidate elements any elements that are not [descendants](https://dom.spec.whatwg.org/#concept-tree-descendant) of the [scoping root](https://drafts.csswg.org/selectors-4/#scoping-root).
3. Initialize the selector match list to empty.
4. For each element in the set of candidate elements:
    1. If the result of [match a selector against an element](https://drafts.csswg.org/selectors-4/#match-a-selector-against-an-element) for element and selector is success, add element to the selector match list.
    2. For each possible pseudo-element associated with element that is one of the pseudo-elements allowed to show up in the match list, if the result of [match a selector against a pseudo-element](https://drafts.csswg.org/selectors-4/#match-a-selector-against-a-pseudo-element) for the pseudo-element and selector is success, add the pseudo-element to the selector match list.
        
         issue-b7f52036)The relative position of pseudo-elements in selector match list is undefined. There’s not yet a context that exposes this information, but we need to decide on something eventually, before something _is_ exposed.
        

## Appendix A: Guidance on Mapping Source Documents & Data to an Element Tree dom-mapping)

_This section is informative._

The element tree structure described by the DOM is powerful and useful, but generic enough to model pretty much any language that describes tree-based data (or even graph-based, with a suitable interpretation).

Some languages, like HTML, already have well-defined procedures for producing a DOM object from a resource. If a given language does not, such a procedure must be defined in order for Selectors to apply to documents in that language.

At minimum, the document language must define what maps to the DOM concept of an "element".

The primary one-to-many relationship between nodes—parent/child in tree-based structures, element/neighbors in graph-based structures—should be reflected as the child nodes of an element.

Other features of the element should be mapped to something that serves a similar purpose to the same feature in DOM:

type

If the elements in the document language have some notion of "type" as a basic distinguisher between different groups of elements, it should be reflected as the "type" feature.

If this "type" can be separated into a "basic" name and a "namespace" that groups names into higher-level groups, the latter should be reflected as the "namespace" feature. Otherwise, the element shouldn’t have a "namespace" feature, and the entire name should be reflected as the "type" feature.

id

If some aspect of the element functions as a unique identifier across the document, it should be mapped to the "id" feature.

Note: While HTML only allows an element to have a single ID, this should not be taken as a general restriction. The important quality of an ID is that each ID should be associated with a single element; a single element can validly have multiple IDs.

classes and attributes

Aspects of the element that are useful for identifying the element, but are not generally unique to elements within a document, should be mapped to the "class" or "attribute" features depending on if they’re something equivalent to a "label" (a string by itself) or a "property" (a name/value pair)

pseudo-classes and pseudo-elements

If any elements match any pseudo-classes or have any pseudo-elements, that must be explicitly defined.

 issue-772ec278)Some pseudo-classes are \*syntactical\*, like [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo) and [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo), and thus should always work. Need to indicate that somewhere. Probably the structural pseudos always work whenever the child list is ordered.

 example-37a1ab6b)For example, [JSONSelect](https://github.com/lloyd/JSONSelect) is a library that uses selectors to extract information from JSON documents.

- The "elements" of the JSON document are each array, object, boolean, string, number, or null. The array and object elements have their contents as children.
- Each element’s type is its JS type name: "array", "object", etc.
- Children of an object have their key as a class.
- Children of an array match the [:first-child](https://drafts.csswg.org/selectors-4/#first-child-pseudo), [:nth-child()](https://drafts.csswg.org/selectors-4/#nth-child-pseudo), etc pseudo-classes.
- The root object matches [:root](https://drafts.csswg.org/selectors-4/#root-pseudo).
- It additionally defines :val() and :contains() pseudo-classes, for matching boolean/number/string elements with a particular value or which contain a particular substring.

This structure is sufficient to allow powerful, compact querying of JSON documents with selectors.

## Appendix B: Obsolete but Required Parsing Quirks for Web Compat compat)

_This appendix is normative._

Due to legacy Web-compat constraints, User Agents expecting to parse Web documents must support the following features:

- All [pseudo-elements](https://drafts.csswg.org/selectors-4/#pseudo-element) whose names begin with the string “-webkit-” (matched [ASCII case-insensitively](https://infra.spec.whatwg.org/#ascii-case-insensitive)) and that are not functional notations must be treated as valid at parse time. (That is, ::-webkit-asdf is valid at parse time, but ::-webkit-jkl() is not.) If they’re not otherwise recognized and supported, they must be treated as matching nothing, and are unknown -webkit- pseudo-elements.
    
    [Unknown -webkit- pseudo-elements](https://drafts.csswg.org/selectors-4/#unknown--webkit--pseudo-elements) must be serialized in ASCII lowercase.
    
    What’s this quirk about?
    
    Selectors have long had a behavior where a single unknown/invalid selector invalidates the entire selector list (rather than just invalidating the one complex selector it finds itself in). This is generally considered a legacy mistake by the WG, but can’t be fixed at this point, as too many stylesheets depend on this behavior, intentionally or not.
    
    One aspect of this is that use of vendor-specific selectors invalidates the entire selector in other User Agents that don’t recognize them, and takes the entire style rule down with it. This has been used intentionally in the past—in the severely-not-recommended practice of hiding style rules from some browsers by making them invalid in every other browser—and unintentionally, with people styling an element and also applying those styles to a vendor-specific pseudo-element (such as the various `[input](https://html.spec.whatwg.org/multipage/input.html#the-input-element)`\-related pseudos some browsers expose), not realizing that this hides the entire rule from other browsers.
    
    In addition to this more general reasoning, WebKit-derived user agents, such as Safari or Chrome, have an additional quirk related to their vendor-prefixed pseudo-elements, where any ::-webkit-\-prefixed selectors are considered valid at parse time. (This is probably a leftover quirk of an early CSS feature, since dropped, that intentionally treated all possible pseudo-elements as valid at parse time, in anticipation of a feature letting authors define their own pseudo-elements.)
    
    Similar to other legacy quirks, such as those documented in [\[QUIRKS\]](https://drafts.csswg.org/selectors-4/#biblio-quirks), this particular vendor-specific oddity has become common enough that other user agents are seeing sites breaking due to them depending on it, accidentally or not. As such, since the quirk is in practical terms _required_ to render the modern web correctly, specifying it and requiring it for all user agents ensures that today’s web pages are more likely to be correctly rendered in user agents both current and future.
    
    As usual with quirks, however, webpages intentionally relying on this will be met with shaming and derision from members of the CSSWG, and all right-thinking web developers.
    

## 19\. Changes changes)

### 19.1. Changes since the 21 November 2018 Working Draft changes-2018-11)

Significant changes since the [21 November 2018 Working Draft](https://www.w3.org/TR/2018/WD-selectors-4-20181121/):

- Removed the Selector profiles, marked [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo) as optional and at-risk instead. ([Issue 3925](https://github.com/w3c/csswg-drafts/issues/3925))

### 19.2. Changes since the 2 February 2018 Working Draft changes-2018-02)

Significant changes since the [2 February 2018 Working Draft](https://www.w3.org/TR/2018/WD-selectors-4-20180202/):

- Named the zero-specificity selector to [:where()](https://drafts.csswg.org/selectors-4/#where-pseudo). ([Issue 2143](https://github.com/w3c/csswg-drafts/issues/2143))
- Renamed [:matches()](https://drafts.csswg.org/selectors-4/#selectordef-matches) to [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo). ([Issue 3258](https://github.com/w3c/csswg-drafts/issues/3258))
- Redefined [:empty](https://drafts.csswg.org/selectors-4/#empty-pseudo) to ignore white-space–only nodes. ([Issue 1967](https://github.com/w3c/csswg-drafts/issues/1967))
- Redefined [:blank](https://drafts.csswg.org/selectors-4/#blank-pseudo) to represent empty user input, rather than empty elements. ([Issue 1283](https://github.com/w3c/csswg-drafts/issues/1283))
- Changed the specificity of [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo), [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo), and [:nth-child()](https://drafts.csswg.org/selectors-4/#nth-child-pseudo) to not depend on which selector argument matched. ([Issue 1027](https://github.com/w3c/csswg-drafts/issues/1027))
- Dropped the :drop() pseudo-classes since HTML dropped the related feature. ([Issue 2257](https://github.com/w3c/csswg-drafts/issues/2257))
- Added the case-sensitive flag `s` to the attribute selector. ([Issue 2101](https://github.com/w3c/csswg-drafts/issues/2101))
- Added further guidance on [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo).
- Added [Appendix B: Obsolete but Required Parsing Quirks for Web Compat](https://drafts.csswg.org/selectors-4/#compat) defining ::-webkit- pseudo-element parsing quirk. ([Issue 3051](https://github.com/w3c/csswg-drafts/issues/3051))
- Rewrote grammar rules about where white space is allowed for clarity. (See [§ 17 Grammar](https://drafts.csswg.org/selectors-4/#grammar).)

### 19.3. Changes since the 2 May 2013 Working Draft changes-2013)

Significant changes since the [2 May 2013 Working Draft](https://www.w3.org/TR/2013/WD-selectors4-20130502/) include:

- Added the [:target-within](https://drafts.csswg.org/selectors-4/#target-within-pseudo), [:focus-within](https://drafts.csswg.org/selectors-4/#focus-within-pseudo), [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo), [:playing](https://drafts.csswg.org/selectors-4/#selectordef-playing), and [:paused](https://drafts.csswg.org/selectors-4/#selectordef-paused) pseudo-classes.
- Added a zero-specificity [:matches()](https://drafts.csswg.org/selectors-4/#selectordef-matches)\-type pseudo-class, with name TBD.
- Replaced subject indicator (!) feature with [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo).
- Replaced the :nth-match() and :nth-last-match() selectors with :nth-child(… of selector) and :nth-last-child(… of selector).
- Changed the :active-drop-target, :valid-drop-target, :invalid-drop-target with :drop().
- Sketched out an empty-or-whitespace-only selector for discussion (See [open issue](https://github.com/w3c/csswg-drafts/issues/1967).)
- Renamed :user-error to [:user-invalid](https://drafts.csswg.org/selectors-4/#user-invalid-pseudo). (See [Discussion](https://www.w3.org/mid/CADhPm3v+WfeGQfBwwx8QBuiOjn2k38V_DcKW17Cm81VgZb1nbQ@mail.gmail.com))
- Renamed :nth-column()/:nth-last-column() to [:nth-col()](https://drafts.csswg.org/selectors-4/#nth-col-pseudo)/[:nth-last-col()](https://drafts.csswg.org/selectors-4/#nth-last-col-pseudo) to avoid naming confusion with a potential ::column pseudo-class.
- Changed the non-functional form of the :local-link pseudo-class to account for fragment URLs.
- Removed the functional form of the `:local-link()` pseudo-class and reference combinator for lack of interest.
- Rewrote selectors grammar using the CSS Value Definition Syntax.
- Split out [relative selectors](https://drafts.csswg.org/selectors-4/#relative-selector) from [scoped selectors](https://drafts.csswg.org/selectors-4/#scoped-selector), as these are different concepts that can be independently invoked.
- Moved definition of [<An+B>](https://drafts.csswg.org/css-syntax-3/#anb-production) microsyntax to CSS Syntax.
    
     issue-fb60ae39)Semantic definition should probably move back here.
    
- Added new sections:
    - [§ 3.2 Data Model](https://drafts.csswg.org/selectors-4/#data-model)
        
         issue-4ca3978c)Need to define tree for XML.
        
    - [§ 18 API Hooks](https://drafts.csswg.org/selectors-4/#api-hooks)
        - Note that earlier versions of this section defined a section on evaluating a selector evaluating-selectors), but that section is no longer present. Specifications referencing that section should instead reference the algorithm to [match a selector against a tree](https://drafts.csswg.org/selectors-4/#match-a-selector-against-a-tree).
- Removed restriction on combinators within [:matches()](https://drafts.csswg.org/selectors-4/#selectordef-matches) and [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo); see [discussion](https://lists.w3.org/Archives/Public/www-style/2014Jan/0607.html).
- Defined [specificity](https://drafts.csswg.org/selectors-4/#specificity) of a [selector list](https://drafts.csswg.org/selectors-4/#selector-list). (Why?)
- Required quotes around [:lang()](https://drafts.csswg.org/selectors-4/#lang-pseudo) values involving an asterisk; only language codes which happen to be CSS identifiers can be used unquoted.

Note: The 1 February 2018 draft included an inadvertent commit of unfinished work; 2 February 2018 has reverted this commit (and fixed some links because why not).

### 19.4. Changes since the 23 August 2012 Working Draft changes-2012)

Significant changes since the [23 August 2012 Working Draft](https://www.w3.org/TR/2012/WD-selectors4-20120823/) include:

- Added [:placeholder-shown](https://drafts.csswg.org/selectors-4/#placeholder-shown-pseudo) pseudo-classes.
- Released some restrictions on [:matches()](https://drafts.csswg.org/selectors-4/#selectordef-matches) and [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo).
- Defined fast and complete Selectors profiles (now called “live” and “snapshot”).
- Improved definition of [specificity](https://drafts.csswg.org/selectors-4/#specificity) to better handle [:matches()](https://drafts.csswg.org/selectors-4/#selectordef-matches).
- Updated grammar.
- Cleaned up definition of [<An+B>](https://drafts.csswg.org/css-syntax-3/#anb-production) notation.
- Added definition of [scope-relative](https://drafts.csswg.org/selectors-4/#relative-selector) selectors, changed _scope-constrained_ to scope-filtered for less confusion with scope-contained.
- The :local-link() pseudo-class now ignores trailing slashes.

### 19.5. Changes since the 29 September 2011 Working Draft changes-2011)

Significant changes since the [29 September 2011 Working Draft](https://www.w3.org/TR/2011/WD-selectors4-20110929/) include:

- Added language variant handling per RFC 4647.
- Added scoped selectors.
- Added :user-error (now called [:user-invalid](https://drafts.csswg.org/selectors-4/#user-invalid-pseudo)).
- Added :valid-drop-target.
- Changed [column combinator](https://drafts.csswg.org/selectors-4/#column-combinator) from double slash to double pipe.

### 19.6. Changes Since Level 3 changes-level-3)

Additions since [Level 3](https://www.w3.org/TR/selectors-3/):

- Extended [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo) to accept a selector list.
- Added [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo) and [:where()](https://drafts.csswg.org/selectors-4/#where-pseudo) and [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo).
- Added [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo).
- Added [:any-link](https://drafts.csswg.org/selectors-4/#any-link-pseudo) and [:local-link](https://drafts.csswg.org/selectors-4/#local-link-pseudo).
- Added [time-dimensional pseudo-classes](https://drafts.csswg.org/selectors-4/#time-pseudos).
- Added [:target-within](https://drafts.csswg.org/selectors-4/#target-within-pseudo), [:focus-within](https://drafts.csswg.org/selectors-4/#focus-within-pseudo), and [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo).
- Added [:dir()](https://drafts.csswg.org/selectors-4/#dir-pseudo).
- Expanded [:lang()](https://drafts.csswg.org/selectors-4/#lang-pseudo) to accept wildcard matching and lists of language codes.
- Expanded :nth-child() to accept a selector list.
- Merged in input selectors from [CSS Basic User Interface Module Level 3](https://www.w3.org/TR/css-ui-3/) and added back [:indeterminate](https://drafts.csswg.org/selectors-4/#indetermine-pseudo).
- Added [:blank](https://drafts.csswg.org/selectors-4/#blank-pseudo) and [:user-invalid](https://drafts.csswg.org/selectors-4/#user-invalid-pseudo).
- Added [grid-structural (column) selectors](https://drafts.csswg.org/selectors-4/#table-pseudos).
- Added case-insensitive / case-sensitive attribute-value matching flags.

## 20\. Acknowledgements acknowledgements)

The CSS working group would like to thank everyone who contributed to the [previous Selectors](https://www.w3.org/TR/css3-selectors) specifications over the years, as those specifications formed the basis for this one. In particular, the working group would like to extend special thanks to the following for their specific contributions to Selectors Level 4: L. David Baron, Andrew Fedoniouk, Daniel Glazman, Ian Hickson, Grey Hodge, Lachlan Hunt, Anne van Kesteren, Jason Cranford Teague, Lea Verou

## 21\. Privacy and Security Considerations priv-sec)

This specification introduces no new privacy or security considerations, as selectors do not provide any ability not already possible by walking the DOM manually.

## Conformance conformance)

### Document conventions document-conventions)

Conformance requirements are expressed with a combination of descriptive assertions and RFC 2119 terminology. The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in the normative parts of this document are to be interpreted as described in RFC 2119. However, for readability, these words do not appear in all uppercase letters in this specification.

All of the text of this specification is normative except sections explicitly marked as non-normative, examples, and notes. [\[RFC2119\]](https://drafts.csswg.org/selectors-4/#biblio-rfc2119)

Examples in this specification are introduced with the words “for example” or are set apart from the normative text with `class="example"`, like this:

 example-ae2b6bc0)

This is an example of an informative example.

Informative notes begin with the word “Note” and are set apart from the normative text with `class="note"`, like this:

Note, this is an informative note.

Advisements are normative sections styled to evoke special attention and are set apart from other normative text with `<strong class="advisement">`, like this: **UAs MUST provide an accessible alternative.**

### Conformance classes conform-classes)

Conformance to this specification is defined for three conformance classes:

style sheet

A [CSS style sheet](http://www.w3.org/TR/CSS2/conform.html#style-sheet).

renderer

A [UA](http://www.w3.org/TR/CSS2/conform.html#user-agent) that interprets the semantics of a style sheet and renders documents that use them.

authoring tool

A [UA](http://www.w3.org/TR/CSS2/conform.html#user-agent) that writes a style sheet.

A style sheet is conformant to this specification if all of its statements that use syntax defined in this module are valid according to the generic CSS grammar and the individual grammars of each feature defined in this module.

A renderer is conformant to this specification if, in addition to interpreting the style sheet as defined by the appropriate specifications, it supports all the features defined by this specification by parsing them correctly and rendering the document accordingly. However, the inability of a UA to correctly render a document due to limitations of the device does not make the UA non-conformant. (For example, a UA is not required to render color on a monochrome monitor.)

An authoring tool is conformant to this specification if it writes style sheets that are syntactically correct according to the generic CSS grammar and the individual grammars of each feature in this module, and meet all other conformance requirements of style sheets as described in this module.

### Requirements for Responsible Implementation of CSS conform-responsible)

The following sections define several conformance requirements for implementing CSS responsibly, in a way that promotes interoperability in the present and future.

#### Partial Implementations conform-partial)

So that authors can exploit the forward-compatible parsing rules to assign fallback values, **CSS renderers _must_ treat as invalid (and [ignore as appropriate](http://www.w3.org/TR/CSS2/conform.html#ignore)) any at-rules, properties, property values, keywords, and other syntactic constructs for which they have no usable level of support**. In particular, user agents _must not_ selectively ignore unsupported property values and honor supported values in a single multi-value property declaration: if any value is considered invalid (as unsupported values must be), CSS requires that the entire declaration be ignored.

#### Implementations of Unstable and Proprietary Features conform-future-proofing)

To avoid clashes with future stable CSS features, the CSSWG recommends [following best practices](http://www.w3.org/TR/CSS/#future-proofing) for the implementation of [unstable](http://www.w3.org/TR/CSS/#unstable) features and [proprietary extensions](http://www.w3.org/TR/CSS/#proprietary-extension) to CSS.

#### Implementations of CR-level Features conform-testing)

Once a specification reaches the Candidate Recommendation stage, implementers should release an [unprefixed](http://www.w3.org/TR/CSS/#vendor-prefix) implementation of any CR-level feature they can demonstrate to be correctly implemented according to spec, and should avoid exposing a prefixed variant of that feature.

To establish and maintain the interoperability of CSS across implementations, the CSS Working Group requests that non-experimental CSS renderers submit an implementation report (and, if necessary, the testcases used for that implementation report) to the W3C before releasing an unprefixed implementation of any CSS features. Testcases submitted to W3C are subject to review and correction by the CSS Working Group.

Further information on submitting testcases and implementation reports can be found from on the CSS Working Group’s website at [http://www.w3.org/Style/CSS/Test/](http://www.w3.org/Style/CSS/Test/). Questions should be directed to the [public-css-testsuite@w3.org](http://lists.w3.org/Archives/Public/public-css-testsuite) mailing list.

## Index index)

### Terms defined by this specification index-defined-here)

- [+](https://drafts.csswg.org/selectors-4/#selectordef-adjacent), in §14.3
- [\>](https://drafts.csswg.org/selectors-4/#selectordef-child), in §14.2
- [||](https://drafts.csswg.org/selectors-4/#selectordef-column), in §15.1
- [~](https://drafts.csswg.org/selectors-4/#selectordef-sibling), in §14.4
- [absolutize a relative selector](https://drafts.csswg.org/selectors-4/#absolutize), in §3.4.1
- [absolutize a relative selector list](https://drafts.csswg.org/selectors-4/#absolutize-list), in §3.4.1
- [:active](https://drafts.csswg.org/selectors-4/#active-pseudo), in §9.2
- [:any-link](https://drafts.csswg.org/selectors-4/#any-link-pseudo), in §8.1
- [<attribute-selector>](https://drafts.csswg.org/selectors-4/#typedef-attribute-selector), in §17
- [attribute selector](https://drafts.csswg.org/selectors-4/#attribute-selector), in §6
- [<attr-matcher>](https://drafts.csswg.org/selectors-4/#typedef-attr-matcher), in §17
- [<attr-modifier>](https://drafts.csswg.org/selectors-4/#typedef-attr-modifier), in §17
- [:blank](https://drafts.csswg.org/selectors-4/#blank-pseudo), in §12.3.1
- [:checked](https://drafts.csswg.org/selectors-4/#checked-pseudo), in §12.2.1
- [child combinator](https://drafts.csswg.org/selectors-4/#child-combinator), in §14.2
- [<class-selector>](https://drafts.csswg.org/selectors-4/#typedef-class-selector), in §17
- [class selector](https://drafts.csswg.org/selectors-4/#class-selector), in §6.6
- [column combinator](https://drafts.csswg.org/selectors-4/#column-combinator), in §15.1
- [<combinator>](https://drafts.csswg.org/selectors-4/#typedef-combinator), in §17
- [combinator](https://drafts.csswg.org/selectors-4/#selector-combinator), in §3.1
- [<complex-selector>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector), in §17
- [complex selector](https://drafts.csswg.org/selectors-4/#complex), in §3.1
- [<complex-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-complex-selector-list), in §17
- [<compound-selector>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector), in §17
- [compound selector](https://drafts.csswg.org/selectors-4/#compound), in §3.1
- [<compound-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-compound-selector-list), in §17
- [:current](https://drafts.csswg.org/selectors-4/#current-pseudo), in §10.1
- [:current()](https://drafts.csswg.org/selectors-4/#selectordef-current), in §10.1
- [declared](https://drafts.csswg.org/selectors-4/#nsdecl), in §3.8
- [:default](https://drafts.csswg.org/selectors-4/#default-pseudo), in §12.1.4
- [:defined](https://drafts.csswg.org/selectors-4/#defined-pseudo), in §5.4
- [descendant combinator](https://drafts.csswg.org/selectors-4/#descendant-combinator), in §14.1
- [:dir()](https://drafts.csswg.org/selectors-4/#dir-pseudo), in §7.1
- [:disabled](https://drafts.csswg.org/selectors-4/#disabled-pseudo), in §12.1.1
- [document language](https://drafts.csswg.org/selectors-4/#document-language), in §3.2
- [:empty](https://drafts.csswg.org/selectors-4/#empty-pseudo), in §13.2
- [:enabled](https://drafts.csswg.org/selectors-4/#enabled-pseudo), in §12.1.1
- [evaluating a selector](https://drafts.csswg.org/selectors-4/#evaluating-selectors), in §19.3
- [featureless](https://drafts.csswg.org/selectors-4/#featureless), in §3.2
- [:first-child](https://drafts.csswg.org/selectors-4/#first-child-pseudo), in §13.3.3
- [:first-of-type](https://drafts.csswg.org/selectors-4/#first-of-type-pseudo), in §13.4.3
- [:focus](https://drafts.csswg.org/selectors-4/#focus-pseudo), in §9.3
- [:focus-visible](https://drafts.csswg.org/selectors-4/#focus-visible-pseudo), in §9.4
- [:focus-within](https://drafts.csswg.org/selectors-4/#focus-within-pseudo), in §9.5
- [<forgiving-relative-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-relative-selector-list), in §17.1
- [<forgiving-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-forgiving-selector-list), in §17.1
- [functional pseudo-class](https://drafts.csswg.org/selectors-4/#functional-pseudo-class), in §3.5
- [:future](https://drafts.csswg.org/selectors-4/#future-pseudo), in §10.3
- [:has()](https://drafts.csswg.org/selectors-4/#has-pseudo), in §4.5
- [host language](https://drafts.csswg.org/selectors-4/#host-language), in §3.2
- [:hover](https://drafts.csswg.org/selectors-4/#hover-pseudo), in §9.1
- [<id-selector>](https://drafts.csswg.org/selectors-4/#typedef-id-selector), in §17
- [ID selector](https://drafts.csswg.org/selectors-4/#id-selector), in §6.7
- [:indeterminate](https://drafts.csswg.org/selectors-4/#indetermine-pseudo), in §12.2.2
- [:in-range](https://drafts.csswg.org/selectors-4/#in-range-pseudo), in §12.3.3
- [:invalid](https://drafts.csswg.org/selectors-4/#invalid-pseudo), in §12.3.2
- [invalid](https://drafts.csswg.org/selectors-4/#invalid-selector), in §3.9
- [invalid selector](https://drafts.csswg.org/selectors-4/#invalid-selector), in §3.9
- [:is()](https://drafts.csswg.org/selectors-4/#matches-pseudo), in §4.2
- [:lang()](https://drafts.csswg.org/selectors-4/#lang-pseudo), in §7.2
- [language range](https://drafts.csswg.org/selectors-4/#language-range), in §7.2
- [:last-child](https://drafts.csswg.org/selectors-4/#last-child-pseudo), in §13.3.4
- [:last-of-type](https://drafts.csswg.org/selectors-4/#last-of-type-pseudo), in §13.4.4
- [:link](https://drafts.csswg.org/selectors-4/#link-pseudo), in §8.2
- [list of complex selectors](https://drafts.csswg.org/selectors-4/#list-of-simple-selectors), in §3.1
- [list of compound selectors](https://drafts.csswg.org/selectors-4/#list-of-simple-selectors), in §3.1
- [list of selectors](https://drafts.csswg.org/selectors-4/#selector-list), in §3.1
- [list of simple selectors](https://drafts.csswg.org/selectors-4/#list-of-simple-selectors), in §3.1
- [:local-link](https://drafts.csswg.org/selectors-4/#local-link-pseudo), in §8.3
- [match](https://drafts.csswg.org/selectors-4/#match), in §3.1
- [match a complex selector against an element](https://drafts.csswg.org/selectors-4/#match-a-complex-selector-against-an-element), in §18.3
- [match a selector against an element](https://drafts.csswg.org/selectors-4/#match-a-selector-against-an-element), in §18.3
- [match a selector against a pseudo-element](https://drafts.csswg.org/selectors-4/#match-a-selector-against-a-pseudo-element), in §18.4
- [match a selector against a tree](https://drafts.csswg.org/selectors-4/#match-a-selector-against-a-tree), in §18.5
- [:matches()](https://drafts.csswg.org/selectors-4/#selectordef-matches), in §4.2
- [next-sibling combinator](https://drafts.csswg.org/selectors-4/#next-sibling-combinator), in §14.3
- [:not()](https://drafts.csswg.org/selectors-4/#negation-pseudo), in §4.3
- [<ns-prefix>](https://drafts.csswg.org/selectors-4/#typedef-ns-prefix), in §17
- [:nth-child()](https://drafts.csswg.org/selectors-4/#nth-child-pseudo), in §13.3.1
- [:nth-col()](https://drafts.csswg.org/selectors-4/#nth-col-pseudo), in §15.2
- [:nth-last-child()](https://drafts.csswg.org/selectors-4/#nth-last-child-pseudo), in §13.3.2
- [:nth-last-col()](https://drafts.csswg.org/selectors-4/#nth-last-col-pseudo), in §15.3
- [:nth-last-of-type()](https://drafts.csswg.org/selectors-4/#nth-last-of-type-pseudo), in §13.4.2
- [:nth-of-type()](https://drafts.csswg.org/selectors-4/#nth-of-type-pseudo), in §13.4.1
- [:only-child](https://drafts.csswg.org/selectors-4/#only-child-pseudo), in §13.3.5
- [:only-of-type](https://drafts.csswg.org/selectors-4/#only-of-type-pseudo), in §13.4.5
- [:optional](https://drafts.csswg.org/selectors-4/#optional-pseudo), in §12.3.4
- [originating element](https://drafts.csswg.org/selectors-4/#originating-element), in §3.6.2
- [:out-of-range](https://drafts.csswg.org/selectors-4/#out-of-range-pseudo), in §12.3.3
- [parse a relative selector](https://drafts.csswg.org/selectors-4/#parse-a-relative-selector), in §18.2
- [parse as a forgiving selector list](https://drafts.csswg.org/selectors-4/#parse-as-a-forgiving-selector-list), in §17.1
- [parse a selector](https://drafts.csswg.org/selectors-4/#parse-a-selector), in §18.1
- [parsed as a forgiving selector list](https://drafts.csswg.org/selectors-4/#parse-as-a-forgiving-selector-list), in §17.1
- [parsing as a forgiving selector list](https://drafts.csswg.org/selectors-4/#parse-as-a-forgiving-selector-list), in §17.1
- [:past](https://drafts.csswg.org/selectors-4/#past-pseudo), in §10.2
- [:paused](https://drafts.csswg.org/selectors-4/#selectordef-paused), in §11.1
- [:placeholder-shown](https://drafts.csswg.org/selectors-4/#placeholder-shown-pseudo), in §12.1.3
- [:playing](https://drafts.csswg.org/selectors-4/#selectordef-playing), in §11.1
- [pseudo-class](https://drafts.csswg.org/selectors-4/#pseudo-class), in §3.5
- [<pseudo-class-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-class-selector), in §17
- [pseudo-element](https://drafts.csswg.org/selectors-4/#pseudo-element), in §3.6
- [<pseudo-element-selector>](https://drafts.csswg.org/selectors-4/#typedef-pseudo-element-selector), in §17
- [:read-only](https://drafts.csswg.org/selectors-4/#read-only-pseudo), in §12.1.2
- [:read-write](https://drafts.csswg.org/selectors-4/#read-write-pseudo), in §12.1.2
- [relative](https://drafts.csswg.org/selectors-4/#relative-selector), in §3.4
- [<relative-selector>](https://drafts.csswg.org/selectors-4/#typedef-relative-selector), in §17
- [relative selector](https://drafts.csswg.org/selectors-4/#relative-selector), in §3.4
- [<relative-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-relative-selector-list), in §17
- [:required](https://drafts.csswg.org/selectors-4/#required-pseudo), in §12.3.4
- [:root](https://drafts.csswg.org/selectors-4/#root-pseudo), in §13.1
- [:scope](https://drafts.csswg.org/selectors-4/#scope-pseudo), in §8.6
- [scope](https://drafts.csswg.org/selectors-4/#scoped-selector), in §3.3
- [scoped selector](https://drafts.csswg.org/selectors-4/#scoped-selector), in §3.3
- [:scope element](https://drafts.csswg.org/selectors-4/#scope-element), in §8.6
- [scope-relative](https://drafts.csswg.org/selectors-4/#relative-selector), in §3.4
- [scoping element](https://drafts.csswg.org/selectors-4/#scoping-element), in §3.3
- [scoping root](https://drafts.csswg.org/selectors-4/#scoping-root), in §3.3
- [selector](https://drafts.csswg.org/selectors-4/#selector), in §3.1
- [<selector-list>](https://drafts.csswg.org/selectors-4/#typedef-selector-list), in §17
- [selector list](https://drafts.csswg.org/selectors-4/#selector-list), in §3.1
- [<simple-selector>](https://drafts.csswg.org/selectors-4/#typedef-simple-selector), in §17
- [simple selector](https://drafts.csswg.org/selectors-4/#simple), in §3.1
- [<simple-selector-list>](https://drafts.csswg.org/selectors-4/#typedef-simple-selector-list), in §17
- [specificity](https://drafts.csswg.org/selectors-4/#specificity), in §16
- [structural pseudo-classes](https://drafts.csswg.org/selectors-4/#structural-pseudo-classes), in §13
- [<subclass-selector>](https://drafts.csswg.org/selectors-4/#typedef-subclass-selector), in §17
- [subject](https://drafts.csswg.org/selectors-4/#selector-subject), in §3.1
- [subject of a selector](https://drafts.csswg.org/selectors-4/#selector-subject), in §3.1
- [subsequent-sibling combinator](https://drafts.csswg.org/selectors-4/#subsequent-sibling-combinator), in §14.4
- [:target](https://drafts.csswg.org/selectors-4/#target-pseudo), in §8.4
- [:target-within](https://drafts.csswg.org/selectors-4/#target-within-pseudo), in §8.5
- [<type-selector>](https://drafts.csswg.org/selectors-4/#typedef-type-selector), in §17
- [type selector](https://drafts.csswg.org/selectors-4/#type-selector), in §5.1
- [universal selector](https://drafts.csswg.org/selectors-4/#universal-selector), in §5.2
- [unknown -webkit- pseudo-elements](https://drafts.csswg.org/selectors-4/#unknown--webkit--pseudo-elements), in §Unnumbered section
- [user action pseudo-class](https://drafts.csswg.org/selectors-4/#user-action-pseudo-class), in §9
- [:user-invalid](https://drafts.csswg.org/selectors-4/#user-invalid-pseudo), in §12.3.5
- [:valid](https://drafts.csswg.org/selectors-4/#valid-pseudo), in §12.3.2
- [virtual scoping root](https://drafts.csswg.org/selectors-4/#virtual-scoping-root), in §3.3
- [:visited](https://drafts.csswg.org/selectors-4/#visited-pseudo), in §8.2
- [:where()](https://drafts.csswg.org/selectors-4/#where-pseudo), in §4.4
- [White space](https://drafts.csswg.org/selectors-4/#whitespace), in §3.7
- [<wq-name>](https://drafts.csswg.org/selectors-4/#typedef-wq-name), in §17

[https://drafts.csswg.org/css-display-3/#box-tree](https://drafts.csswg.org/css-display-3/#box-tree)**Referenced in:**

- [3.6.4. Internal Structure](https://drafts.csswg.org/selectors-4/#ref-for-box-tree) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-box-tree%E2%91%A0)

[https://drafts.csswg.org/css-display-3/#propdef-display](https://drafts.csswg.org/css-display-3/#propdef-display)**Referenced in:**

- [12.1.1. The :enabled and :disabled Pseudo-classes](https://drafts.csswg.org/selectors-4/#ref-for-propdef-display)

[https://drafts.csswg.org/css-pseudo-4/#selectordef-after](https://drafts.csswg.org/css-pseudo-4/#selectordef-after)**Referenced in:**

- [3.6. Pseudo-elements](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-after)
- [3.6.1. Syntax](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-after%E2%91%A0)
- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-after%E2%91%A1)
- [18.5. Match a Selector Against a Tree](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-after%E2%91%A2)

[https://drafts.csswg.org/css-pseudo-4/#selectordef-before](https://drafts.csswg.org/css-pseudo-4/#selectordef-before)**Referenced in:**

- [3.6. Pseudo-elements](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-before)
- [3.6.1. Syntax](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-before%E2%91%A0)
- [3.6.2. Binding to the Document Tree](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-before%E2%91%A1)
- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-before%E2%91%A2)
- [18.5. Match a Selector Against a Tree](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-before%E2%91%A3)

[https://drafts.csswg.org/css-pseudo-4/#selectordef-first-letter](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-letter)**Referenced in:**

- [3.6. Pseudo-elements](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-letter)
- [3.6.1. Syntax](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-letter%E2%91%A0)
- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-letter%E2%91%A1)

[https://drafts.csswg.org/css-pseudo-4/#selectordef-first-line](https://drafts.csswg.org/css-pseudo-4/#selectordef-first-line)**Referenced in:**

- [3.2. Data Model](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A0)
- [3.6. Pseudo-elements](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A1) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A2)
- [3.6.1. Syntax](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A3)
- [3.6.2. Binding to the Document Tree](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A4) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A5)
- [3.6.3. Pseudo-classing Pseudo-elements](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A6) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A7)
- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-first-line%E2%91%A8)

[https://drafts.csswg.org/css-pseudo-4/#tree-abiding](https://drafts.csswg.org/css-pseudo-4/#tree-abiding)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-tree-abiding)

[https://www.w3.org/TR/css-scoping-1/#selectordef-content](https://www.w3.org/TR/css-scoping-1/#selectordef-content)**Referenced in:**

- [3.6.4. Internal Structure](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-content)

[https://www.w3.org/TR/css-scoping-1/#selectordef-shadow](https://www.w3.org/TR/css-scoping-1/#selectordef-shadow)**Referenced in:**

- [3.6.4. Internal Structure](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-shadow)

[https://drafts.csswg.org/css-scoping-1/#selectordef-slotted](https://drafts.csswg.org/css-scoping-1/#selectordef-slotted)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-slotted)

[https://drafts.csswg.org/css-scoping-1/#selectordef-host](https://drafts.csswg.org/css-scoping-1/#selectordef-host)**Referenced in:**

- [3.2. Data Model](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-host)

[https://drafts.csswg.org/css-scoping-1/#selectordef-host-context](https://drafts.csswg.org/css-scoping-1/#selectordef-host-context)**Referenced in:**

- [3.2. Data Model](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-host-context)

[https://drafts.csswg.org/css-scoping-1/#flat-tree](https://drafts.csswg.org/css-scoping-1/#flat-tree)**Referenced in:**

- [8.5. The Target Container Pseudo-class: :target-within](https://drafts.csswg.org/selectors-4/#ref-for-flat-tree)
- [9.1. The Pointer Hover Pseudo-class: :hover](https://drafts.csswg.org/selectors-4/#ref-for-flat-tree%E2%91%A0)
- [9.2. The Activation Pseudo-class: :active](https://drafts.csswg.org/selectors-4/#ref-for-flat-tree%E2%91%A1)
- [9.5. The Focus Container Pseudo-class: :focus-within](https://drafts.csswg.org/selectors-4/#ref-for-flat-tree%E2%91%A2)

[https://drafts.csswg.org/css-speech-1/#valdef-pause-before-strong](https://drafts.csswg.org/css-speech-1/#valdef-pause-before-strong)**Referenced in:**

- [16\. Calculating a selector’s specificity](https://drafts.csswg.org/selectors-4/#ref-for-valdef-pause-before-strong)

[https://drafts.csswg.org/css-text-3/#content-language](https://drafts.csswg.org/css-text-3/#content-language)**Referenced in:**

- [7.2. The Language Pseudo-class: :lang()](https://drafts.csswg.org/selectors-4/#ref-for-content-language) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-content-language%E2%91%A0) [(3)](https://drafts.csswg.org/selectors-4/#ref-for-content-language%E2%91%A1) [(4)](https://drafts.csswg.org/selectors-4/#ref-for-content-language%E2%91%A2) [(5)](https://drafts.csswg.org/selectors-4/#ref-for-content-language%E2%91%A3) [(6)](https://drafts.csswg.org/selectors-4/#ref-for-content-language%E2%91%A4)

[https://drafts.csswg.org/css-text-3/#white-space](https://drafts.csswg.org/css-text-3/#white-space)**Referenced in:**

- [13.2. :empty pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-white-space)

[https://drafts.csswg.org/css-values-3/#string-value](https://drafts.csswg.org/css-values-3/#string-value)**Referenced in:**

- [7.2. The Language Pseudo-class: :lang()](https://drafts.csswg.org/selectors-4/#ref-for-string-value)

[https://drafts.csswg.org/css-values-4/#mult-req](https://drafts.csswg.org/css-values-4/#mult-req)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-mult-req)

[https://drafts.csswg.org/css-values-4/#mult-comma](https://drafts.csswg.org/css-values-4/#mult-comma)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-mult-comma) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-mult-comma%E2%91%A0) [(3)](https://drafts.csswg.org/selectors-4/#ref-for-mult-comma%E2%91%A1) [(4)](https://drafts.csswg.org/selectors-4/#ref-for-mult-comma%E2%91%A2)

[https://drafts.csswg.org/css-values-4/#mult-zero-plus](https://drafts.csswg.org/css-values-4/#mult-zero-plus)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-mult-zero-plus) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-mult-zero-plus%E2%91%A0) [(3)](https://drafts.csswg.org/selectors-4/#ref-for-mult-zero-plus%E2%91%A1) [(4)](https://drafts.csswg.org/selectors-4/#ref-for-mult-zero-plus%E2%91%A2)

[https://drafts.csswg.org/css-values-4/#typedef-ident](https://drafts.csswg.org/css-values-4/#typedef-ident)**Referenced in:**

- [7.2. The Language Pseudo-class: :lang()](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident)

[https://drafts.csswg.org/css-values-4/#mult-opt](https://drafts.csswg.org/css-values-4/#mult-opt)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-mult-opt) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-mult-opt%E2%91%A0) [(3)](https://drafts.csswg.org/selectors-4/#ref-for-mult-opt%E2%91%A1) [(4)](https://drafts.csswg.org/selectors-4/#ref-for-mult-opt%E2%91%A2) [(5)](https://drafts.csswg.org/selectors-4/#ref-for-mult-opt%E2%91%A3) [(6)](https://drafts.csswg.org/selectors-4/#ref-for-mult-opt%E2%91%A4) [(7)](https://drafts.csswg.org/selectors-4/#ref-for-mult-opt%E2%91%A5) [(8)](https://drafts.csswg.org/selectors-4/#ref-for-mult-opt%E2%91%A6)

[https://drafts.csswg.org/css-values-4/#comb-one](https://drafts.csswg.org/css-values-4/#comb-one)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-comb-one) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A0) [(3)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A1) [(4)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A2) [(5)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A3) [(6)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A4) [(7)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A5) [(8)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A6) [(9)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A7) [(10)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A8) [(11)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A0%E2%93%AA) [(12)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A0%E2%91%A0) [(13)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A0%E2%91%A1) [(14)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A0%E2%91%A2) [(15)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A0%E2%91%A3) [(16)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A0%E2%91%A4) [(17)](https://drafts.csswg.org/selectors-4/#ref-for-comb-one%E2%91%A0%E2%91%A5)

[https://drafts.csswg.org/css-writing-modes-3/#propdef-direction](https://drafts.csswg.org/css-writing-modes-3/#propdef-direction)**Referenced in:**

- [7.1. The Directionality Pseudo-class: :dir()](https://drafts.csswg.org/selectors-4/#ref-for-propdef-direction)

[https://drafts.csswg.org/css2/#selectordef-lang](https://drafts.csswg.org/css2/#selectordef-lang)**Referenced in:**

- [6.1. Attribute presence and value selectors](https://drafts.csswg.org/selectors-4/#ref-for-selectordef-lang)

[https://drafts.csswg.org/css2/#propdef-visibility](https://drafts.csswg.org/css2/#propdef-visibility)**Referenced in:**

- [12.1.1. The :enabled and :disabled Pseudo-classes](https://drafts.csswg.org/selectors-4/#ref-for-propdef-visibility)

[https://drafts.csswg.org/css-namespaces-3/#css-qualified-name](https://drafts.csswg.org/css-namespaces-3/#css-qualified-name)**Referenced in:**

- [5.1. Type (tag name) selector](https://drafts.csswg.org/selectors-4/#ref-for-css-qualified-name)
- [5.2. Universal selector](https://drafts.csswg.org/selectors-4/#ref-for-css-qualified-name%E2%91%A0)

[https://drafts.csswg.org/css-namespaces-3/#default-namespace](https://drafts.csswg.org/css-namespaces-3/#default-namespace)**Referenced in:**

- [5.3. Namespaces in Elemental Selectors](https://drafts.csswg.org/selectors-4/#ref-for-default-namespace)

[https://drafts.csswg.org/css-syntax-3/#anb-production](https://drafts.csswg.org/css-syntax-3/#anb-production)**Referenced in:**

- [19.3. Changes since the 2 May 2013 Working Draft](https://drafts.csswg.org/selectors-4/#ref-for-anb-production)
- [19.4. Changes since the 23 August 2012 Working Draft](https://drafts.csswg.org/selectors-4/#ref-for-anb-production%E2%91%A0)

[https://drafts.csswg.org/css-syntax-3/#typedef-any-value](https://drafts.csswg.org/css-syntax-3/#typedef-any-value)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-typedef-any-value)
- [17.1. <forgiving-selector-list> and <forgiving-relative-selector-list>](https://drafts.csswg.org/selectors-4/#ref-for-typedef-any-value%E2%91%A0)

[https://drafts.csswg.org/css-syntax-3/#typedef-function-token](https://drafts.csswg.org/css-syntax-3/#typedef-function-token)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-typedef-function-token) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-typedef-function-token%E2%91%A0)

[https://drafts.csswg.org/css-syntax-3/#typedef-hash-token](https://drafts.csswg.org/css-syntax-3/#typedef-hash-token)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-typedef-hash-token) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-typedef-hash-token%E2%91%A0)

[https://drafts.csswg.org/css-syntax-3/#typedef-ident-token](https://drafts.csswg.org/css-syntax-3/#typedef-ident-token)**Referenced in:**

- [6.1. Attribute presence and value selectors](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident-token)
- [6.2. Substring matching attribute selectors](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident-token%E2%91%A0)
- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident-token%E2%91%A1) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident-token%E2%91%A2) [(3)](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident-token%E2%91%A3) [(4)](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident-token%E2%91%A4) [(5)](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident-token%E2%91%A5) [(6)](https://drafts.csswg.org/selectors-4/#ref-for-typedef-ident-token%E2%91%A6)

[https://drafts.csswg.org/css-syntax-3/#typedef-string-token](https://drafts.csswg.org/css-syntax-3/#typedef-string-token)**Referenced in:**

- [6.1. Attribute presence and value selectors](https://drafts.csswg.org/selectors-4/#ref-for-typedef-string-token)
- [6.2. Substring matching attribute selectors](https://drafts.csswg.org/selectors-4/#ref-for-typedef-string-token%E2%91%A0)
- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-typedef-string-token%E2%91%A1)

[https://drafts.csswg.org/css-syntax-3/#identifier](https://drafts.csswg.org/css-syntax-3/#identifier)**Referenced in:**

- [3.5. Pseudo-classes](https://drafts.csswg.org/selectors-4/#ref-for-identifier)
- [3.6.1. Syntax](https://drafts.csswg.org/selectors-4/#ref-for-identifier%E2%91%A0)
- [5.1. Type (tag name) selector](https://drafts.csswg.org/selectors-4/#ref-for-identifier%E2%91%A1)
- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-identifier%E2%91%A2)

[https://drafts.csswg.org/css-syntax-3/#css-parse-something-according-to-a-css-grammar](https://drafts.csswg.org/css-syntax-3/#css-parse-something-according-to-a-css-grammar)**Referenced in:**

- [17\. Grammar](https://drafts.csswg.org/selectors-4/#ref-for-css-parse-something-according-to-a-css-grammar)
- [18.1. Parse A Selector](https://drafts.csswg.org/selectors-4/#ref-for-css-parse-something-according-to-a-css-grammar%E2%91%A0)
- [18.2. Parse A Relative Selector](https://drafts.csswg.org/selectors-4/#ref-for-css-parse-something-according-to-a-css-grammar%E2%91%A1)

[https://drafts.csswg.org/css-syntax-3/#css-parse-a-comma-separated-list-according-to-a-css-grammar](https://drafts.csswg.org/css-syntax-3/#css-parse-a-comma-separated-list-according-to-a-css-grammar)**Referenced in:**

- [17.1. <forgiving-selector-list> and <forgiving-relative-selector-list>](https://drafts.csswg.org/selectors-4/#ref-for-css-parse-a-comma-separated-list-according-to-a-css-grammar)

[https://dom.spec.whatwg.org/#document](https://dom.spec.whatwg.org/#document)**Referenced in:**

- [13.1. :root pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-document)

[https://dom.spec.whatwg.org/#documentfragment](https://dom.spec.whatwg.org/#documentfragment)**Referenced in:**

- [3.3. Scoped Selectors](https://drafts.csswg.org/selectors-4/#ref-for-documentfragment)

[https://dom.spec.whatwg.org/#concept-tree-descendant](https://dom.spec.whatwg.org/#concept-tree-descendant)**Referenced in:**

- [18.5. Match a Selector Against a Tree](https://drafts.csswg.org/selectors-4/#ref-for-concept-tree-descendant)

[https://dom.spec.whatwg.org/#concept-tree-inclusive-sibling](https://dom.spec.whatwg.org/#concept-tree-inclusive-sibling)**Referenced in:**

- [13.3. Child-indexed Pseudo-classes](https://drafts.csswg.org/selectors-4/#ref-for-concept-tree-inclusive-sibling)
- [13.3.1. :nth-child() pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-concept-tree-inclusive-sibling%E2%91%A0)
- [13.3.2. :nth-last-child() pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-concept-tree-inclusive-sibling%E2%91%A1)
- [13.3.3. :first-child pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-concept-tree-inclusive-sibling%E2%91%A2)
- [13.3.4. :last-child pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-concept-tree-inclusive-sibling%E2%91%A3)

[https://dom.spec.whatwg.org/#concept-document-quirks](https://dom.spec.whatwg.org/#concept-document-quirks)**Referenced in:**

- [6.6. Class selectors](https://drafts.csswg.org/selectors-4/#ref-for-concept-document-quirks)
- [6.7. ID selectors](https://drafts.csswg.org/selectors-4/#ref-for-concept-document-quirks%E2%91%A0)

[https://dom.spec.whatwg.org/#concept-tree-root](https://dom.spec.whatwg.org/#concept-tree-root)**Referenced in:**

- [18.5. Match a Selector Against a Tree](https://drafts.csswg.org/selectors-4/#ref-for-concept-tree-root)

[https://dom.spec.whatwg.org/#element-shadow-host](https://dom.spec.whatwg.org/#element-shadow-host)**Referenced in:**

- [3.2. Data Model](https://drafts.csswg.org/selectors-4/#ref-for-element-shadow-host)

[https://dom.spec.whatwg.org/#concept-shadow-tree](https://dom.spec.whatwg.org/#concept-shadow-tree)**Referenced in:**

- [3.2. Data Model](https://drafts.csswg.org/selectors-4/#ref-for-concept-shadow-tree)

[https://dom.spec.whatwg.org/#concept-shadow-including-tree-order](https://dom.spec.whatwg.org/#concept-shadow-including-tree-order)**Referenced in:**

- [18.5. Match a Selector Against a Tree](https://drafts.csswg.org/selectors-4/#ref-for-concept-shadow-including-tree-order)

[https://dom.spec.whatwg.org/#concept-tree](https://dom.spec.whatwg.org/#concept-tree)**Referenced in:**

- [18.5. Match a Selector Against a Tree](https://drafts.csswg.org/selectors-4/#ref-for-concept-tree)

[https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-a-element)**Referenced in:**

- [3.3. Scoped Selectors](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A0)
- [6.1. Attribute presence and value selectors](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A1) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A2) [(3)](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A3) [(4)](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A4) [(5)](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A5)
- [6.2. Substring matching attribute selectors](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A6)
- [8.1. The Hyperlink Pseudo-class: :any-link](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A7)
- [9\. User Action Pseudo-classes](https://drafts.csswg.org/selectors-4/#ref-for-the-a-element%E2%91%A8)

[https://html.spec.whatwg.org/multipage/image-maps.html#the-area-element](https://html.spec.whatwg.org/multipage/image-maps.html#the-area-element)**Referenced in:**

- [8.1. The Hyperlink Pseudo-class: :any-link](https://drafts.csswg.org/selectors-4/#ref-for-the-area-element)

[https://html.spec.whatwg.org/multipage/form-elements.html#the-button-element](https://html.spec.whatwg.org/multipage/form-elements.html#the-button-element)**Referenced in:**

- [4.3. The Negation (Matches-None) Pseudo-class: :not()](https://drafts.csswg.org/selectors-4/#ref-for-the-button-element)

[https://html.spec.whatwg.org/multipage/custom-elements.html#custom-element](https://html.spec.whatwg.org/multipage/custom-elements.html#custom-element)**Referenced in:**

- [5.4. The Defined Pseudo-class: :defined](https://drafts.csswg.org/selectors-4/#ref-for-custom-element)

[https://html.spec.whatwg.org/multipage/grouping-content.html#the-div-element](https://html.spec.whatwg.org/multipage/grouping-content.html#the-div-element)**Referenced in:**

- [6.6. Class selectors](https://drafts.csswg.org/selectors-4/#ref-for-the-div-element)
- [13.3.3. :first-child pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-the-div-element%E2%91%A0)
- [14.1. Descendant combinator ( )](https://drafts.csswg.org/selectors-4/#ref-for-the-div-element%E2%91%A1)

[https://html.spec.whatwg.org/multipage/custom-elements.html#element-definition](https://html.spec.whatwg.org/multipage/custom-elements.html#element-definition)**Referenced in:**

- [5.4. The Defined Pseudo-class: :defined](https://drafts.csswg.org/selectors-4/#ref-for-element-definition)

[https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-em-element](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-em-element)**Referenced in:**

- [14.1. Descendant combinator ( )](https://drafts.csswg.org/selectors-4/#ref-for-the-em-element) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-the-em-element%E2%91%A0)

[https://html.spec.whatwg.org/multipage/semantics.html#the-html-element](https://html.spec.whatwg.org/multipage/semantics.html#the-html-element)**Referenced in:**

- [13.1. :root pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-the-html-element)

[https://html.spec.whatwg.org/multipage/embedded-content.html#the-img-element](https://html.spec.whatwg.org/multipage/embedded-content.html#the-img-element)**Referenced in:**

- [13.4.1. :nth-of-type() pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-the-img-element)
- [13.4.2. :nth-last-of-type() pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-the-img-element%E2%91%A0)

[https://html.spec.whatwg.org/multipage/input.html#the-input-element](https://html.spec.whatwg.org/multipage/input.html#the-input-element)**Referenced in:**

- [9.4. The Focus-Indicated Pseudo-class: :focus-visible](https://drafts.csswg.org/selectors-4/#ref-for-the-input-element)
- [12\. The Input Pseudo-classes](https://drafts.csswg.org/selectors-4/#ref-for-the-input-element%E2%91%A0)
- [12.1.3. The Placeholder-shown Pseudo-class: :placeholder-shown](https://drafts.csswg.org/selectors-4/#ref-for-the-input-element%E2%91%A1)
- [12.3.1. The Empty-Value Pseudo-class: :blank](https://drafts.csswg.org/selectors-4/#ref-for-the-input-element%E2%91%A2)
- [Appendix B: Obsolete but Required Parsing Quirks for Web Compat](https://drafts.csswg.org/selectors-4/#ref-for-the-input-element%E2%91%A3)

[https://html.spec.whatwg.org/multipage/forms.html#the-label-element](https://html.spec.whatwg.org/multipage/forms.html#the-label-element)**Referenced in:**

- [9.1. The Pointer Hover Pseudo-class: :hover](https://drafts.csswg.org/selectors-4/#ref-for-the-label-element)
- [9.3. The Input Focus Pseudo-class: :focus](https://drafts.csswg.org/selectors-4/#ref-for-the-label-element%E2%91%A0)

[https://html.spec.whatwg.org/multipage/grouping-content.html#the-li-element](https://html.spec.whatwg.org/multipage/grouping-content.html#the-li-element)**Referenced in:**

- [14.2. Child combinator (>)](https://drafts.csswg.org/selectors-4/#ref-for-the-li-element) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-the-li-element%E2%91%A0)

[https://html.spec.whatwg.org/multipage/semantics.html#the-link-element](https://html.spec.whatwg.org/multipage/semantics.html#the-link-element)**Referenced in:**

- [8.1. The Hyperlink Pseudo-class: :any-link](https://drafts.csswg.org/selectors-4/#ref-for-the-link-element)

[https://html.spec.whatwg.org/multipage/semantics.html#meta](https://html.spec.whatwg.org/multipage/semantics.html#meta)**Referenced in:**

- [7.2. The Language Pseudo-class: :lang()](https://drafts.csswg.org/selectors-4/#ref-for-meta)

[https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-object-element](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#the-object-element)**Referenced in:**

- [6.2. Substring matching attribute selectors](https://drafts.csswg.org/selectors-4/#ref-for-the-object-element)

[https://html.spec.whatwg.org/multipage/grouping-content.html#the-ol-element](https://html.spec.whatwg.org/multipage/grouping-content.html#the-ol-element)**Referenced in:**

- [4.2. The Matches-Any Pseudo-class: :is()](https://drafts.csswg.org/selectors-4/#ref-for-the-ol-element)
- [14.2. Child combinator (>)](https://drafts.csswg.org/selectors-4/#ref-for-the-ol-element%E2%91%A0) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-the-ol-element%E2%91%A1)

[https://html.spec.whatwg.org/multipage/form-elements.html#the-option-element](https://html.spec.whatwg.org/multipage/form-elements.html#the-option-element)**Referenced in:**

- [12.1.3. The Placeholder-shown Pseudo-class: :placeholder-shown](https://drafts.csswg.org/selectors-4/#ref-for-the-option-element)

[https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element](https://html.spec.whatwg.org/multipage/grouping-content.html#the-p-element)**Referenced in:**

- [6.6. Class selectors](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element)
- [8.4. The Target Pseudo-class: :target](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element%E2%91%A0)
- [12.3.2. The Validity Pseudo-classes: :valid and :invalid](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element%E2%91%A1)
- [13.2. :empty pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element%E2%91%A2)
- [13.3.3. :first-child pseudo-class](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element%E2%91%A3)
- [14.1. Descendant combinator ( )](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element%E2%91%A4)
- [14.2. Child combinator (>)](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element%E2%91%A5) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element%E2%91%A6)
- [14.3. Next-sibling combinator (+)](https://drafts.csswg.org/selectors-4/#ref-for-the-p-element%E2%91%A7)

[https://html.spec.whatwg.org/multipage/input.html#attr-input-placeholder](https://html.spec.whatwg.org/multipage/input.html#attr-input-placeholder)**Referenced in:**

- [12.1.3. The Placeholder-shown Pseudo-class: :placeholder-shown](https://drafts.csswg.org/selectors-4/#ref-for-attr-input-placeholder)

[https://html.spec.whatwg.org/multipage/grouping-content.html#the-pre-element](https://html.spec.whatwg.org/multipage/grouping-content.html#the-pre-element)**Referenced in:**

- [14.4. Subsequent-sibling combinator (~)](https://drafts.csswg.org/selectors-4/#ref-for-the-pre-element)

[https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-q-element](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-q-element)**Referenced in:**

- [7.2. The Language Pseudo-class: :lang()](https://drafts.csswg.org/selectors-4/#ref-for-the-q-element)

[https://html.spec.whatwg.org/multipage/form-elements.html#the-select-element](https://html.spec.whatwg.org/multipage/form-elements.html#the-select-element)**Referenced in:**

- [12.1.3. The Placeholder-shown Pseudo-class: :placeholder-shown](https://drafts.csswg.org/selectors-4/#ref-for-the-select-element)

[https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-span-element](https://html.spec.whatwg.org/multipage/text-level-semantics.html#the-span-element)**Referenced in:**

- [6.1. Attribute presence and value selectors](https://drafts.csswg.org/selectors-4/#ref-for-the-span-element) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-the-span-element%E2%91%A0)
- [6.6. Class selectors](https://drafts.csswg.org/selectors-4/#ref-for-the-span-element%E2%91%A1)

[https://html.spec.whatwg.org/multipage/form-elements.html#the-textarea-element](https://html.spec.whatwg.org/multipage/form-elements.html#the-textarea-element)**Referenced in:**

- [12.3.1. The Empty-Value Pseudo-class: :blank](https://drafts.csswg.org/selectors-4/#ref-for-the-textarea-element)

[https://html.spec.whatwg.org/multipage/input.html#attr-input-value](https://html.spec.whatwg.org/multipage/input.html#attr-input-value)**Referenced in:**

- [12.3.1. The Empty-Value Pseudo-class: :blank](https://drafts.csswg.org/selectors-4/#ref-for-attr-input-value)

[https://infra.spec.whatwg.org/#ascii-case-insensitive](https://infra.spec.whatwg.org/#ascii-case-insensitive)**Referenced in:**

- [3.5. Pseudo-classes](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive)
- [3.6.1. Syntax](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A0)
- [3.7. Characters and case sensitivity](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A1)
- [6.3. Case-sensitivity](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A2) [(2)](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A3) [(3)](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A4)
- [6.6. Class selectors](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A5)
- [6.7. ID selectors](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A6)
- [7.2. The Language Pseudo-class: :lang()](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A7)
- [Appendix B: Obsolete but Required Parsing Quirks for Web Compat](https://drafts.csswg.org/selectors-4/#ref-for-ascii-case-insensitive%E2%91%A8)

[https://drafts.csswg.org/selectors-3/#x](https://drafts.csswg.org/selectors-3/#x)**Referenced in:**

- [3.6.2. Binding to the Document Tree](https://drafts.csswg.org/selectors-4/#ref-for-x)

[https://url.spec.whatwg.org/#concept-url-fragment](https://url.spec.whatwg.org/#concept-url-fragment)**Referenced in:**

- [8.4. The Target Pseudo-class: :target](https://drafts.csswg.org/selectors-4/#ref-for-concept-url-fragment)

### Terms defined by reference index-defined-elsewhere)

- \[css-display-3\] defines the following terms:
    - box tree
    - display
- \[CSS-PSEUDO-4\] defines the following terms:
    - ::after
    - ::before
    - ::first-letter
    - ::first-line
    - tree-abiding pseudo-element
- \[css-scoping-1\] defines the following terms:
    - ::content
    - ::shadow
    - ::slotted()
    - :host
    - :host-context()
    - flat tree
- \[css-speech-1\] defines the following terms:
    - strong
- \[css-text-3\] defines the following terms:
    - content language
    - document white space characters
- \[css-values-3\] defines the following terms:
    - <string>
- \[css-values-4\] defines the following terms:
    - !
    - #
    - \*
    - <ident>
    - ?
    - |
- \[css-writing-modes-3\] defines the following terms:
    - direction
- \[CSS21\] defines the following terms:
    - :lang
    - visibility
- \[CSS3NAMESPACE\] defines the following terms:
    - css qualified name
    - default namespace
- \[CSS3SYN\] defines the following terms:
    - <an+b>
    - <any-value>
    - <function-token>
    - <hash-token>
    - <ident-token>
    - <string-token>
    - identifier
    - parse
    - parse a list
- \[DOM\] defines the following terms:
    - Document
    - DocumentFragment
    - descendant
    - inclusive sibling
    - quirks mode
    - root
    - shadow host
    - shadow tree
    - shadow-including tree order
    - tree
- \[HTML\] defines the following terms:
    - a
    - area
    - button
    - custom element
    - div
    - element definition
    - em
    - html
    - img
    - input
    - label
    - li
    - link
    - meta
    - object
    - ol
    - option
    - p
    - placeholder
    - pre
    - q
    - select
    - span
    - textarea
    - value
- \[INFRA\] defines the following terms:
    - ascii case-insensitive
- \[SELECT\] defines the following terms:
    - \*
- \[URL\] defines the following terms:
    - fragment

## References references)

### Normative References normative)

\[CSS-DISPLAY-3\]

Tab Atkins Jr.; Elika Etemad. [CSS Display Module Level 3](https://www.w3.org/TR/css-display-3/). 19 May 2020. CR. URL: [https://www.w3.org/TR/css-display-3/](https://www.w3.org/TR/css-display-3/)

\[CSS-PSEUDO-4\]

Daniel Glazman; Elika Etemad; Alan Stearns. [CSS Pseudo-Elements Module Level 4](https://www.w3.org/TR/css-pseudo-4/). 25 February 2019. WD. URL: [https://www.w3.org/TR/css-pseudo-4/](https://www.w3.org/TR/css-pseudo-4/)

\[CSS-SCOPING-1\]

Tab Atkins Jr.; Elika Etemad. [CSS Scoping Module Level 1](https://www.w3.org/TR/css-scoping-1/). 3 April 2014. WD. URL: [https://www.w3.org/TR/css-scoping-1/](https://www.w3.org/TR/css-scoping-1/)

\[CSS-TEXT-3\]

Elika Etemad; Koji Ishii; Florian Rivoal. [CSS Text Module Level 3](https://www.w3.org/TR/css-text-3/). 29 April 2020. WD. URL: [https://www.w3.org/TR/css-text-3/](https://www.w3.org/TR/css-text-3/)

\[CSS-VALUES-3\]

Tab Atkins Jr.; Elika Etemad. [CSS Values and Units Module Level 3](https://www.w3.org/TR/css-values-3/). 6 June 2019. CR. URL: [https://www.w3.org/TR/css-values-3/](https://www.w3.org/TR/css-values-3/)

\[CSS-VALUES-4\]

Tab Atkins Jr.; Elika Etemad. [CSS Values and Units Module Level 4](https://www.w3.org/TR/css-values-4/). 31 January 2019. WD. URL: [https://www.w3.org/TR/css-values-4/](https://www.w3.org/TR/css-values-4/)

\[CSS-WRITING-MODES-3\]

Elika Etemad; Koji Ishii. [CSS Writing Modes Level 3](https://www.w3.org/TR/css-writing-modes-3/). 10 December 2019. REC. URL: [https://www.w3.org/TR/css-writing-modes-3/](https://www.w3.org/TR/css-writing-modes-3/)

\[CSS21\]

Bert Bos; et al. [Cascading Style Sheets Level 2 Revision 1 (CSS 2.1) Specification](https://www.w3.org/TR/CSS2/). 7 June 2011. REC. URL: [https://www.w3.org/TR/CSS2/](https://www.w3.org/TR/CSS2/)

\[CSS3NAMESPACE\]

Elika Etemad. [CSS Namespaces Module Level 3](https://www.w3.org/TR/css-namespaces-3/). 20 March 2014. REC. URL: [https://www.w3.org/TR/css-namespaces-3/](https://www.w3.org/TR/css-namespaces-3/)

\[CSS3SYN\]

Tab Atkins Jr.; Simon Sapin. [CSS Syntax Module Level 3](https://www.w3.org/TR/css-syntax-3/). 16 July 2019. CR. URL: [https://www.w3.org/TR/css-syntax-3/](https://www.w3.org/TR/css-syntax-3/)

\[DOM\]

Anne van Kesteren. [DOM Standard](https://dom.spec.whatwg.org/). Living Standard. URL: [https://dom.spec.whatwg.org/](https://dom.spec.whatwg.org/)

\[HTML\]

Anne van Kesteren; et al. [HTML Standard](https://html.spec.whatwg.org/multipage/). Living Standard. URL: [https://html.spec.whatwg.org/multipage/](https://html.spec.whatwg.org/multipage/)

\[INFRA\]

Anne van Kesteren; Domenic Denicola. [Infra Standard](https://infra.spec.whatwg.org/). Living Standard. URL: [https://infra.spec.whatwg.org/](https://infra.spec.whatwg.org/)

\[RFC2119\]

S. Bradner. [Key words for use in RFCs to Indicate Requirement Levels](https://tools.ietf.org/html/rfc2119). March 1997. Best Current Practice. URL: [https://tools.ietf.org/html/rfc2119](https://tools.ietf.org/html/rfc2119)

\[SELECT\]

Tantek Çelik; et al. [Selectors Level 3](https://www.w3.org/TR/selectors-3/). 6 November 2018. REC. URL: [https://www.w3.org/TR/selectors-3/](https://www.w3.org/TR/selectors-3/)

\[URL\]

Anne van Kesteren. [URL Standard](https://url.spec.whatwg.org/). Living Standard. URL: [https://url.spec.whatwg.org/](https://url.spec.whatwg.org/)

### Informative References informative)

\[BCP47\]

A. Phillips; M. Davis. [Tags for Identifying Languages](https://tools.ietf.org/html/bcp47). September 2009. IETF Best Current Practice. URL: [https://tools.ietf.org/html/bcp47](https://tools.ietf.org/html/bcp47)

\[CSS-SPEECH-1\]

Daniel Weck. [CSS Speech Module](https://www.w3.org/TR/css-speech-1/). 10 March 2020. CR. URL: [https://www.w3.org/TR/css-speech-1/](https://www.w3.org/TR/css-speech-1/)

\[CSS3UI\]

Tantek Çelik; Florian Rivoal. [CSS Basic User Interface Module Level 3 (CSS3 UI)](https://www.w3.org/TR/css-ui-3/). 21 June 2018. REC. URL: [https://www.w3.org/TR/css-ui-3/](https://www.w3.org/TR/css-ui-3/)

\[CSSSTYLEATTR\]

Tantek Çelik; Elika Etemad. [CSS Style Attributes](https://www.w3.org/TR/css-style-attr/). 7 November 2013. REC. URL: [https://www.w3.org/TR/css-style-attr/](https://www.w3.org/TR/css-style-attr/)

\[HTML5\]

Ian Hickson; et al. [HTML5](https://www.w3.org/TR/html5/). 27 March 2018. REC. URL: [https://www.w3.org/TR/html5/](https://www.w3.org/TR/html5/)

\[ITS20\]

David Filip; et al. [Internationalization Tag Set (ITS) Version 2.0](https://www.w3.org/TR/its20/). 29 October 2013. REC. URL: [https://www.w3.org/TR/its20/](https://www.w3.org/TR/its20/)

\[MATHML\]

Patrick D F Ion; Robert R Miner. [Mathematical Markup Language (MathML) 1.01 Specification](https://www.w3.org/TR/REC-MathML/). 7 July 1999. REC. URL: [https://www.w3.org/TR/REC-MathML/](https://www.w3.org/TR/REC-MathML/)

\[QUIRKS\]

Simon Pieters. [Quirks Mode Standard](https://quirks.spec.whatwg.org/). Living Standard. URL: [https://quirks.spec.whatwg.org/](https://quirks.spec.whatwg.org/)

\[RFC4647\]

A. Phillips; M. Davis. [Matching of Language Tags](https://tools.ietf.org/html/rfc4647). September 2006. Best Current Practice. URL: [https://tools.ietf.org/html/rfc4647](https://tools.ietf.org/html/rfc4647)

\[SVG11\]

Erik Dahlström; et al. [Scalable Vector Graphics (SVG) 1.1 (Second Edition)](https://www.w3.org/TR/SVG11/). 16 August 2011. REC. URL: [https://www.w3.org/TR/SVG11/](https://www.w3.org/TR/SVG11/)

\[XFORMS11\]

John Boyer. [XForms 1.1](https://www.w3.org/TR/xforms11/). 20 October 2009. REC. URL: [https://www.w3.org/TR/xforms11/](https://www.w3.org/TR/xforms11/)

\[XML-NAMES\]

Tim Bray; et al. [Namespaces in XML 1.0 (Third Edition)](https://www.w3.org/TR/xml-names/). 8 December 2009. REC. URL: [https://www.w3.org/TR/xml-names/](https://www.w3.org/TR/xml-names/)

\[XML10\]

Tim Bray; et al. [Extensible Markup Language (XML) 1.0 (Fifth Edition)](https://www.w3.org/TR/xml/). 26 November 2008. REC. URL: [https://www.w3.org/TR/xml/](https://www.w3.org/TR/xml/)