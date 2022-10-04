---
id: 72rg8r9g22vu3r1c27f9n49
title: '4'
desc: ''
updated: 1664914952307
created: 1507914720000
tags:
  - java
  - euler-difficulty-5
  - hackerrank-medium
  - hackerrank
  - euler
---

> This is the HackerRank version of [Euler Project problem #4](https://www.hackerrank.com/contests/projecteuler/challenges/euler004/problem).

### Problem

A palindromic number reads the same both ways. The largest palindrome made from the product of two 3-digit numbers is 101101 = 143 × 707.

Find the largest palindrome made from the product of two 3-digit numbers which is less than N.

#### Input Format

First line contains T that denotes the number of test cases. This is followed by T lines, each containing an integer, N.

#### Constraints

- 1 <= T <= 100
- 101101 < N < 1000000

#### Output Format

Print the required answer for each test case in a new line.

### Solution

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Problem4 {
  public static final int NUM = 3;

  public static void main(String[] args) {
    Scanner in = new Scanner(System.in);
    int t = in.nextInt();
    for (int a0 = 0; a0 < t; a0++) {
      int n = in.nextInt();
      String nines = "9";
      String small = "1";
      for (int i = 1; i < NUM; i++) {
        nines += "9";
        small += "0";
      }

      int numOne = Integer.parseInt(nines);
      int numTwo = numOne;
      int minNum = Integer.parseInt(small);
      int largestPalindrome = 0;

      while (numOne >= minNum) {
        while (numTwo >= minNum) {
          int temp = numOne * numTwo;
          if (isPalindrome(temp) && temp > largestPalindrome && temp < n) {
            largestPalindrome = temp;
          } else if (temp <= largestPalindrome) {
            break;
          }

          numTwo--;
        }

        numOne--;
        numTwo = numOne;
      }

      System.out.println(largestPalindrome);
    }
  }


  public static boolean isPalindrome(int number) {
    return String.valueOf(number).equals(new StringBuilder(String.valueOf(number)).reverse().toString());
  }
}
```
