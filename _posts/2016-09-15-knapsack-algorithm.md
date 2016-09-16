---
title: Knapsack Algorithm
---
Hi, It is my first blog post about Knapsack Algorithm.

### Let's Start
What is it? **The Knapsack Algorithm (Knap)** is piece of Cambinatoric and Dynamic Programming.

Firstly, let me explain about knapsack, the main problem of Knapsack is, given a set of items, each with a weight and
a value, determine the number of each item to include in a collection so that the total weight is less than or equal
to a given limit and the total value is as large as possible. It derives its name from the problem faced by someone
who is constrained by a fixed-size knapsack and must fill it with the most valuable items.
		 
May be you have question,how is it related to combinatoric, so the answer is, we should generate all
items that we can put in our Knap, that total weight of this 
items will not reach the max weigth of KNAP, but If we will do it with brute force (stupid code) the complexcity will very big. 
(I think, This part is clear 😄)

However, we can use dynamic programming, that optimize our stupid code. How we will do it.

**Look on this image**👇👇👇
![knapsack Table](/atukenov.github.io/img/knapsack.png "Table")
We will write same algorithm like this table.

*PseudoCode*👇👇👇
{% highlight c++ linenos %}
	//struct array with two declarations: Weight & Cost Array[]
	//array for dynamic D[];
	//it is base of our dynamic solving, because we can always take with you 0 weight (0 items)
	was[0] = true; 
	D[0] = 0;
	for (int i = 1; i <= n; ++i)
		for (int j = maxCapasity of KNAPSACK; j >= 0; --j)
		{
			// checking did we get some item with weight j
			if (was[j])
			{
				was[j + Array[i].Weight] = true; // So we adding the new item to our initial KNAP
				// we adding cost that should be max
				D[j + Array[i].Weight] = max(D[j + Array[i].Weight], D[j] + Array[i].Cost); 
			}
		}
		//answer will the max cost in all D array
	
{% endhighlight %}

So you can check yourself in this [problem](https://www.hackerrank.com/challenges/unbounded-knapsack). The problem is a little bit 😈 different 😈, but you can found using logic 😉 (*Hint:* can use one item many times)) Good Luck!!!
