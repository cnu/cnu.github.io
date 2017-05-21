---
author: Srinivasan Rangarajan
categories: 
  - Programming
tags:
  - programming
  - unix
  - zsh
  - ohmyzsh
date: 2016-06-25T22:41:37+05:30
title: d command in oh my zsh
url: /d-command-in-oh-my-zsh

---

I use [zsh](http://www.zsh.org/) as my primary shell and have [Oh My Zsh](http://ohmyz.sh/) which has lot of helpful plugins, themes and functions which make using the terminal easy. One neat command/alias I found out was when I typed **`d`** by mistake. 

<!--more-->

I got back a listing of all my previously visited directories.

    0   ~/Projects/foo
    1   ~/Projects/foo/bar/baz
    2   ~/Projects/foo/bar
    3   ~/Projects/foo/baz
    4   ~/Projects/foo/baz/baz
    5   ~/Projects/foo/spam
    6   ~/Projects
    7   ~
    8   ~/Projects/eggs
    9   ~/Projects/foo/eggs

And I typed a number and was magically transported to that directory. 

But it is all magic only till the trick is exposed, right? All I had to do was do a little bit of googling to find that the `d` alias was powered by a built-in command called `dirs`. 

Looking at the the [source code of the directories.sh plugin](https://github.com/robbyrussell/oh-my-zsh/blob/master/lib/directories.zsh), I also learnt another neat trick. 

I have always known that typing `cd -` would swap me between the previous directory and the current directory. Seems like the innocuous `cd` command has more options. You can type `cd -2` or `cd -3` and so on to jump to the 2<sup>nd</sup>/3<sup>rd</sup> previously visited directory. Now machines I don't have zsh installed, instead of `pushd`/`popd`, I can easily do a `cd -n`.

Zsh/oh-my-zsh makes it all so easy. You should also try it instead of the old bash.