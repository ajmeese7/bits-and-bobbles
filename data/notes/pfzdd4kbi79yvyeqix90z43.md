
### JavaScript

```js
function longestRepetition(s) {
  if (s.length == 0) return ["", 0];

  let longest = [s.charAt(0), 1];
  let currentCount = 1;
  for (let i = 1; i < s.length; i++) {
    let currentChar = s.charAt(i),
        lastChar = s.charAt(i - 1);
    if (currentChar == lastChar) {
      currentCount++;
      if (currentCount > longest[1])
        longest = [currentChar, currentCount];
    } else {
      currentCount = 1;
    }
  }

  return longest;
}
```
