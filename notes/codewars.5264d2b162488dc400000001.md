---
id: kqcs5tlazyv9jh1jwdn8ail
title: 'Stop gninnipS My sdroW!'
desc: ''
updated: 1664741474676
created: 1591960500000
tags:
  - javascript
  - coffeescript
  - python
  - typescript
  - 6-kyu
  - codewars
  - answer
---

### JavaScript

```js
function spinWords(sentence) {
  return sentence.split(' ').map(word => word.length > 4 ? word.split('').reverse().join('') : word).join(' ');
}
```

### CoffeeScript

```coffee
spinWords = (string) ->
  return `string.split(' ').map(word => word.length > 4 ? word.split('').reverse().join('') : word).join(' ')`
```

### Python

```py
def spin_words(sentence):
    sentence = sentence.split(' ')
    for i in range(len(sentence)):
        sentence[i] = reverse(sentence[i])
    return ' '.join(sentence)

def reverse(word):
    if len(word) > 4:
        return word[::-1]
    return word
```

### TypeScript

```ts
export class Kata {
  static spinWords(words: string) {
    return words.split(' ').map(word => word.length > 4 ? word.split('').reverse().join('') : word).join(' ');
  }
}
```
