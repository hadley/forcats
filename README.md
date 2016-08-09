# forcats

[![Travis-CI Build Status](https://travis-ci.org/hadley/forcats.svg?branch=master)](https://travis-ci.org/hadley/forcats)

forcats provides tools for **cat**egorical variables (forcats is an anagram of factors).

## Installation

You can install forcats from github with:

```R
# install.packages("devtools")
devtools::install_github("hadley/forcats")
```

## Key functions:

Change order of levels:

* `fct_inorder()`: order by first appearance of each level,
* `fct_infreq()`: order by frequency.
* `fct_reorder()`: order by summary of another value.
* `fct_relevel()`: re-order "by hand".
* `fct_shift()`: shift order to the left/right.

Change value of levels:

* `fct_collapse()`: lump rare levels into "other".
* `fct_recode()`: manually recode levels.

A few other helpers:

* `fct_c()`: concatenate factors using union of levels.
* `fct_unify()`: ensure list of factors all share the same levels.
* `fct_drop()`: same as `base::droplevels()`.
* `fct_rev()`: reverse factor levels.
* `lvl_union()`: finds union of levels from list of factors.

## Caveats

* This was written in two hours of frenzied coding.
* There are no unit tests
