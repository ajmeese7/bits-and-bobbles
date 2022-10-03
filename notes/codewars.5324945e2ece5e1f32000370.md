---
id: ctjkc4rb461797wkmyi0opf
title: 'Sum Strings as Numbers'
desc: ''
updated: 1664743216274
created: 1590760800000
tags:
  - javascript
  - php
  - 4-kyu
  - codewars
  - answer
---

### JavaScript

```js
function sumStrings(x, y) {
  let sum = "";
  let len;
  const lenx = x.length;
  const leny = y.length;
  let x1, y1, rem, div = 0;

  if (lenx > leny) len = lenx;
  else len = leny;

  for (var i = 0; i < len; i++) {
    if (i >= lenx) x1  = 0;
    else x1 = parseInt(x[lenx - i - 1]);
    if (i >= leny) y1 = 0;
    else y1 = parseInt(y[leny - i - 1]);
    rem = (x1 + y1 + div) % 10;
    div = Math.floor((x1 + y1 + div) / 10);
    sum = rem + sum;
  }

  if (div > 0) sum = div + sum;
  if (sum.charAt(0) == 0) sum = sum.substring(1);

  return sum;
}
```

### PHP

```php
function sum_strings($a, $b) {
  return (float)$a + (float)$b;
}
```
