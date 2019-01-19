
<!-- README.md is generated from README.Rmd. Please edit that file -->
forcats <img src='man/figures/logo.png' align="right" height="139" />
=====================================================================

<!-- badges: start -->
[![CRAN status](https://www.r-pkg.org/badges/version/forcats)](https://cran.r-project.org/package=forcats) [![Travis build status](https://travis-ci.org/tidyverse/forcats.svg?branch=master)](https://travis-ci.org/tidyverse/forcats) [![Codecov test coverage](https://codecov.io/gh/tidyverse/forcats/branch/master/graph/badge.svg)](https://codecov.io/gh/tidyverse/forcats?branch=master) <!-- badges: end -->

Overview
--------

R uses **factors** to handle categorical variables, variables that have a fixed and known set of possible values. Historically, factors were much easier to work with than character vectors, so many base R functions automatically convert character vectors to factors. (For historical context, I recommend [*stringsAsFactors: An unauthorized biography*](http://simplystatistics.org/2015/07/24/stringsasfactors-an-unauthorized-biography/) by Roger Peng, and [*stringsAsFactors = &lt;sigh&gt;*](http://notstatschat.tumblr.com/post/124987394001/stringsasfactors-sigh) by Thomas Lumley. If you want to learn more about other approaches to working with factors and categorical data, I recommend [*Wrangling categorical data in R*](https://peerj.com/preprints/3163/), by Amelia McNamara and Nicholas Horton.) These days, making factors automatically is no longer so helpful, so packages in the [tidyverse](http://tidyverse.org) never create them automatically.

However, factors are still useful when you have true categorical data, and when you want to override the ordering of character vectors to improve display. The goal of the **forcats** package is to provide a suite of useful tools that solve common problems with factors. If you're not familiar with strings, the best place to start is the [chapter on factors](http://r4ds.had.co.nz/factors.html) in R for Data Science.

Installation
------------

``` r
# The easiest way to get forcats is to install the whole tidyverse:
install.packages("tidyverse")

# Alternatively, install just forcats:
install.packages("forcats")

# Or the the development version from GitHub:
# install.packages("devtools")
devtools::install_github("tidyverse/forcats")
```

Getting started
---------------

forcats is part of the core tidyverse, so you can load it with `library(tidyverse)` or `library(forcats)`.

``` r
library(forcats)
```

Factors are used to describe categorical variables with a fixed and known set of **levels**. You can create factors with the base `factor()` or [`readr::parse_factor()`](http://readr.tidyverse.org/reference/parse_factor.html):

``` r
x1 <- c("Dec", "Apr", "Jan", "Mar")
month_levels <- c(
  "Jan", "Feb", "Mar", "Apr", "May", "Jun", 
  "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"
)

factor(x1, month_levels)
#> [1] Dec Apr Jan Mar
#> Levels: Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec

readr::parse_factor(x1, month_levels)
#> [1] Dec Apr Jan Mar
#> Levels: Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec
```

The advantage of `parse_factor()` is that it will generate a warning if values of `x` are not valid levels:

``` r
x2 <- c("Dec", "Apr", "Jam", "Mar")

factor(x2, month_levels)
#> [1] Dec  Apr  <NA> Mar 
#> Levels: Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec

readr::parse_factor(x2, month_levels)
#> Warning: 1 parsing failure.
#> row col           expected actual
#>   3  -- value in level set    Jam
#> [1] Dec  Apr  <NA> Mar 
#> attr(,"problems")
#> # A tibble: 1 x 4
#>     row   col expected           actual
#>   <int> <int> <chr>              <chr> 
#> 1     3    NA value in level set Jam   
#> Levels: Jan Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec
```

Once you have the factor, forcats provides helpers for solving common problems.

Getting help
------------

If you encounter a clear bug, please file a minimal reproducible example on [github](https://github.com/tidyverse/forcats/issues). For questions and other discussion, please use [community.rstudio.com](https://community.rstudio.com/).

Code of Conduct
---------------

Please note that the 'forcats' project is released with a [Contributor Code of Conduct](.github/CODE_OF_CONDUCT.md). By contributing to this project, you agree to abide by its terms.
