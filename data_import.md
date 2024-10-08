Data Import
================

This document will show how to import data.

## Import the FAS litters CSV

``` r
litters_df = read_csv("data/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Group, Litter Number, GD0 weight, GD18 weight
    ## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)

litters_df
```

    ## # A tibble: 49 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>           <chr>      <chr>             <dbl>           <dbl>
    ##  1 Con7  #85             19.7       34.7                 20               3
    ##  2 Con7  #1/2/95/2       27         42                   19               8
    ##  3 Con7  #5/5/3/83/3-3   26         41.4                 19               6
    ##  4 Con7  #5/4/2/95/2     28.5       44.1                 19               5
    ##  5 Con7  #4/2/95/3-3     <NA>       <NA>                 20               6
    ##  6 Con7  #2/2/95/3-2     <NA>       <NA>                 20               6
    ##  7 Con7  #1/5/3/83/3-3/2 <NA>       <NA>                 20               9
    ##  8 Con8  #3/83/3-3       <NA>       <NA>                 20               9
    ##  9 Con8  #2/95/3         <NA>       <NA>                 20               8
    ## 10 Con8  #3/5/2/2/95     28.5       <NA>                 20               8
    ## # ℹ 39 more rows
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
head(litters_df)
```

    ## # A tibble: 6 × 8
    ##   group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##   <chr> <chr>         <chr>      <chr>             <dbl>           <dbl>
    ## 1 Con7  #85           19.7       34.7                 20               3
    ## 2 Con7  #1/2/95/2     27         42                   19               8
    ## 3 Con7  #5/5/3/83/3-3 26         41.4                 19               6
    ## 4 Con7  #5/4/2/95/2   28.5       44.1                 19               5
    ## 5 Con7  #4/2/95/3-3   <NA>       <NA>                 20               6
    ## 6 Con7  #2/2/95/3-2   <NA>       <NA>                 20               6
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
tail(litters_df, 10)
```

    ## # A tibble: 10 × 8
    ##    group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>         <chr>      <chr>             <dbl>           <dbl>
    ##  1 Mod8  #7/110/3-2    27.5       46                   19               8
    ##  2 Mod8  #2/95/2       28.5       44.5                 20               9
    ##  3 Mod8  #82/4         33.4       52.7                 20               8
    ##  4 Low8  #53           21.8       37.2                 20               8
    ##  5 Low8  #79           25.4       43.8                 19               8
    ##  6 Low8  #100          20         39.2                 20               8
    ##  7 Low8  #4/84         21.8       35.2                 20               4
    ##  8 Low8  #108          25.6       47.5                 20               8
    ##  9 Low8  #99           23.5       39                   20               6
    ## 10 Low8  #110          25.5       42.7                 20               7
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
view(litters_df)
```

Use relative paths

``` r
pups_df = read_csv("data/FAS_pups.csv")
```

    ## Rows: 313 Columns: 6
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Litter Number, PD ears
    ## dbl (4): Sex, PD eyes, PD pivot, PD walk
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
pups_df= janitor::clean_names(pups_df) 

head(pups_df)
```

    ## # A tibble: 6 × 6
    ##   litter_number   sex pd_ears pd_eyes pd_pivot pd_walk
    ##   <chr>         <dbl> <chr>     <dbl>    <dbl>   <dbl>
    ## 1 #85               1 4            13        7      11
    ## 2 #85               1 4            13        7      12
    ## 3 #1/2/95/2         1 5            13        7       9
    ## 4 #1/2/95/2         1 5            13        8      10
    ## 5 #5/5/3/83/3-3     1 5            13        8      10
    ## 6 #5/5/3/83/3-3     1 5            14        6       9

Use an absolute path. Does not work once data wrangling folder was moved
to bonus_directory. Relative path will still work tho.

``` r
pups_df = read.csv("/Users/tinavarela/Desktop/data_wrangling_1/data/FAS_pups.csv")
```

## look at read csv options

col_names and skipping rows

``` r
litters_df = 
  read_csv(
    file = "data/FAS_litters.csv",
    col_names= FALSE,
    skip = 2
  )
```

    ## Rows: 48 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): X1, X2, X3, X4
    ## dbl (4): X5, X6, X7, X8
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df
```

    ## # A tibble: 48 × 8
    ##    X1    X2              X3    X4       X5    X6    X7    X8
    ##    <chr> <chr>           <chr> <chr> <dbl> <dbl> <dbl> <dbl>
    ##  1 Con7  #1/2/95/2       27    42       19     8     0     7
    ##  2 Con7  #5/5/3/83/3-3   26    41.4     19     6     0     5
    ##  3 Con7  #5/4/2/95/2     28.5  44.1     19     5     1     4
    ##  4 Con7  #4/2/95/3-3     <NA>  <NA>     20     6     0     6
    ##  5 Con7  #2/2/95/3-2     <NA>  <NA>     20     6     0     4
    ##  6 Con7  #1/5/3/83/3-3/2 <NA>  <NA>     20     9     0     9
    ##  7 Con8  #3/83/3-3       <NA>  <NA>     20     9     1     8
    ##  8 Con8  #2/95/3         <NA>  <NA>     20     8     0     8
    ##  9 Con8  #3/5/2/2/95     28.5  <NA>     20     8     0     8
    ## 10 Con8  #5/4/3/83/3     28    <NA>     19     9     0     8
    ## # ℹ 38 more rows

What about missing data

``` r
litters_df = 
  read_csv(
    file = "data/FAS_litters.csv",
    na = c("NA", "", ".")
  )
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

What if we code `group` as a factor variable

``` r
litters_df = 
  read_csv(
    file = "data/FAS_litters.csv",
    na = c("NA", "", "."),
    col_types = cols(
      Group = col_factor()
    )
  )
```

## Import an Excel File

Import MLB 2011 summary data, only use sheet = when there are multiple
sheets. This one does not, but is included for practice.

``` r
mlb_df = read_excel("data/mlb11.xlsx", sheet = "mlb11")
```

## Import SAS data

``` r
pulse_df = read_sas("data/public_pulse_data.sas7bdat")
```

## Never use read.csv, and never use the \$
