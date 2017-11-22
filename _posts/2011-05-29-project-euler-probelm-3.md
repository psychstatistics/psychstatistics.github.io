---
layout: post
title: 'Project Euler - Probelm #3'
date: 2011-05-29 14:53:23.000000000 -06:00
tags: [python, project euler]
comments: true
---
## Problem Description

The prime factors of 13195 are 5, 7, 13 and 29. What is the largest prime factor of the number 600851475143?

## Python Solution

I started trying to solve this problem by writing a function for identifying prime numbers. I found an entry on Wikipedia for the "<a href="http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes">Sieve of Eratosthenes</a>." The entry also included Python code for implementing the sieve. I've reproduced an adapted version of the Wikipedia code. I had to change it because my computer ran out of memory when creating the candidate list. I had to change it so the candidate list had an upper limit of the square root of 600851475143. In any case, here is the solution with the sieve function first and then a function for actually solving the problem.

	def sieve(n): 
	    fin = int(n**0.5) ##candidates below sqrt of n -- this is the upper limit
	    candidates = list(range(fin+1)) ##This is an change of the wiki code
	
	    # Loop over the candidates, marking out each multiple.
	    for i in xrange(2, fin+1): 
	        if candidates[i]:
	            candidates[2*i::i] = [None] * (fin//i - 1) 
	            ##the previous line replaces all multiples of i with None
	
	    # Filter out non-primes and return the list.
	    return [i for i in candidates[2:] if i]

##A function for returning prime factors of n
	def largeprime(n):
	    for i in sieve(n):
	        if n % i == 0:
	            yield i

##Return the prime factors as a list and print the last number

	div = list(largeprime(n))
	print div[-1]

This solution takes .38 seconds.
