---
id: r1g4lhlgy50ztyjjh993zvi
title: 'Two to One'
desc: ''
updated: 1664743712842
created: 1590684240000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
function longest(s1, s2) {
  let uniqueString = "";
  const uniqueLetter = (letter) => !uniqueString.includes(letter);

  function includeString(str) {
    for (let i = 0; i < str.length; i++) {
      const currentChar = str.charAt(i);
      if (uniqueLetter(currentChar)) {
        uniqueString += currentChar;
      }
    }
  }

  includeString(s1);
  includeString(s2);

  return sortString(uniqueString);
}

function sortString(str) {
  const arr = str.split('');
  const sorted = arr.sort();
  return sorted.join('');
}
```
