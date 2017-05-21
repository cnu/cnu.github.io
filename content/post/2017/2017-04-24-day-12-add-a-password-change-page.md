---
title: 'Day 12: Add a password change page'
author: Srinivasan Rangarajan
date: 2017-04-24
url: /day-12-add-a-password-change-page
categories:
  - Programming
tags:
  - 100DaysOfCode
  - passwords

---
Thinking of the next important feature that would be asked to make others to use the app is the Password Change screen. Right now, we have 8 users on the app and it was I who set everyone&#8217;s password. But soon they would want to change it to something more secure.

<!--more-->

So I quickly wrote a view function which will display a password change form and will also change it if the password and confirm_password fields match. It also logs the user out on successful password change. All of this was made easy because of [Flask-Login][1].

Tomorrow I will be back to my home and would have a much better internet and more time to program.

 [1]: https://flask-login.readthedocs.io