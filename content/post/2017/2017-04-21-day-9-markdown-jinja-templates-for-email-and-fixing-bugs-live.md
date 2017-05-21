---
title: 'Day 9: Markdown, Jinja Templates for email and fixing bugs live'
author: Srinivasan Rangarajan
date: 2017-04-21
url: /day-9-markdown-jinja-templates-for-email-and-fixing-bugs-live
categories:
  - Programming
tags:
  - 100DaysOfCode
  - bootstrap
  - flask
  - markdown
  - testing

---
Working late at night after office work means, I can&#8217;t put in my best effort on this challenge. So I wanted to change my schedule into coding in the morning as soon as I wake up. But yesterday, after writing the post, I continued and worked on supporting markdown for the entry text and adding Jinja support for email templates.

<!--more-->

## Flask-Markdown and Bleach

[Flask-Markdown][1] does a pretty easy job of integrating markdown in your flask app. But I wanted to support only a subset of the tags, like ordered and unordered list, bold, italics, etc. I don&#8217;t want a h1 tag included in an entry.

To strip out such tags and allow only a specified list of tags, there is a python package called [bleach][2]. You specify which tags are allowed and it encodes it into HTML entities or even strips out those tags.

So I had to pass the entry&#8217;s text through a markdown filter and then through a bleach filter. I also used Markdown package&#8217;s nl2br extension instead of my custom template filter. Less number of code means less bugs.

## Jinja Email Templates

For the emails, I was using normal python formatted strings. I was constructing the string using complex loops and lists. I wanted to use [Jinja][3] templates as I already use that for the HTML pages. Replacing with Jinja means there is a single template string/file and I can store it in a config table in a database. For now I have it embedded in the views.py file. But later I will move it to a file or DB.

## Beautified Text Area

HTML Text areas are always an eyesore. The width and height are fixed and doesn&#8217;t adjust based on the window width. [Bootstrap][4] makes it easy to beautify it. All I had to do was add a form-control class to the textarea.

## Fixing Bugs Live

Today during the call, I typed out all the text and pressed he save button waiting for a beautiful email in my inbox. Instead I saw an error screen and couldn&#8217;t understand why. All my changes were simple and not in the actual business logic. Why an error suddenly.

Remember how I was trying to beautify the textarea? I added one more feature where I set a jinja variable so that I can reuse it for the name of the textarea and the label tag. The way I constructed the variable was wrong and it caused all the text areas to not have a name.

I made two mistakes:

  1. combine two fixes in one commit. One commit should always be for fixing 1 bug/issue. Don&#8217;t combine multiple fixes into one commit. Hard to debug and hard to revert back too.
  2. Didn&#8217;t have test cases for saving entries via the HTML templates. I had basic test cases which tested the views, but no test cases to add a day&#8217;s entry via the HTML templates.

So I had to rush and fix the code during the call and it was slightly panicking.

This is a lesson that I think will have to be etched into my brain (and many other developers&#8217; brains).

BTW, I will be travelling for the next 3 days and may not have a good internet connection. I will have to try to commit something and try to finish the milestone over the weekend.

 [1]: https://pythonhosted.org/Flask-Markdown/
 [2]: https://bleach.readthedocs.io
 [3]: http://jinja.pocoo.org/
 [4]: http://getbootstrap.com/