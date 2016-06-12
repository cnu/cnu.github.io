---
title: Tackle Technical Debt with Time Bombs
author: Srinivasan Rangarajan
layout: post
date: 2015-01-01
url: /tackle-technical-debt/
categories:
  - Programming
tags:
  - programming

---
Technical Debt is a term that most developers have heard of. Even if you haven&#8217;t heard of the term, I am pretty sure you would have done something in your programming career that is a technical debt.

> [Technical Debt][1] is a metaphor referring to the eventual consequences of poor system design, software architecture or software development within a codebase.

In most cases, it is that quick and dirty hack your manager asked to put in just so that he could deliver it to the client.

Most technical debts requires two persons (it could also be the same person donning two hats). One is the business guy and other is the technical guy.

#### Can we finish this with a quick hack?

Let&#8217;s say you are building a new feature in the product &#8211; &#8220;provide different levels of access to normal users and admin users&#8221;. The right way to do it is to build a permission system with groups and manage them via a database. Assume building that would take 2 days.

But your manager comes around and says, we need to release this immediately as the client is waiting for this feature to sign up. Can we just put in a couple of if-else blocks and deal with the permission in DB stuff later?

<a href="http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/01/office-space.jpg" rel="attachment wp-att-30"><img class="aligncenter wp-image-30 size-medium" src="http://i0.wp.com/cnu.name/wp-content/uploads/sites/7/2015/01/office-space-300x251.jpg?fit=300%2C251" alt="Yeeaah! If you could just do this quick fix, that'd be great." srcset="http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/01/office-space.jpg?resize=300%2C251 300w, http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/01/office-space.jpg?resize=250%2C209 250w, http://i2.wp.com/cnu.name/wp-content/uploads/sites/7/2015/01/office-space.jpg?w=500 500w" sizes="(max-width: 300px) 100vw, 300px" data-recalc-dims="1" /></a>

Technically you could do it and you say that unless this is refactored as early as possible, it would be hard to add more features or be difficult to handle it in all the templates.

You agree to put in a temporary hack and the company signs up the client and also gets its first cheque. But now that you have a paying client, you need to quickly build more features and you still haven&#8217;t gotten the time to refactor the code.

Any new features you add, must also include a provision for that hack and this is the interest you pay for that technical debt.

#### Why didn&#8217;t you do it the right way?

Your manager though was happy that you delivered the product with a workaround, doesn&#8217;t realize the amount of time/effort/money required to refactor it. What would have been a couple of days to get it right the first time, now requires at least a week to refactor & one more person to test all possible combinations in all the templates.

Pretty soon you need to pay back the technical debt and if your manager is also like most other non-technical managers, he would shout at you for not implementing it the right way the first time around. Or you quit your job at that company and the next person who look at your code says &#8220;Who the Fuck wrote this shitty piece of code?&#8221;

#### Now how can we as developers avoid this?

**Step 1:** When you make the decision to take the technical debt, you could create a pending issue in your issue tracker (you do use one, right?) and say why and who took the decision. Also make a note on what date that debt needs to be repaid.

Decide whatever happens, by that date that quick and dirty hack should be removed and a well designed version be pushed to production.

**Step 2:** is to setup a time bomb in the code. Cause we all know how strict these issue trackers are followed. All it takes is for one person to mark the issue as &#8220;completed&#8221; and we forget about it after a month.

Have a small piece of code which starts sending an email to the dev list about the pending debt about 2 weeks before the date it should be repaid. Let it send an email every day and on the date decided, it should just stop working (or at least show some embarrassing photo of your manager as an easter egg)

#### What else can be done?

While in theory this is cool, implementing such a piece of code, testing that it works and letting this pass through management would be very hard.

The alternative to this should be to implement a special label in the issue tracker.

Issue trackers should have a special label/tag called &#8220;Tech Debt&#8221;.

  * It should be only closed by a developer (preferably by a quorum of developers).
  * Should send emails daily based on the due date if it is still open.
  * If it is still open on the day before the due date, all other issues should be hidden this should be the only visible issue.

I am not saying this would work 100%, but at least this would increase the manager&#8217;s attention given to such technical debts and make sure that proper resources are spent in fixing them.

Yeah, and if some developer of an issue tracker or a plugin developer could implement this feature, that&#8217;d be great.

 [1]: http://en.wikipedia.org/wiki/Technical_debt