
### Python

```py
def polydivisible(x):
    isPoly = True
    for numDigits in range(1, len(str(x)) + 1):
        num = int(str(x)[:numDigits])
        if num % numDigits is not 0:
            isPoly = False
            break
    return isPoly
```
