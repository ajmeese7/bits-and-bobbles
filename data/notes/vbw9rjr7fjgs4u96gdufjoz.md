
### PowerShell

```powershell
function RowSumOddNumbers([int] $n) {
  return $n * $n * $n;
}
```

### JavaScript

```js
function rowSumOddNumbers(n) {
  let sum = 0, num = 1;
  for (let row = 1; row <= n; row++) {
    for (let i = 0; i < row; i++) {
      if (row == n) sum += num;
      num += 2;
    }
  }

  return sum;
}
```
