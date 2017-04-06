---
title: "Debuggin in C"
subtitle: "Keep It Simple Sir"
date: 2017-4-6 8:51:32
author: "Nischal Lal Shrestha"
categories: post
header-image: "sample-post.png"
permalink: /2017/4/6/Debugging-in-c
layout: post
---
# Dare To Debug

C programmers are great inventors of our times. However, there are is no shortage of horror stories about programs that took twenty times to " debug " as they did to "Write". Many a time programs had to be rewritten all over again because the bugs present in them could not be located. Bugs are C programmer's birththright. But how do we chase them away. No sure-shot way for that. I thought if I make a list of more common programming mistakes, it might be a help. They are not arranged in any particular order. But as you realize, surely a great help!
	
-
[1] Omitting ampersand before the variables using in scanf().
For example:
		
		int choice;
		
		scanf("%d",choice);
		
Here, the & i.e ampersand is missing.
		
Another common mistakes with scanf() is to give blanks either just before the format string or immediately after the format string as in;
		
		int choice;
		
		scanf(" %d ",%choice);
		
Note that it is not a mistake but till you are not going to understand scanf() it will trouble you. Safety is in avoiding the blanks.

[2] Using the operator = instead of the operator ==.
Note that = is used for assignmet while == is used for equality. In C equal to is not equal to equal to.
for eg;
		int i=10;
		
		while(i=10)
		
		{
			printf("got to get out");
			i++;

		}
		
Here the while loop become an infinite loop since every time, instead of checking the value of i against 10, it assigns
the value 10 to i. As 10 is a non zero value the will be always true.

[3] Ending a loop with a semicolon.Observes the following program;

	int j=1;
	while(j<=10);
	j++;

Here, inadverently, we have fallen in an indefinite  loop. Cause is the semicolon after the while loop.
the semicolon is treated as the null statement by the compiler as shown below

	while(j<=10)
		;
		
This is an indefinite loop,since the null statement keeps getting executed indefinitely as j never gets the increament.