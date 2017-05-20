---
title: 'Day 13: Refactoring and URL design'
author: Srinivasan Rangarajan
date: 2017-04-25
url: /day-13-refactoring-and-url-design
categories:
  - Programming
tags:
  - 100DaysOfCode

---
Today I spent most of the time refactoring the entry view function. Moving the save functionality into it&#8217;s own separate function.

This refactoring is needed because I have to add a way to get all entries that were added between two dates. The entry view function is becoming too big and I definitely need a cleanup for implementing this new feature better.

<!--more-->

I have been thinking hard about how best to create the URL for this and since URL. Currently the URL structure is something like /entry/YYYY/MM/DD/ and you can remove the DD and MM part to show entries for a month and an year respectively. But I want the user to be able to see all entries from a date till another date.

### Option 1:

Use an URL like /entry/YYYY/MM/DD/to/YYYY/MM/DD/. While this does make it easy to remember and type, it does make writing code to handle all the different combinations hard. What is the user wants to put in just /entry/YYYY/MM/to/YYYY/MM ? And what if he gives date in from and no date in the to section?

### Option 2:

Accept the from and to as GET params &#8211; like /entry/?from=YYYY-MM-DD&to=YYYY-MM-DD. This makes it easier to code and will introduce a lot lesser bugs. But the downside is bad URL design.

These are the two options I can think of and I think I will go with the second option for it&#8217;s ease of implementation.