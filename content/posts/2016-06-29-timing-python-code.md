---
author: Srinivasan Rangarajan
categories: 
  - Programming
tags:
  - programming
  - python
  - profiling
date: 2016-06-29T22:21:35+05:30
title: Timing your Python Code
url: /timing-python-code

---

There are many times when you would want to see how much time your program takes to execute. The easiest way to do it on a unix system is to use the `time` command before running the program.

<!--more-->

    $ time command

    real    0m1.320s
    user    0m0.010s
    sys     0m0.023s

This shows that the `command` took 1.32 seconds of wall clock time and 0.01s of time spent in userspace and 0.023s of time spent in kernel space.

This works well for any command you can run on the shell. But how would you find out how long a python function took? Or how long a particular line of code took?

The usual way I used to do was create a `time.time()` object before the piece of code, store it in a variable. Do the same `time.time()` and subtract from the previously stored value and print it. 

Nothing wrong with it. But instead of repeating this same piece of code everywhere, there has got to be a better way.

Let me introduce the timing context manager.

Create a module called `timer.py` and paste the following piece of code in it.

    import time

    class Timer(object):
        def __init__(self, verbose=False):
            self.verbose = verbose

        def __enter__(self):
            self.start = time.time()
            return self

        def __exit__(self, *args):
            self.end = time.time()
            self.secs = self.end - self.start
            self.msecs = self.secs * 1000  # millisecs
            if self.verbose:
                print 'elapsed time: %f ms' % self.msecs

Now all you have to do is, in the module where you want to time a piece of code,

    from timer import Timer
    ...
    with Timer() as t:
        some_slow_function()
    print 'elapsed: %ss' % t.secs

You can use `t.msecs` to display it in milliseconds. 

This is such a simple and elegant solution to log the time taken, that these kind of modules will probably have to go in a private python-utils package which I can import in any project I want. 