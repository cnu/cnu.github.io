---
title: 'Day 4: Displaying the entry and editing it'
author: Srinivasan Rangarajan
date: 2017-04-16
url: /day-4-displaying-the-entry-and-editing-it
categories:
  - Programming
tags:
  - 100DaysOfCode

---
Today was a slow day as I had to spend some time with family given most of the long weekend was spent on coding. But I did get to completing a working Entry page. Though not pretty, it conveys the information to the user.

<!--more-->

Right now for each day it displays the entries for each user. If a particular day doesn&#8217;t have any entry, it redirects to the edit page for that date. The edit page is almost similar to the entry page, but with text areas instead of displaying the entry. (Btw, why is text area still so fugly?)

I did want to build the entry forms dynamically for each user in the system, but decided to do it in jinja templates instead. I would like to do it through WTForms so that I can do server side validations and add a consistent way to include the CSRF field.

For today&#8217;s milestone, I need to save the entry from the edit screen and have to send an email after saving the entry.

After that, for the next week&#8217;s milestone, I will put in extra checks like preventing users to not edit the history, displaying the entries using markdown, displaying entries for multiple dates, etc.

**Update:** I had set a milestone for v0.1 and I had to finish it. The last parts to be completed were editing and saving an edit for a day&#8217;s entry. And to send an email whenever a day&#8217;s entry was created. To send emails, I used the Flask-Mail extension which is as easy as plugging in a few configs and creating a Message object.

**Bonus:** The emails are also HTML emails so I have added basic <b> tags to highlight specific words.