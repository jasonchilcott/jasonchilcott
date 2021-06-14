---
layout: page
title:  "Watchmatch"
date:   2021-06-14 16:07:00 -0600
categories: project
---



Created as a final project for Flatiron School Software Engineering bootcamp, and continuing to be worked on and improved, to continue learning.

WATCHMATCH is a webapp which matches users based on how they rate movies. Users can rate movies on a scale from 1/2 star to 5 stars. The ratings of all movies any two users have both rated are compared to each other on a weighted algorithmic scale and then averaged to find a maximum possible compatibility percentage of the users' tastes. In addition, the percentage is adjusted by a margin of error based on how many rated movies the users have in common. This method was inspired by the algorithm used on OKCupid. [Inside OKCupid: The math of online dating](https://www.ted.com/talks/christian_rudder_inside_okcupid_the_math_of_online_dating/transcript?language=en)

The weighted difference for any two users' ratings of the same movie are calculated as follows:

![image](/assets/img/weighted-difference.png)