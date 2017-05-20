---
title: 'Day 11: Edit an existing entry'
author: Srinivasan Rangarajan
date: 2017-04-23
url: /day-11-edit-an-existing-entry
categories:
  - Programming
tags:
  - 100DaysOfCode

---
Still stuck with a crappy internet, but I did get some time and bandwidth to complete one important feature that was very much needed &#8211; Editing an entry.

Previously all entries were insert only, no edits were possible. I thought there shouldn&#8217;t be a way to edit the history (or the future) for that matter. So I went with an insert only design. But within 2 days of using the software, I found editing entries is very much needed.

<!--more-->

The code to allow editing is easy to implement and all you have to do is, pass ?edit=true as GET params to a page and you will be shown the edit screen.

I think I might restrict edits to only today&#8217;s entries instead of being able to edit any arbitrary day&#8217;s entries. But that is for a future release.

But for milestone v0.2, I would have to probably remove couple of issues and mark the milestone as complete. Next week, when I go back to mainland, I will add more features.