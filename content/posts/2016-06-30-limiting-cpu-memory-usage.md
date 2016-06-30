---
author: Srinivasan Rangarajan
categories: 
  - Programming
tags:
  - programming
  - python
date: 2016-06-30T22:21:35+05:30
title: Limiting your CPU and Memory Usage
url: /limiting-cpu-memory-usage

---

Yesterday I wrote about how to use a very simple timing context manager to measure how much time your python code/functions take. There might be times when you want to restrict how long your code executes. Python's [`resource`](https://docs.python.org/2/library/resource.html) module in the standard library gives you an easy way to do that and more. 

Here is a simple program which shows you how it is done:

<!--more-->

    import signal
    import resource
    import os

    def time_exceeded(signo, frame):
        raise SystemExit("Time's up!")  # prints the text and exits with error code 1

    def set_max_runtime(seconds):
        # Install the signal handler and set a resource limit
        soft, hard = resource.getrlimit(resource.RLIMIT_CPU)
        resource.setrlimit(resource.RLIMIT_CPU, (seconds, hard))
        signal.signal(signal.SIGXCPU, time_exceeded)

    if __name__ == '__main__':
        set_max_runtime(15)
        while True:
            pass

While running the program, it shows the following output.

    $ time python test.py
    Time's up!

    real    0m14.999s
    user    0m14.998s
    sys     0m0.000s

In this program, `resource.setrlimit()` is used to set a soft and hard limit on a particular resource. 

* The *soft limit* is the current limit, and may be lowered or raised by the process over time. When the operating system reaches the soft limit, it will typically restrict or notify the process via a signal. 

* The *hard limit* represents an upper bound on the values that may be used for the soft limit. It can only be lowered upto the soft limit and can never be raised by the user process. To raise the hard limit, you need to be a superuser.

The best thing about the resource module is that it can be used to set the limits for lot of system resources like  the number of child processes, number of open files, maximum size of the heap and even the maximum memory the process takes.

To limit the maximum memory a process takes, use something like this

    def limit_memory(maxsize):
        soft, hard = resource.getrlimit(resource.RLIMIT_AS)
        resource.setrlimit(resource.RLIMIT_AS, (maxsize, hard))

It would be best to check the [documentation page of resource module](https://docs.python.org/2/library/resource.html) to find out what other resources can be restricted. 
