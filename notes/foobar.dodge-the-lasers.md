---
id: zer6szds0we2lk3340ffup2
title: Dodge the Lasers
desc: ''
updated: 1666221838933
created: 1665856307482
tags:
  - python
  - level-5
  - foobar
  - google
---

## Instructions

Oh no! You've managed to escape Commander Lambda's collapsing space station in an escape pod with the rescued bunny workers - but Commander Lambda isnt about to let you get away that easily. Lambda sent an elite fighter pilot squadron after you -- and they've opened fire!

Fortunately, you know something important about the ships trying to shoot you down. Back when you were still Lambda's assistant, the Commander asked you to help program the aiming mechanisms for the starfighters. They undergo rigorous testing procedures, but you were still able to slip in a subtle bug. The software works as a time step simulation: if it is tracking a target that is accelerating away at 45 degrees, the software will consider the targets acceleration to be equal to the square root of 2, adding the calculated result to the targets end velocity at each timestep. However, thanks to your bug, instead of storing the result with proper precision, it will be truncated to an integer before adding the new velocity to your current position.  This means that instead of having your correct position, the targeting software will erringly report your position as `sum(i=1..n, floor(i*sqrt(2)))` - not far enough off to fail Commander Lambdas testing, but enough that it might just save your life.

If you can quickly calculate the target of the starfighters' laser beams to know how far off they'll be, you can trick them into shooting an asteroid, releasing dust, and concealing the rest of your escape.  Write a function solution(str_n) which, given the string representation of an integer n, returns the sum of `(floor(1*sqrt(2)) + floor(2*sqrt(2)) + ... + floor(n*sqrt(2)))` as a string. That is, for every number i in the range 1 to n, it adds up all of the integer portions of `i*sqrt(2)`.

For example, if str_n was "5", the solution would be calculated as
```text
floor(1*sqrt(2)) +
floor(2*sqrt(2)) +
floor(3*sqrt(2)) +
floor(4*sqrt(2)) +
floor(5*sqrt(2))
= 1+2+4+5+7 = 19
```
so the function would return "19".

str_n will be a positive integer between 1 and 10^100, inclusive. Since n can be very large (up to 101 digits!), using just sqrt(2) and a loop won't work. Sometimes, it's easier to take a step back and concentrate not on what you have in front of you, but on what you don't.

### Test cases

Your code should pass the following test cases.

Note that it may also be run against hidden test cases not shown here.

Input: `solution.solution('77')`

Output: `4208`

Input: `solution.solution('5')`

Output: `19`

## Solution

Given infinite time and resources, the following would work perfectly:

```py
from math import sqrt, floor

def solution(str_n):
    n = int(str_n)
    mod = sqrt(2)
    return str(sum([int(floor(x * mod)) for x in range(n + 1)]))

# Test cases
print(solution("5")) # 19
print(solution("77")) # 4208
```

However, this is not the case. The test cases are very large, and the time limit is very short. We need to find a way to optimize this.

After doing some research (I am not yet very well-versed in mathematics), I was able to finalize the following solution:

```py
from decimal import Decimal, localcontext

# https://towardsdatascience.com/dodge-the-lasers-fantastic-question-from-googles-hiring-challenge-72363d95fec
def solution(str_n):
    n = Decimal(str_n)
    with localcontext() as ctx:
        ctx.prec = 101
        r = Decimal(2).sqrt()
        s = 2 + r

        # https://en.wikipedia.org/wiki/Beatty_sequence
        def solve(n):
            if n == 0: return 0

            # B = Beatty sequence
            # r = any irrational number greater than 1 (in our case, sqrt(2))
            # n = any positive integer (in our case, the input)
            # s = 2 + sqrt(2)
            Br_n = int(r * n)
            Br_n_s = int(Decimal(Br_n) / s)

            # https://oeis.org/A001951
            return (Br_n * (Br_n + 1)) / 2 - solve(Br_n_s) - Br_n_s * (Br_n_s + 1)

        return str(int(solve(n)))

# Test cases
print(solution("5")) # 19
print(solution("77")) # 4208
```
