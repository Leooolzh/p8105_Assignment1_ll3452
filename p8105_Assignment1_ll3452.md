Assignment 1
================
Leo Liu
Sept 14 2020

This is my solution to Assignment 1

``` r
library(tidyverse)
```

    ## ── Attaching packages ───────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.3     ✓ dplyr   1.0.2
    ## ✓ tidyr   1.1.2     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ── Conflicts ──────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(ggplot2)
```

### Problem 1

Create a data frame with the specified elements.

``` r
df = tibble(num = rnorm(10), 
            log_vec = num > 0 , 
            char_vec = c('a','b','c','b','c','c','a','b','a','c'), 
            fac_vec =      factor(c("F1","F2","F1","F1","F3","F2","F2","F1","F3","F3")))
```

Take the mean of each variable in the data frame df

``` r
mean(pull(df, num))
```

    ## [1] 0.4855733

``` r
mean(pull(df, log_vec))
```

    ## [1] 0.7

``` r
mean(pull(df, char_vec))
```

    ## Warning in mean.default(pull(df, char_vec)): argument is not numeric or logical:
    ## returning NA

    ## [1] NA

``` r
mean(pull(df, fac_vec))
```

    ## Warning in mean.default(pull(df, fac_vec)): argument is not numeric or logical:
    ## returning NA

    ## [1] NA

We cannot take the mean of character vectors and factor vectors.
Therefore, we should try to convert them into numerical values first
using as.numeric

``` r
as.numeric(pull(df, log_vec))
```

    ##  [1] 1 0 1 1 0 1 1 1 0 1

``` r
as.numeric(pull(df, char_vec))
```

    ## Warning: NAs introduced by coercion

    ##  [1] NA NA NA NA NA NA NA NA NA NA

``` r
as.numeric(pull(df, fac_vec))
```

    ##  [1] 1 2 1 1 3 2 2 1 3 3
