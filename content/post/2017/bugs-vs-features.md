---
title: "Which is important? Fixing Bugs or Adding Features"
date: 2017-09-28T06:04:37+05:30
author: Srinivasan Rangarajan
url: /bugs-vs-features
categories: "Software Development"
tags:
  - software
  - programming
  - bugs
  - features
  - business of software

---

Lets say you are building a Social Media marketing automation product, where you allow the users to schedule multiple posts to different social media platforms. For your first release, you plan to have only Twitter as the only platform. You release it and people love your product. 

There are a few bugs. Sometimes the posts aren't saved to the DB and get lost. Other times the posts aren't tweeted at the right time it was scheduled for. These are minor annoyances, but your early adopters don't care about them. 

**Question**: You have a week of your developer's time after which he goes off for a long vacation, what would you do?

<!--more-->

* **Option A:** Add a brand new feature (posting to facebook or instagram) that is going to get you more money?

* **Option B:** Fix these two bugs that existing customers have been complaining about?

![Bugs vs Features](/img/bugs-vs-features.jpg)

### Option A: MOAR FEATURES

Lot of business/non-tech guys in a company would prefer to build out more features in the product. 

As a customer, new features are like candy to a 5 year old. If you love a product so much, you would want to see more features so that you get more value for the money you pay.

And for the sales/marketing people, new features are an easy way to entice more customers. You can reach out to a new market segment altogether. Adding Instagram means, you can reach out to ecommerce sites. Adding LinkedIn means, you can reach out to companies who are looking to hire people.

These minor bugs are just annoyances and not many customers are complaining about them yet. So there is still time to work on it. We will fix it eventually.

This mentality makes a lot of sense to the CEO and the Board, because everyone wants more revenue right? If adding one small feature can 2x or even 3x your revenue, you would have to be stupid not to do it.

### Option B: FIX SHIT

If you chose Option B, there is a high probability that you are a developer. You understand how technical debts pile up and unless you fix the core of the product first, it would be a big pain in the ass later on. 

Maybe the [database choice was wrong](https://news.ycombinator.com/item?id=15124306) and that is what is causing the saving problems? Or you are using some [fancy task scheduler](http://www.celeryproject.org/) that everyone is using, but the process keeps getting killed or running out of memory. 

*Sometimes the fix could be simple:* Use a crontab instead of the scheduler.

*Sometimes the fix could be complex:* Use a better database and move your data to the new DB. But it involves a migration plan to make sure the existing customers aren't affected. 

Depending upon the severity of the bug and the issues that might come up later, you would prioritise which to fix. But you would make sure to fix these ASAP cause you know about the Broken Window Theory.

### Broken Window Theory

Broken Window Theory is a theory about norm-setting and signaling effect of vandalism and disorder, causing more crime and anti-social behaviour. 

> Consider a building with a few broken windows. If the windows are not repaired, the tendency is for vandals to break a few more windows. Eventually, they may even break into the building, and if it's unoccupied, perhaps become squatters or light fires inside.

> Or consider a pavement. Some litter accumulates. Soon, more litter accumulates. Eventually, people even start leaving bags of refuse from take-out restaurants there or even break into cars.

Lot of psychologist have conducted numerous experiments about this and it shows that if some property is not maintained properly, it would become the norm and any new maintainers would also not care about it so much.

This holds true to any piece of code or product. If you don't care enough to fix the bugs in the product first, new hires would also think that developers in this company doesn't care enough to fix bugs. And when they find new bugs, they would leave it unfixed. 

**Not fixing bugs would become the norm.**

Good developers always try to fix bugs before writing more new code. They understand how difficult it is to build something on a badly built/architected code. Just like no builder would build a house on top of a bad basement.

## But we can't fix all the bugs

I hear you complain "No one can create software without any bugs." True. 

> If debugging is the process of removing bugs, then programming must be the process of putting them in. 
> - Edsger W. Dijkstra

What I am asking for is to fix the known bugs first before you add more features. Even then there are two kinds of bugs:

1. Things you know are broken on the inside, also known as Technical Debt
2. Things your customers know are broken and keep complaining.

You need to track both these kinds of bugs and make sure you handle the bugs that the customer knows. Many times if you target the customer facing bugs, most of the internal bugs will also be fixed as a side-effect.


## Why it makes business sense to fix bugs first

If you keep adding more features, which means more bugs, then the customers would soon be tired of using your product and eventually leave. To say it in a term you would understand: **Churn**.

Customers will stop using your product, as it causes unwanted frustration when using it. This will affect your Monthly Active Users (MAU) and eventually they will stop paying for a service which they no longer use. 

Then they will leave angry reviews and comments about your product and future customers will also not sign up for your service. This is going to affect your Revenue Growth. And finally, your valuation is going to tank and it would be next to impossible to raise a new round of funding. 

All of this happened because you didn't give time for the developer to fix the two bugs.

So next time before you plan/build a new feature, make sure you fix all the known bugs first.