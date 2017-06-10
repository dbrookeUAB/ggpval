ggpval user guide
================
Jun Cheng

<!-- README.md is generated from README.Rmd. Please edit that file -->
ggpval
======

`ggpval` allow you to generate statistic test and add test p-value to plots automatically. P-valules can be presented as formated p-values or with stars (e.g. \*, \*\*). Alternatively one can also annotation groups with text.

Installation
------------

You can install ggpval from github with:

``` r
# install.packages("devtools")
devtools::install_github("s6juncheng/ggpval")
```

Example
-------

This is a basic example which shows you how to solve a common problem:

``` r
## basic example code
```

Example
-------

Simulate data with groups.

``` r
library(ggpval)
library(data.table)
library(ggplot2)
A <- rnorm(200, 0, 3)
B <- rnorm(200, 2, 4)
G <- rep(c("G1", "G2"), each = 100)
dt <- data.table(A, B, G)
dt <- melt(dt, id.vars = "G")
```

A trivial boxplot example
-------------------------

Give group pairs you want to compare in `pairs`.

``` r
plt <- ggplot(dt, aes(variable, value)) +
  geom_boxplot() +
  geom_jitter()

add_pval(plt, pairs = list(c(1, 2)))
```

![](README-unnamed-chunk-3-1.png)

Boxplot with facets
-------------------

``` r
plt <- ggplot(dt, aes(variable, value)) +
  geom_boxplot() +
  geom_jitter() +
  facet_wrap(~G)
add_pval(plt, pairs = list(c(1, 2)))
```

![](README-unnamed-chunk-4-1.png)
