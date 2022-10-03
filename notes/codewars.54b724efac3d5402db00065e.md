---
id: 6g7k2196s0bkbzcn9hu07ys
title: 'Decode the Morse code'
desc: ''
updated: 1664757278414
created: 1590672480000
tags:
  - javascript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
decodeMorse = function(morseCode) {
  var decodedMessage = "";
  var chars = morseCode.trim().replace(/  /g, ' ').split(' ');

  for (let i = 0; i < chars.length; i++) {
    let currentChar = MORSE_CODE[chars[i]];
    if (!currentChar) currentChar = " ";

    decodedMessage += currentChar;
  }

  return decodedMessage;
}
```
