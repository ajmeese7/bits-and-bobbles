---
id: scqle32spaa3z6se1k511pj
title: 'Halving Sum'
desc: ''
updated: 1664741694622
created: 1591729200000
tags:
  - java
  - python
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### Java

```java
public class HalvingSum {
  int halvingSum(int n) {
    int sum = 0;
    for (int i = 1; i <= n; i *= 2) {
      sum += n / i;
    }

    return sum;
  }
}
```

### Python

```py
def halving_sum(n):
    i, sum = 1, 0
    while i <= n:
        sum += int(n / i)
        i *= 2;
    return sum
```

### JavaScript

```js
function halvingSum(n) {
  let i = 1, sum = 0
  while (i <= n) {
    sum += parseInt(n / i)
    i *= 2
  }

  return sum
}
```
