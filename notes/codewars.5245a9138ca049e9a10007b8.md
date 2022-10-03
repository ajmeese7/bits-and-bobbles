---
id: 763uttfx5zzxx4z1n4or9bt
title: 'Adjacent repeated words in a string'
desc: ''
updated: 1664742031950
created: 1591636020000
tags:
  - javascript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function countAdjacentPairs(searchString) {
  let words = searchString.split(' ').map(word => word.toLowerCase());
  let count = 0, lastMatch = '';
  while (words.length > 1) {
    var bool = false;
    if (words[0].localeCompare(words[1]) == 0 && words[0].localeCompare(lastMatch) != 0) {
      lastMatch = words[0];
      bool = true;

      count++;
      words.shift();
    }

    if (!bool) lastMatch = words[0];
    words.shift();
  }

  return count;
}
```
