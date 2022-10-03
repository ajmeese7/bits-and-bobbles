---
id: z1nurvpvflxoyis42b4epth
title: 'Jaden Casing Strings'
desc: ''
updated: 1664742703336
created: 1591096860000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
String.prototype.toJadenCase = function () {
  var words = this.split(' ');
  words.forEach(function(word, index) {
    words[index] = word.charAt(0).toUpperCase() + word.slice(1);
  });

  return words.join(' ');
};
```
