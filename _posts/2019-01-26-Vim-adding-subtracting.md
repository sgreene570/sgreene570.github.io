---
layout: post
title:  "Adding & Subtracting in Vim"
date:   2019-01-26 15:08:40 -0600
categories: jekyll update
---

Using `cntrl + a` and `cntrl + x` in vim normal mode, you can increment or decrement any integer with wrapping.
For example, if you had `9` somewhere in your text file, pressing `cntrl + a` with your cursor over 9 in normal mode
will change `9` to `10`.
<br>
But wait, there's more.
<br>
Vim repetitions allow for any integer to be added to any number by running `cntrl + a` n times.
For example, typing `15 cntrl + a` will add 15 to any currently highlighted integer.  This is very useful.
<br>
But wait, there's even more.
<br>
Vim supports binary and hexidecimal integers with the `0b` and `0x` prefix.
Using vim reptitions, you can automatically add any integer value to any binary or hexidecimal value
without having to do any manual conversions.  For example, `14 cntrl + a` on `0xf` will produce `0x1d`.
How cool is that?  Your favorite text editor is also a binary calculator.

