---
title: 'Day 15: Last N days and email multiple entries'
author: Srinivasan Rangarajan
date: 2017-04-27
url: /day-15-last-n-days-and-email-multiple-entries
categories:
  - Programming
tags:
  - 100DaysOfCode
  - python

---
Since I try to make most of the interaction with the web app through the URL, I wanted to add an easier way to get the last N entries. I added a new view function which displays the last N entries.

The user has to visit /entry/last/N/ to display the N days&#8217; entries. This is in fact quite simple to implement after I have implemented the [custom date range filters][1] yesterday. I just calculate the from and to date based on the last N dates and I redirect the user to the right filters.

<!--more-->

The second feature I added was to send an email to all the users based on the filter you have selected. Previously the app used to send emails only when a new day&#8217;s entry was created.

Now at the end of every entry page, be it a single day&#8217;s entry or a month or a year or any custom date ranges, there is an Email button which will send the report to all the subscribed users in the system.

For now the implementation is simple as I reuse the email function and I pass all the entries for the given query.
  
I might change it later to not email all users and instead to let the user specify an email address.

I do want to clean up the templates and fix some timezone related bugs, But I think the app is in a stable state that I will not be concentrating on this daily. Instead I will be working on a new project that I want to build using Golang &#8211; so that I can start using golang as my primary programming language.

Tomorrow I will be doing a few more tests, some basic cleanup, deploying of latest code to heroku and making the code repository public. From Saturday, I will be working on my golang project.

 [1]: http://cnu.name/day-14-custom-date-ranges/