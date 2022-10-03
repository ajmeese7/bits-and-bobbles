---
id: czcir5gcji0m5r0869i8pi2
title: 'Regex validate PIN code'
desc: ''
updated: 1664741565124
created: 1657410720000
tags:
  - javascript
  - 7-kyu
  - codewars
  - answer
---

### JavaScript

```js
function validatePIN (pin) {
  const pinRegex = new RegExp("^\\d{4}(?:\\d{2})?$");
  return pinRegex.test(pin);
}
```
