
### JavaScript

```js
const decodeBits = (bits) => {
  // Removes any leading zeros
  bits = bits.substring(bits.indexOf("1"));

  // Removes any trailing zeros (after last occurance of '1')
  bits = bits.substring(0, bits.lastIndexOf("1") + 1);

  // To detect the transmission rate
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

      if (count < minCount)
        minCount = count;

      count = 1;
    }

    previousChar = currentChar;
  }

  // Fix last char issues with the loop
  if (count == 1) minCount = 1;

  let doubleBits = "";
  for (let i = 0; i < bits.length; i += minCount)
    doubleBits += bits[i];

  if (allCharactersSame(bits))
    doubleBits = doubleBits.charAt(0);

  const decodedBits = doubleBits
    .replace(/111/g, '-')
    .replace(/1/g, '.')
    .replace(/0000000/g, '   ')
    .replace(/000/g, ' ')
    .replace(/0/g, '');

  return decodedBits;
}

function allCharactersSame(str) {
  for (let i = 1; i < str.length; i++)
    if (str.charAt(i) != str.charAt(0))
      return false;

  return true;
}

const decodeMorse = (morseCode) => {
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
