---
id: 0l3o4q0svfg571iwgkuu74b
title: 'Find the missing letter'
desc: ''
updated: 1664743343230
created: 1590757140000
tags:
  - javascript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function findMissingLetter(array) {
  let previousCharCode = '';
  for (let i = 0; i < array.length; i++) {
    const charCode = array[i].charCodeAt(0);
    if (previousCharCode != '' && charCode != previousCharCode + 1) {
      return String.fromCharCode(charCode - 1);
    } else {
      previousCharCode = charCode;
    }
  }

  return ' ';
}
```
