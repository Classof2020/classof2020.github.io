---
title: "Debuggin in C"
subtitle: "Keep It Simple Sir"
date: 2017-4-6 8:51:32
author: "Nischal Lal Shrestha"
categories: post
header-img: 
permalink: /2017/4/6/Debugging-in-c
layout: post
---
# Dare To Debug

C programmers are great inventors of our times. However, there are is no shortage of horror stories about programs that took twenty times to **DEBUG** as they did to **WRITE**. Many a time programs had to be rewritten all over again because the bugs present in them could not be located. Bugs are C programmer's birththright. But how do we chase them away. No sure-shot way for that. I thought if I make a list of more common programming mistakes, it might be a help. They are not arranged in any particular order. But as you realize, surely a great help!
	
	
	
[1] Omitting ampersand(**&**) before the variables using in scanf().
For example:
		
		int choice;
		
		scanf("%d",choice);
		
Here, the **&** i.e ampersand is missing.
		
Another common mistakes with scanf() is to give blanks either just before the format string or immediately after the format string as in;
		
		int choice;
		
		scanf(" %d ",%choice);
		
Note that it is not a mistake but till you are not going to understand scanf() it will trouble you. Safety is in avoiding the blanks.

[2] Using the operator **=** instead of the operator **==**.
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

[4] Using **continue** in a **switch**. It is a common error to believe that the way the keyword break is used with loops and a **switch**; similarly
the keyword **continue** can also be used with them. Remember that continue works only with loops, never with **switch**.

[5] Forgetting the bound of an array.
Note in C we don't have bound checking so it is upto you how you deal with this.
	
	int num[50], i;
	
	for(i = 0; i <= 50; ++i)
		
		num[i] = i * i;
		
Here, in the array num, there is no such element as num[50], since array counting begins with 0 and not 1. 
Compiler would not give a warining if our program exceeds the bounds. If no taken care of, in extremes cases, the above code might even hang the computer.



# Always Remember


<blockquote> 

Programming is not about being clever and obscure -- it's about how clearly your program communictate it's purpose.</blockquote>

<blockquote> Code conciseness is much more less important than code readability. </blockquote>


<blockquote> Reduction in program size necessarily doesn't mean reduction in meaning for the next programmers. </blockquote>

<blockquote> Any person can write the program which computer can understad, but real programmer write program which human can understand.

</blockquote>

# Note

If you found similar contents in the book Let Us C, page 638 -644, It is a pure accident.

Looking for C examples	[Visit Novice Programmers](https://www.aakrist.me)