---
title: 'Day 16: Email template fixes, deploy, public repo'
author: Srini
date: 2017-04-28
url: /day-16-email-template-fixes-deploy-public-repo
categories:
  - Programming
tags:
  - 100DaysOfCode
  - bsd
  - go
  - golang
  - license

---
Yesterday when I added the feature to email users multiple day&#8217;s entries, there was one small bug that I missed. The subject like still showed the first entry&#8217;s date. I fixed it by making sure that if we are emailing a single day&#8217;s entry, it showed one date and if we are emailing more than a day&#8217;s entry, it will show the from and to dates.

<!--more-->

Other than that bug fix and a few docstrings, I deployed all the changes from past 3-4 days to heroku. Even though the changes are simple, I didn&#8217;t want to [debug a silly error][1] when someone is editing the entries in the morning.

Another major change in the project is making it a [public repository][2]. Previously the code was private, but since the code is now decent enough and gets the work done, I am making it public. Code reviews, pull requests are welcome. I usually prefer [BSD 3 clause license][3] for such kind of small scripts or web apps and I am releasing it under the same license.

Now that it is stable enough for daily use, I will not be adding new features to this daily. I will be working on it when I get some free time or want to improve the design. But what will I do for the rest of the 84 days of the challenge?

The whole point of the challenge is to push yourself to learn new stuff and me building yet another web app is too un-challenging (if thats even a word). So I decided to concentrate on sharpening my golang and start building some tools or services using it.

What changes? Nothing! I will have to brush up on my golang skills and decide on a simple project to work on. I will be logging my progress in evernote instead of posting about it daily in this blog. I do want to make sure to post here at least twice a week with detailed progress. But my daily public progress tracker will be on twitter ([@cnu][4]).

 [1]: http://cnu.name/day-9-markdown-jinja-templates-for-email-and-fixing-bugs-live/
 [2]: https://gitlab.com/cnu/nillu/
 [3]: https://opensource.org/licenses/BSD-3-Clause
 [4]: https://twitter.com/cnu