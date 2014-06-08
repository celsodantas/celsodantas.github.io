---
layout: post
title: "OpenGL deprecated newbie functions =("
date: 2014-06-07 12:00
comments: true
categories: 3d-dev
---

A few days ago a decided to develop a game as an excuse to improve my C++ skills, learn more how to use a Makefile and play with 3D graphics. As I'm on a Mac, I choose to use OpenGL 4.1. I had a litle bit of experience on OpengGL 3.1, but since OpenGL 3.3, a lot of things changed. Now, it requires a lot more core to have a simple 3D element on the screen (like VAO, VBO, shaders).

Now, in **OpenGL 4.1**, there's **no more default shaders**, so for now on, you need to load your own *vertex* and *fragment* shader. Also, there's no more `glTranslate`, `glPushMatrix`. All vectors manipulation (translate, rotate and scale) now needs to be done by your shader. This took me to had to back and refresh my memory (and study) and few mathematics stuff before going back to the code.

<!-- more -->

I had to study/refresh:

  - Linear transformations (to understand how to rotate, scale and translate a 3D point using Matrixes)
  - Complex numbers (to understand Quaternions)
  - Quaternions
  - Euler Angles

### Quaternions and Euler Angles

A short version: You can rotate anything in 3D space with Matrixes, Quaternions and with Euler Angles. Each has it's own pros and cons. You can do everything with Matrixes, if you whish. But sometimes using Quaternions or Euler Angles is easy to solve a specific problem.

I'll explaing with more details what I found in a later post.


Here is a list of the [removed functions from OpenGL](https://docs.google.com/spreadsheet/ccc?key=0At5QLa2ZAYZBdHFLbEtvOHF5S1NobWJFbmpDUHZSWWc&usp=sharing#gid=0).