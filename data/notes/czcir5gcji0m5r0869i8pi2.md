
### JavaScript

```js
function validatePIN (pin) {
  const pinRegex = new RegExp("^\\d{4}(?:\\d{2})?$");
  return pinRegex.test(pin);
}
```
