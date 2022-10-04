---
id: b06idxnaskoer9xwkrgdhol
title: 'Largest prime factor'
desc: ''
updated: 1664914966724
created: 1507603440000
tags:
  - java
  - euler-difficulty-5
  - hackerrank-easy
  - hackerrank
  - euler
---

> This is the HackerRank version of [Euler Project problem #3](https://www.hackerrank.com/contests/projecteuler/challenges/euler003/problem).

### Problem

The prime factors of 13195 are 5, 7, 13 and 29.

What is the largest prime factor of a given number N?

#### Input Format

First line contains T that denotes the number of test cases. This is followed by T lines, each containing an integer, N.

#### Constraints

- 1 <= T <= 10
- 10 <= N <= 10^12

#### Output Format

For each test case, display the largest prime factor of N.

### Solution

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Problem3 {
  public static void main(String[] args) {
    Scanner in = new Scanner(System.in);
    int t = in.nextInt();
    for (int a0 = 0; a0 < t; a0++) {
      long n = in.nextLong();
      int factor = 2;
      int lastFactor = 1;

      if (n % 2 == 0) {
        lastFactor = 2;
        n /= 2;

        while (n % 2 == 0) {
          n /= 2;
        }
      }

      factor = 3;
      double maxFactor = Math.sqrt(n);
      while (n > 1 && factor <= maxFactor) {
        if (n % factor == 0) {
          n /= factor;
          lastFactor = factor;

          while (n % factor == 0) {
            n /= factor;
          }

          maxFactor = Math.sqrt(n);
        }

        factor += 2;
      }

      System.out.println(n == 1 ? lastFactor : n);
    }
  }
}
```
