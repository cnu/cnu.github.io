---
title: 'Day 8: Deployed to Heroku and Fixed user ordering'
author: Srinivasan Rangarajan
date: 2017-04-20
url: /day-8-deployed-to-heroku-and-fixed-user-ordering
categories:
  - Programming
tags:
  - 100DaysOfCode
  - deploy
  - heroku

---
Today was an important milestone &#8211; I finally deployed the app to [Heroku][1] and today&#8217;s standup meeting was logged using the app. Emails went out to both developers and non-developers and it was beautiful to see the app working so smoothly.

<!--more-->

But of course the deployment didn&#8217;t go without hiccups. I was trying to deploy it using gunicorn and by following the official flask documentation on [deploying to gunicorn][2], my Procfile was supposed to be

<pre><span class="n">web: gunicorn</span> <span class="n">nillu</span><span class="p">:</span><span class="n">app</span></pre>

But even after many combinations I couldn&#8217;t get it to work as gunicorn kept complaining about not able to import nillu.app.

Finally I had to create a wsgi.py file which had these lines:

<pre>from nillu import app as application

if __name__ == '__main__':
    application.run()</pre>

And my Procfile had just

<pre>web: gunicorn wsgi</pre>

This is the combination that worked.

When I received the emails today morning, I noticed that the user names were sorted in a different order than the /entry/ page. I wanted to maintain an alphabetical order for the names and managed to do it in the templates by sending a user order variable.

For the emails I used the default random ordering of the dict which caused this inconsistency. I had to pass the same user order to the email template generation program and the bug was fixed.

But I did find a few more bugs like if I don&#8217;t fill in any entry for a user, it still creates three empty entry rows. This should not happen. And the email should also not include users with empty entries. I will try to fix it later maybe.

But tomorrow I do want to beautify the entries a little bit by allowing markdown text (a subset of markdown).

&nbsp;

&nbsp;

 [1]: http://www.heroku.com/
 [2]: http://flask.pocoo.org/docs/0.12/deploying/wsgi-standalone/#gunicorn