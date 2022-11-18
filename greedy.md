## Revisiting Two-sum

-   Given an array a, find the indices of two elements such that their sum is x.

Lets look at the $O(n^2)$ solution:

```
a = [1, 3, 4, 5]
x = 9

n = len(a) # len(array) = length of the array

for i in range(n): # choosing our first index i
	for j in range(n): # choosing second index j
	
		if a[i] + a[j] == x: # the same condition above
			print(i, j)

```

Lets rewrite this condition: $a_i+a_j=x$ --> $a_j=x-a_i$ 
We know the expected value of $a_j$ so we can search for it with binary search:

```
def search(a, x): # defines a function

	n = len(a)  
	left = 0
	right = n-1

	found = False # we want to know if we found the element
	
	while left < right:
		mid = (left + right) // 2 # // means floor division
		
		if a[mid] == x:
			found = True
			break
		
		elif a[mid] > x:
			right = mid
		else:
			left = mid + 1

	return found # returns either true or false, whether the element x was found in array a

```

```
a = [1, 3, 4, 5]
x = 9

n = len(a) # len(array) = length of the array

for i in range(n): # choosing our first index i
	a_j = x - a[i]
	if search(a, a_j) == True: # if found a_j
		print("Found")
```

## Problem 1 - Binary search

Key idea: We can apply binary search to find the start and end indices of each query. We binary search the index of integer A and integer B. Then, the question asks us to get the difference between the indices

```
from bisect import bisect_left, bisect_right # python's built in binary search functions


bale_num, query_num = 4, 6

a = [3, 2, 7, 5]

haybales = sorted(a)

ans = []

for _ in range(query_num):

	start, end = [int(i) for i in read.readline().split()] # reads in the queries from python input

	left = bisect_left(haybales, start) # gets the greatest element less than or equal to start

	right = bisect_right(haybales, end) # gets the least element greater or equal to start

	print(right - left)

```

## Greedy algorithms

-   Chooses the locally optimal value
-   Uses heuristics (predefined rules) to solve a problem
-   Typically require some insight

## Coin problem

-   Given the coins {1c, 5c, 10c, 50c, 100c} and a value x cents, what is the least number of coins that we need to make the value x?
-   E.g. x = 101 cents --> coins = {100c + 1c}
-   Challenge: can this method work for all coins? How would you implement such an algorithm?

Why does this work for these coins?

A simple greedy algorithm to the problem always selects the largest possible coin, until the required sum of money has been constructed. 

The correctness of the algorithm can be shown as follows: 

First, each coin 1, 5, 10, 50 and 100 appears at most once in an optimal solution, because if the solution would contain two such coins, we could replace 57 them by one coin and obtain a better solution. 

We notice that each coin's value is divisible by the previous coin, and all coins are divisble by 1. Lets represent coins $c$ and $d=5c$. If a value $x$ can be made with $d$ and it can be made with $c$, we will always choose $d$ first as it covers the same a larger *value* with a lower number of *coins*. This is the case for each of 1, 5, ..., 100 so this algorithm is optimal

Implementation:

```

x = 104
coins = [100, 50, 10, 5, 1]
total_coins_used = 0

for coin in coins:
	if coin >= x:
		total_coins_used += (x // coin)
		x %= coin # get the remainder after dividing by a coin value

print(total_coins_used)

```

## Problemset

[https://codeforces.com/contest/1698/problem/B](https://codeforces.com/contest/1698/problem/B) - Greedy
https://codeforces.com/contest/1754/problem/A - Greedy
http://www.usaco.org/index.php?page=viewproblem2&cpid=835 - Greedy + sorting
http://www.usaco.org/index.php?page=viewproblem2&cpid=858 - Binary search
http://www.usaco.org/index.php?page=viewproblem2&cpid=966 - Binary search
