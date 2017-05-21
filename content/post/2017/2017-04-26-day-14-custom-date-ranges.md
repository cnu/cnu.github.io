---
title: 'Day 14: Custom Date Ranges'
author: Srinivasan Rangarajan
date: 2017-04-26
url: /day-14-custom-date-ranges
categories:
  - Programming
tags:
  - 100DaysOfCode

---
Today I completed the [custom date ranges][1] that I talked about in yesterday&#8217;s post. Instead of just displaying a day/month/year, you can choose a from and a to date range and all entries that were created in that range will be displayed.

<!--more-->

I ended up using GET parameter to get the date ranges. You have to form the URL as /entry/?from=2017-04-01&to=2017-04-26 to display all entries from 1st of April till 26th of April (both inclusive).

 [1]: http://cnu.name/day-13-refactoring-and-url-design/