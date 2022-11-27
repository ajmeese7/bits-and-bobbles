
> This is the HackerRank version of [Euler Project problem #5](https://www.hackerrank.com/contests/projecteuler/challenges/euler005/problem).

### Problem

2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.

What is the smallest positive number that is evenly divisible by all of the numbers from 1 to N?

#### Input Format

First line contains T that denotes the number of test cases. This is followed by T lines, each containing an integer, N.

#### Constraints

- 1 <= T <= 10
- 1 <= N <= 40

#### Output Format

Print the required answer for each test case.

### Solution

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Problem5 {
  public static void main(String[] args) {
    Scanner in = new Scanner(System.in);
    int t = in.nextInt();
    for (int a0 = 0; a0 < t; a0++) {
      int n = in.nextInt();
      System.out.println(LCM(n));
    }
  }

  // Least Common Multiple
  public static long LCM(long n) {
    long answer = 1;

    for (long i = 1; i <= n; i++) {
      answer *= i / GCD(i, answer);
    }

    return answer;
  }

  // Greatest Common Divisor
  public static long GCD(long a, long b) {
    while (b != 0) {
      long temp = a;
      a = b;
      b = temp % b;
    }

    return a;
  }
}
```
