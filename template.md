Homework 1
================
Beibei Cao

This is my solution to HW1.

``` r
library(tidyverse)
```

    ## ── Attaching packages ──────────────────────────────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.3     ✓ dplyr   1.0.2
    ## ✓ tidyr   1.1.2     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ── Conflicts ─────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

## Problem 1

Create a data frame with the specified elements.

``` r
prob1_df = 
  tibble(
    samp = rnorm(10),
    samp_gt_0 = samp > 0,
    char_vec = c("a", "b", "c", "d", "e", "f", "g", "h", "i", "j"),
    factor_vec = factor(c("low", "low", "low", "mod", "mod", "mod", "mod", "high", "high", "high"))
  )
```

Take the mean of each variable in my data frame.

``` r
mean(pull(prob1_df, samp))
```

    ## [1] -0.1774616

``` r
mean(pull(prob1_df, samp_gt_0))
```

    ## [1] 0.3

``` r
mean(pull(prob1_df, char_vec))
```

    ## Warning in mean.default(pull(prob1_df, char_vec)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

``` r
mean(pull(prob1_df, factor_vec))
```

    ## Warning in mean.default(pull(prob1_df, factor_vec)): argument is not numeric or
    ## logical: returning NA

    ## [1] NA

I can take the means of numbers and logical but not character or factor.

Use `as.numeric` function to convert variables from one type to another.

``` r
as.numeric(pull(prob1_df, samp))
```

    ##  [1] -0.2317453  0.3494782  0.9851325 -0.6548249 -0.9190473 -0.1590957
    ##  [7] -0.5250126  1.2307863 -1.2223231 -0.6279638

``` r
as.numeric(pull(prob1_df, samp_gt_0))
```

    ##  [1] 0 1 1 0 0 0 0 1 0 0

``` r
as.numeric(pull(prob1_df, char_vec))
```

    ## Warning: NAs introduced by coercion

    ##  [1] NA NA NA NA NA NA NA NA NA NA

``` r
as.numeric(pull(prob1_df, factor_vec))
```

    ##  [1] 2 2 2 3 3 3 3 1 1 1

Convert the logical vector to numeric, and multiply the random sample by
the result.

``` r
as.numeric(pull(prob1_df, samp_gt_0)) * pull(prob1_df, samp)
```

    ##  [1] 0.0000000 0.3494782 0.9851325 0.0000000 0.0000000 0.0000000 0.0000000
    ##  [8] 1.2307863 0.0000000 0.0000000

Convert the logical vector to a factor, and multiply the random sample
by the result.

``` r
as.factor(pull(prob1_df, samp_gt_0)) * pull(prob1_df, samp)
```

    ## Warning in Ops.factor(as.factor(pull(prob1_df, samp_gt_0)), pull(prob1_df, : '*'
    ## not meaningful for factors

    ##  [1] NA NA NA NA NA NA NA NA NA NA

Convert the logical vector to a factor and then convert the result to
numeric, and multiply the random sample by the result

``` r
as.numeric(as.factor(pull(prob1_df, samp_gt_0))) * pull(prob1_df, samp)
```

    ##  [1] -0.2317453  0.6989565  1.9702651 -0.6548249 -0.9190473 -0.1590957
    ##  [7] -0.5250126  2.4615725 -1.2223231 -0.6279638

why not `$`

``` r
prob1_df$samp
```

    ##  [1] -0.2317453  0.3494782  0.9851325 -0.6548249 -0.9190473 -0.1590957
    ##  [7] -0.5250126  1.2307863 -1.2223231 -0.6279638

``` r
pull(prob1_df, samp)
```

    ##  [1] -0.2317453  0.3494782  0.9851325 -0.6548249 -0.9190473 -0.1590957
    ##  [7] -0.5250126  1.2307863 -1.2223231 -0.6279638

``` r
prob1_df[["samp"]]
```

    ##  [1] -0.2317453  0.3494782  0.9851325 -0.6548249 -0.9190473 -0.1590957
    ##  [7] -0.5250126  1.2307863 -1.2223231 -0.6279638

## Problem 2
