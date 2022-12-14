---
id: djalt7pjrmul76fa6lsjg8r
title: Please Pass the Coded Messages
desc: ''
updated: 1665094883443
created: 1665093780392
tags:
  - foobar
  - google
  - python
  - level-2
---

## Instructions

You need to pass a message to the bunny workers, but to avoid detection, the code you agreed to use is... obscure, to say the least. The bunnies are given food on standard-issue plates that are stamped with the numbers 0-9 for easier sorting, and you need to combine sets of plates to create the numbers in the code. The signal that a number is part of the code is that it is divisible by 3. You can do smaller numbers like 15 and 45 easily, but bigger numbers like 144 and 414 are a little trickier. Write a program to help yourself quickly create large numbers for use in the code, given a limited number of plates to work with.

You have L, a list containing some digits (0 to 9). Write a function solution(L) which finds the largest number that can be made from some or all of these digits and is divisible by 3. If it is not possible to make such a number, return 0 as the solution. L will contain anywhere from 1 to 9 digits.  The same digit may appear multiple times in the list, but each element in the list may only be used once.

### Languages

To provide a Java solution, edit `Solution.java`

To provide a Python solution, edit `solution.py`

### Test cases

Your code should pass the following test cases.
Note that it may also be run against hidden test cases not shown here.

-- Java cases --

Input:
`Solution.solution({3, 1, 4, 1})`
Output:
    `4311`

Input:
`Solution.solution({3, 1, 4, 1, 5, 9})`

Output:
    `94311`

-- Python cases --

Input:
`solution.solution([3, 1, 4, 1])`

Output:
    `4311`

Input:
`solution.solution([3, 1, 4, 1, 5, 9])`

Output:
    `94311`

Use `verify [file]` to test your solution and see how it does. When you are finished editing your code, use `submit [file]` to submit your answer. If your solution passes the test cases, it will be removed from your home folder.

### Python

```py
import itertools

def solution(nums):
    for i in range(len(nums), 1, -1):
        # Get all possible arrays that can be made from the given array
        combinations = itertools.permutations(nums, i)

        # Combine each array into a single number
        combinations = [int(''.join(map(str, combination))) for combination in combinations]

        # Filter to only those that are divisible by 3
        divisible_by_3 = list(filter(lambda x: x % 3 == 0, combinations))

        # If there are any, return the largest
        if divisible_by_3:
            return max(divisible_by_3)

    return 0

# Test cases
print(solution([3, 1, 4, 1])) # 4311
print(solution([3, 1, 4, 1, 5, 9])) # 94311
```
