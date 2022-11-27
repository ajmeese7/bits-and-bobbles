
### JavaScript

```js
const encryptThis = (text) => {
  let words = text.split(" ");

  for (let i = 0; i < words.length; i++) {
    let word = words[i];
    if (word.length > 1) {
      const secondLetter = word.charAt(1);
      const lastCharIndex = word.length - 1;
      const lastLetter = word.charAt(lastCharIndex);
      word = word.replaceAt(1, lastLetter);
      word = word.replaceAt(lastCharIndex, secondLetter);
    }

    var ascii = word.charCodeAt(0);
    word = word.slice(1);
    word = ascii + word;
    words[i] = word;
  }

  return words.join().replaceAll(",", " ");
}

String.prototype.replaceAt = function(index, replacement) {
  return this.substr(0, index) + replacement + this.substr(index + replacement.length);
}

// Using the lazy way to replace the random commas with spaces; will break eventually
String.prototype.replaceAll = function(search, replacement) {
  let target = this;
  return target.replace(new RegExp(search, 'g'), replacement);
};
```
