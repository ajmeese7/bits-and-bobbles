---
id: cgt8tktnqdskkhq4xpfd92t
title: 'Even Fibonacci numbers'
desc: ''
updated: 1664914962672
created: 1507601580000
tags:
  - java
  - euler-difficulty-5
  - hackerrank-easy
  - hackerrank
  - euler
---

> This is the HackerRank version of [Euler Project problem #2](https://www.hackerrank.com/contests/projecteuler/challenges/euler002/problem).

### Problem

Each new term in the Fibonacci sequence is generated by adding the previous two terms. By starting with 1 and 2, the first 10 terms will be:

1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...

By considering the terms in the Fibonacci sequence whose values do not exceed N, find the sum of the even-valued terms.

#### Input Format

First line contains T that denotes the number of test cases. This is followed by T lines, each containing an integer, N.

#### Constraints

- 1 <= T <= 10^5
- 1 <= N <= 4 * 10^16

#### Output Format

Print the required answer for each test case.

### Solution

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Problem2 {
  public static void main (String[] args) {
    Scanner in = new Scanner(System.in);
    int t = in.nextInt();
    for (int a0 = 0; a0 < t; a0++) {
      long maxNum = in.nextLong();
      long num = 1;
      long previousNum = 0;
      long total = 0;

      while (num < maxNum) {
        if (num % 2 == 0) {
          total += num;
        }

        long temp = previousNum;
        previousNum = num;
        num += temp;
      }

      System.out.println(total);
    }
  }
}
```
