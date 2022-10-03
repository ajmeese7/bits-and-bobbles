---
id: kb1yvjujmo8vju0oogc2j3p
title: 'Isograms'
desc: ''
updated: 1664743449704
created: 1590756060000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
function isIsogram(str) {
  let existingChars = "";
  str = str.toLowerCase();

  const chars = str.split("");
  for (let i = 0; i < chars.length; i++) {
    const currentChar = chars[i];
    if (existingChars.includes(currentChar)) {
      return false;
    } else {
      existingChars += currentChar;
    }
  }

  return true;
}
```
