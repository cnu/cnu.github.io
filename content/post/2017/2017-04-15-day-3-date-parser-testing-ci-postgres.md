---
title: 'Day 3: Date Parser, Testing, CI, Postgres'
author: Srinivasan Rangarajan
date: 2017-04-15
url: /day-3-date-parser-testing-ci-postgres
categories:
  - Programming
tags:
  - 100DaysOfCode
  - ci
  - continuous integration
  - docker
  - postgres
  - postgresql
  - sqlite
  - test cases
  - unit tests

---
Yesterday I said I would be spending all of today on getting the entries page done. I did work on the date parser part of the entries view function, but I didn&#8217;t fully implement the views function yet.

<!--more-->

### Date Parser

The idea is you can pass different types of dates in the URL and see/edit the entries for that date. For example: /entry/2017/04/15/ would show the entries for 15th of April, 2017. You can also goto /entry/today/ and /entry/yesterday/ as shortcuts for the corresponding days.

For tomorrow&#8217;s v0.1 milestone, I think I will implement just these types of dates. But for the next milestone (next week) I want to display all the entries for a month (/entry/2017/04/) and for an year (/entry/2017/). This makes it easy to generate reports for entire month or year.

### Test cases

While the date parser was easy to implement, I spent the most of my time writing unit test cases.

<blockquote class="twitter-tweet" data-lang="en">
  <p dir="ltr" lang="en">
    And Remember Kids..
  </p>
  
  <p>
    Writing code: 1hrs<br /> Fixing bugs: 3hrs
  </p>
  
  <p>
    Writing code: 1hrs<br /> Writing tests: 1hrs<br /> Fixing bugs: 10mins
  </p>
  
  <p>
    — Mahdi Yusuf (@myusuf3) <a href="https://twitter.com/myusuf3/status/685834795193098240">January 9, 2016</a>
  </p>
</blockquote>



Even though I spent most of today writing test cases, it would help a lot when I refactor the code base. Test cases is something that I haven&#8217;t given much attention to in my projects at work. But I do know that there is a much higher probability of catching and fixing bugs if you have proper test cases.

One example of such a bug was in the date parser function I just wrote. I was doing a check to see if the date was a future date as I don&#8217;t want to edit the future entries before the day. The code was pretty simple.

<pre class="prettyprint lang-python" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">if date_obj - today &gt; 0:
    raise FutureDateException("Trying to edit the future.")</pre>

The bug is that `date_obj - today` returns a timedelta object and you can&#8217;t really compare it with int. I wouldn&#8217;t have caught this bug till I finished the views function and manually entered different types of dates. But since I wrote a test case to cover this line I found out the bug and handled it properly.

### Testing Web Apps

Usually testing web apps are not that easy and that is one major reason I hate writing test cases. But flask has few helpful ways to make it easy. But I wanted to test whether a URL redirects properly. For that I ended up using the [Flask-Testing][1] extension. If you are writing flask apps, I would suggest using Flask-Testing.

### Continuous Integration

Since I use Gitlab for hosting my code, I ended up setting up a Pipeline to run tests automatically whenever I push any code. I use [Gitlab-CI][2] for it. It is a bit different compared to the [Github][3]+[Travis][4] combo I used to use earlier. But the advantage of Gitlab-CI is you can specify what docker image to use to run your builds/tests. And I always felt that even with my sparing builds, travis was overloaded and had lot of downtime. Gitlab-CI seems to be quite fast in spinning up jobs as soon as a git push is done.

### Moving to PostgreSQL

I was using SQLite for my development and tests, but I knew I had to move to PostgreSQL soon as I will be deploying on it. I didn&#8217;t want any surprises when I made the switch. Using an ORM does abstract out most of the pieces, but I did get couple of surprises.

  1. bcrypt&#8217;s hash function returns a byte object and SQLite doesn&#8217;t have any problem in storing a byte in a text column. In fact SQLite wouldn&#8217;t even complain about most data types. But Postgres kept saying that I was trying to store more than varchar(120) even though the hash value was just 60 characters long. Then I remembered that for python 3, I had to do a .decode(&#8216;utf-8&#8217;) to convert it into a str type. Weird error message, but quite easy to google and figure out.
  2. Postgresql has it&#8217;s own Enum datatype and whenever you create a enum type, you have to give a name for it. In SQLite there is no Enum data type and there was no error even if you didn&#8217;t give a name. But when I moved to postgres, I had to pass  a name param to the Enum.
  
    All I had to do was  `db.Enum('done', 'todo', 'blocking', name='entry_types')`

Other than these two gotchas, there were no other issues in the database change.

### Docker

Btw, I didn&#8217;t want to install postgresql on my Mac OS and ended up running a docker container for the DB. The commands to run the DB server was:

<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">docker run --name nillu-pg -e POSTGRES_PASSWORD=foobar -p5432:5432 -d postgres</pre>

and the command to run the psql prompt was

<pre class="prettyprint lang-sh" data-start-line="1" data-visibility="visible" data-highlight="" data-caption="">docker run -it --rm --link nillu-pg:postgres postgres psql -h postgres -U postgres</pre>

For tomorrow, I definitely need to display the entry page and the edit screen for &#8220;today&#8221;. And I also need to send an email to the users. Those are the three things that are definitely needed for the app to be usable on Monday.

&nbsp;

 [1]: https://pythonhosted.org/Flask-Testing/
 [2]: https://about.gitlab.com/gitlab-ci/
 [3]: https://github.com/
 [4]: https://travis-ci.org/