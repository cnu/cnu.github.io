---
title: 'Day 5: Month and Year view'
author: Srinivasan Rangarajan
date: 2017-04-17
url: /day-5-month-year-view
categories:
  - Programming
tags:
  - 100DaysOfCode

---
Being a Monday, I was busy with my work projects. But I managed to put in a very simple feature. The ability to display a month or even an years&#8217; entries in 1 page.

By going to /entry/2017/04 you can see all the entries from 2017-04-01 till 2017-04-30 (or till today if the current month isn&#8217;t complete yet. Similarly visiting /entry/2017/ will show all entries for the entire year.

<!--more-->

For the month view, I need to find out how many days a particular month has. I can spend a few days to put in the right conditions to calculate this or I can use the [calendar][1] standard library package in python. There is a function called monthrange which returns how many days a month has.

<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">_, num_days_in_month = calendar.monthrange(year, month)</pre>

This one line is all it takes to do complex calendar arithmetic without any mistakes. With just this and a few more lines for handling year, I was able to generate SQLAlchemy queries to get all entries which is between two dates.

And since I had refactored all the processing of the rows to separate functions, the change took practically 5 minutes to code. Remember kids, write modular code. Separate out your code into methods and functions.

I will be travelling for most part of tomorrow, so don&#8217;t know what I will be able to finish tomorrow. I also need to deploy the app on Heroku maybe?

 [1]: https://docs.python.org/3.6/library/calendar.html