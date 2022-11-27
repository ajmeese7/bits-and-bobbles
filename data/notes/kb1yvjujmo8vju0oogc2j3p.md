
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
