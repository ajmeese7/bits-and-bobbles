---
id: e9vei5c8fjzdc0vkbwnmc7g
title: 'Disemvowel Trolls'
desc: ''
updated: 1664757421681
created: 1590668040000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
function disemvowel(str) {
  const regex = /[aeiou]/gi;
  str = str.replace(regex, '');

  return str;
}
```
