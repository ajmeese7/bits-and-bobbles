---
id: i2pdplguy2iuvx8f08vdzy4
title: 'Number Zoo Patrol'
desc: ''
updated: 1664741857067
created: 1591710300000
tags:
  - php
  - javascript
  - coffeescript
  - 6-kyu
  - codewars
  - answer
---

### PHP

```php
function find_number(array $a): int {
  sort($a);
  $len = count($a);

  for ($i = 1; $i <= $len; $i++) {
    if ($i - 1 != $a[$i - 1] - 1) {
      return $i;
    }
  }

  return $len + 1;
}
```

### JavaScript

```js
function findNumber(array) {
  if (array.length == 0) return 1;
  let arraySum = array.reduce((sum, val) => sum + val);
  return ((array.length + 1) * (array.length + 2) / 2) - arraySum;
}
```

### CoffeeScript

```coffee
findNumber = (array) ->
  if array.length == 0
    return 1;
  arraySum = array.reduce((sum, val) => sum + val);
  return ((array.length + 1) * (array.length + 2) / 2) - arraySum;
```
