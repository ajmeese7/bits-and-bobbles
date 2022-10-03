---
id: shxuiy5fwariwdtqwx3o2xm
title: 'Convert string to camel case'
desc: ''
updated: 1664742658415
created: 1591112760000
tags:
  - javascript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function toCamelCase(str) {
  var firstWordCapital = str.charAt(0) == str.charAt(0).toUpperCase();
  var camelCase = "";

  str.split(/[- _]+/).forEach((word, wordIndex) => {
    word.split('').forEach((char, charIndex) => {
      if (wordIndex == 0 && charIndex == 0) {
        camelCase += firstWordCapital ? char.toUpperCase() : char.toLowerCase();
      } else {
        camelCase += charIndex == 0 ? char.toUpperCase() : char.toLowerCase();
      }
    });
  });

  return camelCase;
}
```
