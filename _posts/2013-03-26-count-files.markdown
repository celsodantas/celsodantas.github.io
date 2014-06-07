---
layout: post
title: "Counting files within folder (sub-folder). Shell or Ruby?"
date: 2013-03-26 12:26
comments: true
categories: ruby code 
---

I was trying to count how many `.java` I had in one specific project. At first I tried using shell commands to do it but I find that I could do a easier task with Ruby.

``` ruby
Dir["/Users/celsodantas/code/java/src/**/*.java"].count
```
There we go. It will go through all sub-folders and return an array of all files. For me it's easier to remember this then a command shell command like:

    find . -type f | wc -l

Some people might find easier to go with shell. I'm lazy and tend to go with what I remember more quick. Feel free to chose what you feel more comfortable. 

cheers!