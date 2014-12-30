---
layout: post
title: 'Project Euler - Problem #1'
date: 2011-05-24 03:24:37.000000000 -06:00
tags: [python, project euler]
comments: true
---
## Problem Description

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23. Find the sum of all the multiples of 3 or 5 below 1000.

## Python Solution #1

This uses the built in `range()` function to get all multiples of three and five. The problem with this solution is that there is going to be overlap between the values in three and five lists. Consequently, we have to put them in a common list (using `extend()`) and identify the unique values with the `set()` function. I also sorted them because I like it better that way.

	answer =[] # empty list
	three = range(0,1000,3) #list of multiples of 3
	five = range(0,1000,5) #list of multiples of 5
	answer.extend(three) # add three to the answer list
	answer.extend(five) #add five to the answer list
	answer.sort() #sort the list
	print sum(set(answer)) #print the sum of the unique values

## Python Solution #2

This solution uses a `for` loop and take advantage of the mod operator in python -- `%` -- to identify values between 0 and 1000 that are divisible by 3 or 5 (i.e., have a mod equal to 0).
	
	answer2 = [] #empty list
	for i in range(1000): #iterate from 0 to 999 -- 1000 isn't included
    	if i % 3 == 0 or i % 5 == 0: #identify whether i is divisible by 3 or 5
        	answer2.append(i) #if divisible, then append it to the answer2 list
	print sum(answer2) #print the sum of answer 2

This will produce the correct answer. It is a bit slower than Solution #1 but both are very fast.
