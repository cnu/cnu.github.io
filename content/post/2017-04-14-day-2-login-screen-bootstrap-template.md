---
title: 'Day 2: Login Screen and Bootstrap Template'
author: Srinivasan Rangarajan
date: 2017-04-14
url: /day-2-login-screen-bootstrap-template
categories:
  - Programming
tags:
  - 100DaysOfCode
  - authentication
  - bcrypt
  - login
  - passwords

---
Initially when I thought of building the Daily Standup Meeting Logger, I decided to give one single master password and whoever wants to access it, will just type the password to login.

<!--more-->

  * But whenever someone leaves the team, you have to reset the password.
  * If the password is leaked, because someone decided to write it down on a post it, you have to reset the password.
  * And giving different set of permissions for developers vs non-developers with a single password is hard.

Since I already have a users table with all types of users in the system, I decided to add a password field to it. I hate having to handle user&#8217;s authentication and would prefer to not have a password based authentication at all. But for the v0.1 milestone that I have set for Sunday (16 April), I decided to go with the traditional route of having a email/password combo.

Lot of people make mistakes when storing passwords. I don&#8217;t want to reinvent the wheel, so I just use bcrypt for hashing the passwords. [Flask-Bcrypt][1] is a very easy to use extension which handles salting and hashing the passwords.

Even though an user system is available, the only way to add new users is through the flask shell command line tool or insert queries in the DB directly. I think for v0.1, I can live without an UI for user management.

Second part of what I did today was to slap on a Bootstrap base template for the project so that the UI looks pretty. Bootstrap is my preferred way to get out of designing a good user interface.

Though the base template is put in place, I have integrated only the login template with bootstrap. I haven&#8217;t even written the views for displaying or updating the entries.

<a href="https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/login-screen.png" rel="attachment wp-att-110"><img class="aligncenter size-full wp-image-110" src="https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/login-screen.png?fit=874%2C756" alt="login screen" srcset="https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/login-screen.png?w=874 874w, https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/login-screen.png?resize=300%2C259 300w, https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/login-screen.png?resize=768%2C664 768w, https://i1.wp.com/cnu.name/wp-content/uploads/sites/7/2017/04/login-screen.png?resize=640%2C554 640w" sizes="(max-width: 874px) 100vw, 874px" data-recalc-dims="1" /></a>

Tomorrow I will be concentrating on adding/updating/viewing the entries.

 [1]: http://pythonhosted.org/Flask-Bcrypt/