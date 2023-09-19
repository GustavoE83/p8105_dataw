R Markdown File lol
================
Gustavo Garcia-Franceschini
2023-09-19

# Data

``` r
pups_df = janitor::clean_names(read_csv("data/FAS_pups.csv"))
```

    ## Rows: 313 Columns: 6
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (1): Litter Number
    ## dbl (5): Sex, PD ears, PD eyes, PD pivot, PD walk
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

# Looking at data

``` r
head(pups_df)
```

    ## # A tibble: 6 × 6
    ##   litter_number   sex pd_ears pd_eyes pd_pivot pd_walk
    ##   <chr>         <dbl>   <dbl>   <dbl>    <dbl>   <dbl>
    ## 1 #85               1       4      13        7      11
    ## 2 #85               1       4      13        7      12
    ## 3 #1/2/95/2         1       5      13        7       9
    ## 4 #1/2/95/2         1       5      13        8      10
    ## 5 #5/5/3/83/3-3     1       5      13        8      10
    ## 6 #5/5/3/83/3-3     1       5      14        6       9

``` r
tail(pups_df)
```

    ## # A tibble: 6 × 6
    ##   litter_number   sex pd_ears pd_eyes pd_pivot pd_walk
    ##   <chr>         <dbl>   <dbl>   <dbl>    <dbl>   <dbl>
    ## 1 #2/95/2           2       4      12        7       9
    ## 2 #2/95/2           2       3      13        6       8
    ## 3 #2/95/2           2       3      13        7       9
    ## 4 #82/4             2       4      13        7       9
    ## 5 #82/4             2       3      13        7       9
    ## 6 #82/4             2       3      13        7       9

Summary

``` r
str(pups_df)
```

    ## spc_tbl_ [313 × 6] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
    ##  $ litter_number: chr [1:313] "#85" "#85" "#1/2/95/2" "#1/2/95/2" ...
    ##  $ sex          : num [1:313] 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ pd_ears      : num [1:313] 4 4 5 5 5 5 NA 4 4 4 ...
    ##  $ pd_eyes      : num [1:313] 13 13 13 13 13 14 14 13 13 NA ...
    ##  $ pd_pivot     : num [1:313] 7 7 7 8 8 6 5 6 7 8 ...
    ##  $ pd_walk      : num [1:313] 11 12 9 10 10 9 9 8 9 10 ...
    ##  - attr(*, "spec")=
    ##   .. cols(
    ##   ..   `Litter Number` = col_character(),
    ##   ..   Sex = col_double(),
    ##   ..   `PD ears` = col_double(),
    ##   ..   `PD eyes` = col_double(),
    ##   ..   `PD pivot` = col_double(),
    ##   ..   `PD walk` = col_double()
    ##   .. )
    ##  - attr(*, "problems")=<externalptr>

``` r
skimr::skim(pups_df)
```

|                                                  |         |
|:-------------------------------------------------|:--------|
| Name                                             | pups_df |
| Number of rows                                   | 313     |
| Number of columns                                | 6       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |         |
| Column type frequency:                           |         |
| character                                        | 1       |
| numeric                                          | 5       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |         |
| Group variables                                  | None    |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| litter_number |         0 |             1 |   3 |  15 |     0 |       49 |          0 |

**Variable type: numeric**

| skim_variable | n_missing | complete_rate |  mean |   sd |  p0 | p25 | p50 | p75 | p100 | hist  |
|:--------------|----------:|--------------:|------:|-----:|----:|----:|----:|----:|-----:|:------|
| sex           |         0 |          1.00 |  1.50 | 0.50 |   1 |   1 |   2 |   2 |    2 | ▇▁▁▁▇ |
| pd_ears       |        18 |          0.94 |  3.68 | 0.59 |   2 |   3 |   4 |   4 |    5 | ▁▅▁▇▁ |
| pd_eyes       |        13 |          0.96 | 12.99 | 0.62 |  12 |  13 |  13 |  13 |   15 | ▂▇▁▂▁ |
| pd_pivot      |        13 |          0.96 |  7.09 | 1.51 |   4 |   6 |   7 |   8 |   12 | ▂▇▂▂▁ |
| pd_walk       |         0 |          1.00 |  9.50 | 1.34 |   7 |   9 |   9 |  10 |   14 | ▆▇▇▂▁ |

Fun fact: `read_csv` has an `na` argument. If you write
`na = c(77, 99)`, those cells will become NA. Useful for survey stuff.

# Fixing col types

``` r
litters_df =
  read_csv(
    "data/FAS_litters.csv",
    col_types =
      cols(
      `GD0 weight` = col_character()
  ))
```

# Other file types

Excel:

``` r
mlb_df = 
  read_excel("data/mlb11.xlsx")
```

SAS:

``` r
pulse =
  read_sas("data/public_pulse_data.sas7bdat")
```
