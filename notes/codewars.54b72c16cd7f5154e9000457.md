---
id: 8fspf1e3hhmepmt94qp2mxo
title: 'Decode the Morse code, advanced'
desc: ''
updated: 1664743600947
created: 1590752040000
tags:
  - javascript
  - 4-kyu
  - codewars
  - answer
---

### JavaScript

```js
var decodeBits = function(bits) {
  // Removes any leading zeros
  const firstOne = bits.indexOf("1");
  bits = bits.substring(firstOne);

  // Removes any trailing zeros (after last occurance of '1')
  const lastOne = bits.lastIndexOf("1") + 1;
  bits = bits.substring(0, lastOne);

  // To detect the transmission rate [in theory]
  let count = 1,
    minCount = 1,
    maxCount = 1,
    previousChar = '',
    firstRun = true;

  for (let i = 0; i < bits.length; i++) {
    const currentChar = bits[i];
    if (currentChar == previousChar) {
      count++;
    } else {
      if (count > maxCount) {
        if (firstRun) {
          minCount = count;
          firstRun = false;
        }

        maxCount = count;
      }

      if (count < minCount) {
        minCount = count;
      }
      count = 1;
    }

    previousChar = currentChar;
  }

  // Fix last char issues with the loop
  if (count == 1) minCount = 1;

  let doubleBits = "";
  for (let i = 0; i < bits.length; i += minCount) {
    doubleBits += bits[i];
  }

  if (allCharactersSame(bits)) doubleBits = doubleBits.charAt(0);

  // Use custom function to replace all, because I don't know of
  // a better way to do it
  let decodedBits = doubleBits.replaceAll('111', '-');
  decodedBits = decodedBits.replaceAll('1', '.');
  decodedBits = decodedBits.replaceAll('0000000', '   ');
  decodedBits = decodedBits.replaceAll('000', ' ');
  decodedBits = decodedBits.replaceAll('0', '');

  return decodedBits;
}

String.prototype.replaceAll = function(search, replacement) {
  const target = this;
  return target.replace(new RegExp(search, 'g'), replacement);
};

function allCharactersSame(str) {
  for (let i = 1; i < str.length; i++) {
    if (str.charAt(i) != str.charAt(0)) {
      return false;
    }
  }

  return true;
}

var decodeMorse = function(morseCode) {
  let decodedString = "";
  const morseChars = morseCode.replace(/  /g, ' ').split(' ');

  for (let i = 0; i < morseChars.length; i++) {
    var currentChar = MORSE_CODE[morseChars[i]];
    if (!currentChar) currentChar = " ";

    decodedString += currentChar;
  }

  return decodedString;
}
```
