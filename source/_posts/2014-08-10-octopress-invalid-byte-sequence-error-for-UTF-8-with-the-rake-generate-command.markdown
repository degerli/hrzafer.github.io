---
layout: post
title: "Octopress 'invalid byte sequence in UTF-8' error with the rake generate command"
date: 2014-08-10 15:15:00 +0300
comments: true
categories: octopres, github
---
This is my first post on this blog. Since it was going to be mostly about my work on Github, I decided to publish it on GitHub and naturally this made me choose [Octopress](http://octopress.org). After [installing and deploying octopress](http://www.techelex.org/setup-octopress-on-windows7/) successfully, I just wanted to edit `_config.yml` to set my name for the `author` and `title` properties. As my name (Harun Reşit Zafer) has the non-ascii `ş` in it when I try to run the `rake generate` command, I got the `invalid byte sequence in UTF-8` error. 

After some googling I found several pages that all suggest creating some system (or environment on Windows) variables called `LANG`, `LC_ALL` and `LC_CTYPE` and set their value to `en_US.UTF-8`. However it didn't help me. Then I also realized that either on Linux or Windows creating such system variables hadn't helped some other users too.

Then I just opened the `_config.yml` with Notepad++, changed the encoding to `UTF-8 without BOM`. As I changed the encoding, the `ş` character corrupted. I fixed it and saved the file. I got no error when I run the `rake generate` command this time. 

This solution also works for the post files (the ones with `.markdown` extensions in `source/_posts` folder). In short, just change the file's encoding `UTF-8 without BOM` before inserting any non-ascii characters. There is no need for the environment variables in my case.

I hope my first post helps those having the same issue. Please let me know if this works for you too.
