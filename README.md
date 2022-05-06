Example report with R Markdown
================
Kim Martin
2022-05-06

## This document

The aim of this document is to analyze inflammation data from the
r-novice-inflammation dataset.

You can find the original data here:
<http://swcarpentry.github.io/r-novice-inflammation/setup.html>

### Method

A function to create plots for individual files was created:

``` r
analyze <- function(filename) {
  
  # takes a filename with relative path
  # reads the csv
  # calculates avg, max, min
  # creates panel of 3 plots
  
  dat <- read.csv(file = filename, header = FALSE)
  
  
  # calculate avg, max, min by column (per day)
  
  avg_day_inflammation <- apply(dat, 2, mean)
  
  max_day_inflammation <- apply(dat, 2, max)
  
  min_day_inflammation <- apply(dat, 2, min)
  
  
  # plot avg, max, min daily inflammation
  
  par(mfrow = c(1, 3)) # set up 1x3 plot panel
  
  plot(avg_day_inflammation, main = filename)
  
  plot(max_day_inflammation, main = filename)
  
  plot(min_day_inflammation, main = filename)
  
  par(mfrow = c(1, 1)) # return plot setting to 1x1
  
}
```

### Data files

``` r
fnames <- list.files('data', pattern = 'inflammation', full.names = TRUE)

print(fnames)
```

    ##  [1] "data/inflammation-01.csv" "data/inflammation-02.csv"
    ##  [3] "data/inflammation-03.csv" "data/inflammation-04.csv"
    ##  [5] "data/inflammation-05.csv" "data/inflammation-06.csv"
    ##  [7] "data/inflammation-07.csv" "data/inflammation-08.csv"
    ##  [9] "data/inflammation-09.csv" "data/inflammation-10.csv"
    ## [11] "data/inflammation-11.csv" "data/inflammation-12.csv"
