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























```
Error in open.connection(con, "rb") : 
  Timeout was reached: Resolving timed out after 10000 milliseconds
```
