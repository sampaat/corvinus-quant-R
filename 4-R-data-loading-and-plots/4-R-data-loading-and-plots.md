Lesson 4: R Data loading, plots
========================================================
author: Mate Csaba Sandor
date: 2018 September
autosize: true


Reminder about regular expressions
========================================================

- Here is a handy app for [learning regexp in general](https://regexone.com/)
- For R specifics you should check this [cheatsheet](https://www.rstudio.com/wp-content/uploads/2016/09/RegExCheatsheet.pdf)

Data? So basic..
========================================================

- In a firm we usually have a database where we can perform SQL queries
- Now we do not have access to such thins unfortunately
- BUT! Nevertheless, you should learn how to write simple SQL queries 
- [This](https://www.codecademy.com/learn/learn-sql) is a really good 2 hour course that gives you most of what you need to start
- To set up database connections in R you should use `odbc` or `jdbc` packages to set up the connection adn `DBI` to send queries. The responses then are a perfect feed for SQL.

Let's trade Bitcoin! Or not. Whatever.
========================================================

[Here](http://bitcoincharts.com) you can get some sweet exchange datasets, let's download some.

```r
library(readr)
read_csv("http://api.bitcoincharts.com/v1/csv/anxhkUSD.csv.gz") 
```

```
# A tibble: 640,824 x 3
   `1376999407` `100.000000000000` `5.000000000000`
          <int>              <dbl>            <dbl>
 1   1376999726                99              5.5 
 2   1377000070                99              0.05
 3   1377000070               100              0.95
 4   1377000113               100              4   
 5   1377005870               100              1.05
 6   1377019633               103              3.5 
 7   1377042357                99              1.2 
 8   1377042421               102              3   
 9   1377042472                99              2.5 
10   1377101655               102.             1.2 
# ... with 640,814 more rows
```
Hmm. Interesting.

Figuring out the dataset, make it tidy
========================================================


```r
library(magrittr)
readr::read_csv("http://api.bitcoincharts.com/v1/csv/anxhkUSD.csv.gz", col_names = c("date", "volume", "price")) %>%
  dplyr::mutate(date = as.POSIXct(date, origin="1970-01-01"))
```

```
# A tibble: 640,825 x 3
   date                volume price
   <dttm>               <dbl> <dbl>
 1 2013-08-20 13:50:07    100  5   
 2 2013-08-20 13:55:26     99  5.5 
 3 2013-08-20 14:01:10     99  0.05
 4 2013-08-20 14:01:10    100  0.95
 5 2013-08-20 14:01:53    100  4   
 6 2013-08-20 15:37:50    100  1.05
 7 2013-08-20 19:27:13    103  3.5 
 8 2013-08-21 01:45:57     99  1.2 
 9 2013-08-21 01:47:01    102  3   
10 2013-08-21 01:47:52     99  2.5 
# ... with 640,815 more rows
```
And so on...

Questions:
- Which was the most active month?
- What is the bottom 5th percentile of the price returns? (function to use: `lag`)

Exercise time!
========================================================

Yahoo Finance is ususally my first go-to if I need some stock or ETF data.
https://finance.yahoo.com/quote/%5EGSPC/history?p=%5EGSPC

- Download S&P500 full history
- Donwload Dow Jones full history
- Join the second to the first while holding on to all records (see `left_join`, `inner_join` and friends)

We can do excels as well!
========================================================
Download excel file from [here](http://www.cboe.com/micro/buywrite/monthendpricehistory.xls) or jus google "cboe excel download"



















```
During startup - Warning messages:
1: Setting LC_CTYPE failed, using "C" 
2: Setting LC_COLLATE failed, using "C" 
3: Setting LC_TIME failed, using "C" 
4: Setting LC_MESSAGES failed, using "C" 
5: Setting LC_MONETARY failed, using "C" 


processing file: 4-R-data-loading-and-plots.Rpres
Parsed with column specification:
cols(
  `1376999407` = col_integer(),
  `100.000000000000` = col_double(),
  `5.000000000000` = col_double()
)
Parsed with column specification:
cols(
  date = col_integer(),
  volume = col_double(),
  price = col_double()
)
Quitting from lines 61-62 (4-R-data-loading-and-plots.Rpres) 
Error: `path` does not exist: 'monthendpricehistory.xls'
Execution halted
```
