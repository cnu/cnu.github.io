---
title: 'Day 1: Daily Standup Meeting Logger'
author: Srinivasan Rangarajan
date: 2017-04-13T23:21:35+05:30
url: /day-1-daily-standup-meeting-logger
categories:
  - Programming
tags:
  - 100DaysOfCode
  - flask
  - python

---
Everyday at work, the first meeting (of the numerous ones) we have is the backend team&#8217;s daily standup meeting. This is an important meeting because this is the only time and place where we get to discuss what we would be working on to build/improve the main platform/product of the company. 

We also discuss on what pending delivery items are there and what is in each team member&#8217;s todo list. There are other standup meetings about what we have for day&#8217;s delivery and that doesn&#8217;t exactly follow a template of a standup meeting.

<!--more-->

Each member of the team gets to be that week&#8217;s scrum master or in other words, the person who collects all the discussed points and sends an email to the team and other delivery managers. This isn&#8217;t a strict scrum style standup meeting, but more of a &#8220;what are all my todo items today?&#8221; meeting. There are a few problems with this:

  1. Even though the minutes of the meeting is captured on email, it is not the proper way to log what was done and what is to be done today.
  2. Remembering to send the email to the developers in the To field and to the managers in the CC field, is hard.
  3. We don&#8217;t track the &#8220;done&#8221; and the &#8220;blocked on&#8221; parts properly.

But I hear you asking how all these can be easily captured if we use a proper agile issue tracker. But making the team use a proper issue tracker with all the agile features is a high friction task. Right now this 10 minute meeting works fine for the team and I wanted to capture and log the meeting better.

This is my first project for the 100 Days of Code challenge.
  
[Nillu][1]: A simple web application to log and email the daily standup meetings to everyone involved.

It is a simple web app which has a matrix of developers vs (done, todo, blocked) items. The scrum master fills in the details for each person and updates it. The details are stored in a DB and also emailed to everyone else on the team including managers.

<a href="https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/Update-Page.png" rel="attachment wp-att-105"><img class="aligncenter size-full wp-image-105" src="https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/Update-Page.png?fit=744%2C577" alt="Update Page Mockup" srcset="https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/Update-Page.png?w=744 744w, https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/Update-Page.png?resize=300%2C233 300w, https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/Update-Page.png?resize=640%2C496 640w" sizes="(max-width: 744px) 100vw, 744px" data-recalc-dims="1" /></a>

### Language and framework

I prefer to program using python and I decided to use [Flask][2] as the web framework for this. Since this is a maximum of one or two pages, I didn&#8217;t want a heavy weight Django framework. And for my personal web applications I prefer flask. I do want to develop it in python 3 as I want to move away from python 2.

I have built a basic schema for the DB with two models &#8211; User and Entry. The user will have a role &#8211; developer or non-developer. Only developers will have entries against their name. But the email will be sent to all users. Developers will be sent in the To field and the non-developers will be CC&#8217;ed. Similarly each entry could be one of the following: done, todo, blocking. And each entry has an user and date associated with it.

The last time I used flask was way back when it was in version 0.7 and currently in 0.12 lot of new things has come up. There is a separate flask command to run your app. You can add custom commands to the flask command line tool, which is useful for initialising the DB.

I am tracking the [issues and features][3] in gitlab. The code is private for now, but I might open source it later.

Lot of interesting changes and lot of new things to learn. Lets see what I can do tomorrow.

 [1]: https://gitlab.com/cnu/nillu/
 [2]: http://flask.pocoo.org/
 [3]: https://gitlab.com/cnu/nillu/boards