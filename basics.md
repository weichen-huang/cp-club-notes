## Setup Python
- Python download: https://www.python.org/downloads/
- Python tutorial (to get familiar with syntax): https://www.youtube.com/watch?v=kqtD5dpn9C8

## Time complexity:

- Used to determine the efficiency of an algorithm
- Denoted using O(...)
- Counts the number of operations in an algorithm
- For further information: 
	- MIT OCW Lecture (More rigourous): https://www.youtube.com/watch?v=ZA-tUyM_y7s&t=1528s (If you can understand the part about time complexity, I suggest you watch the entire lecture)
	- Video from "Reducible" (Easier to understand): https://www.youtube.com/watch?v=Q_1M2JaijjQ


## Data structures:

- An array is a list of numbers
- The index of an element in an array is its position in the array

Python syntax (the main programming language for the club):
```
a = [1, 3, 5, 7] # creates an array a

print(a[0]) # prints the 0 + 1 = 1st element in the array
print(a[3]) # prints the 3 + 1 = 4th element in the array
print(a[-1]) # also prints the 4th element in the array

# When the index is negative, it counts the numbers backwards

print(a[-2]) # prints the 3rd element in the array

```

## Operations:

- A for loop repeats a sequence of operations a fixed number of times

Python syntax:

```
# The following for loop prints the numbers 1 through 10

for i in range(1, 10+1):
	print(i) 

```

```

"""
The range() syntax:

The range function takes range(start, end, step)
start - the number to start from
end - the number to end at (the loop will stop once it reaches this number, but not at this number i.e. start, start + 1, ..., end - 1)
step - the number that is added after the loop runs one sequence of operations

"""

# The following example uses the step parameter to print even numbers from 2 through 10

for i in range(2, 10+1, step=2):
	print(i)

```

```
"""
We can also directly loop through all the contents of an array
"""

a = [1, 6, 7, 9]

for element in a:
	print(element)

# prints 1 followed by 6 followed by 7 and 9
```

## Two Sum:

- Given an array of numbers a and an integer target value x, return indices of the two numbers such that they add up to x. 
```    
	Input: a = [2,7,11,15], target = 9
    Output: [0,1]
    Explanation: Because a[0] + a[1] = 9, we return [0, 1].
```

### Solution 1 with $O(n^2)$ time complexity:

- Let $a$ be the array
- To break the problem down: we need to find two array indices $i$ and $j$ (plural of index) such that ```a[i] + a[j] == x```
- To do this, we can check over all values in the array and see if the above condition is true.
- We can use for loops and array indexing to code this

Python:

```

a = [1, 3, 4, 5]
x = 9
n = len(a) # len(array) = length of the array

for i in range(n): # choosing our first index i
	for j in range(n): # choosing second index j
		if a[i] + a[j] == x: # the same condition above
			print(i, j)

```


## Binary search:

Toy problem: Given a sorted array a and a target value x, check if x is in the array a.

Naive solution with $O(n)$ complexity: Run a for loop over the entire array and check if the value matches x

Binary search leverages an observation about sorted arrays. Lets choose to check if the middle element of the array is the target value first.

Example:

```a = [1, 3, 5, 8, 11], x = 3```

Notice that since the array is sorted, if x is less than the middle element then all elements to the right of the middle element (i.e. have a greater index) cannot be equal to x. 

Similarly, if x is greater than the middle element, we know that all elements with a lower index (on the left) cannot equal x.

We can repeat this operation:

```
[1, 3, 5, 8 11]

# 3 < 5 so the search space becomes

[1, 3]

# 3 > 1 so the search space becomes

[3]

# 3 = 3 so the element is found :D

```

Notice that at each iteration, the number of elements we have to search for is divided by 2. Therefore we have $2^x = n$ where the number of operations = x. Thus the time complexity is $O(log_{2}(n)) = O(log(n))$
