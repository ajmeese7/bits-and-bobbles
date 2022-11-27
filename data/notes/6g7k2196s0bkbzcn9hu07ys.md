
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
