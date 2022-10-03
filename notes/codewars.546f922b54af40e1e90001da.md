---
id: gpveyz4xco8cncj2dfygn1q
title: 'Replace With Alphabet Position'
desc: ''
updated: 1664742598853
created: 1591107360000
tags:
  - javascript
  - php
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function alphabetPosition(text) {
  var words = text.toLowerCase().split(' ');
  var initialCharCode = 96;

  var positionString = "";
  words.forEach(word => {
    var chars = word.split('');
    chars.forEach(char => {
      var charCode = char.charCodeAt(0) - initialCharCode;
      if (charCode <= 26 && charCode >= 1) {
        positionString += charCode + " ";
      }
    });
  });

  return positionString.trim();
}
```

### PHP

```php
function alphabet_position(string $s): string {
  $upper = strtoupper($s);
  $chars = preg_replace( '/[\W]/', '', $upper);
  $charArray = str_split($chars);
  $alphabetPositions = "";

  for ($i = 0; $i < count($charArray); $i++) {
    if (ord($charArray[$i]) - 64 >= 1)
    $alphabetPositions .= (ord($charArray[$i]) - 64) . " ";
  }

  return trim($alphabetPositions);
}
```
