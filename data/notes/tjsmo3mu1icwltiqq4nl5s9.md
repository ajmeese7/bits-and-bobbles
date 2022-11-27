
### JavaScript

```js
let termsToAdd = [], foundTerms = [];

function sumDifRev(n) {
  if (foundTerms.length < n) populateTerms();
  return foundTerms[n - 1];
}

function populateTerms() {
  let lastTerm = foundTerms[foundTerms.length - 1];
  let numToTest = lastTerm ? lastTerm + 1 : 0;

  for (let i = numToTest; i < 1000000; i++) {
    // Reversed number
    if (termsToAdd.includes(i)) {
      foundTerms.push(i);
      continue;
    }

    var reverse = flipInt(i);
    var sum = i + reverse;
    var diff = Math.abs(i - reverse);

    // Checks if the condition is met
    if (sum % diff == 0) {
      if (reverse.toString().length == i.toString().length) {
        foundTerms.push(i);
        termsToAdd.push(reverse);
      }
    }
  }
}

// https://stackoverflow.com/a/52366332
function flipInt(n) {
  var digit, result = 0;
  while (n) {
      digit = n % 10;                  //  Get last digit. Ex. 123/10 → 12.3 → 3
      result = (result * 10) + digit;  //  Ex. 123 → 1230 + 4 → 1234
      n = n/10|0;                      //  Remove last digit. Ex. 123 → 12.3 → 12
  }

  return result;
}
```

### CoffeeScript

```coffee
foundTerms = []

sumDifRev = (n) ->
  if foundTerms.length < n
    populateTerms()

  return foundTerms[n - 1]

populateTerms = () ->
  i = 0
  while i < 1000000
    reverse = flipInt(i)
    sum = i + reverse
    diff = Math.abs(i - reverse)

    # Checks if the condition is met
    if sum % diff == 0
      if reverse.toString().length == i.toString().length
        foundTerms.push(i)

    i++

# https://stackoverflow.com/a/52366332
flipInt = (n) ->
  digit = 0
  result = 0
  while n != 0
      digit = n % 10
      result = (result * 10) + digit
      n = n/10|0;

  return result
```

### Python

```py
foundTerms = []

def sum_dif_rev(n):
    if len(foundTerms) < n:
        populateTerms()

    return foundTerms[n - 1]

def populateTerms():
    for i in range(1, 1000000):
        reverse = flipInt(i)
        sum = i + reverse
        diff = abs(i - reverse)

        # Checks if the condition is met
        if diff != 0 and sum % diff == 0:
            if len(str(reverse)) == len(str(i)):
                foundTerms.append(i)

# https://stackoverflow.com/a/52366332
def flipInt(num):
  rev = 0
  while num > 0:
    rev = (10 * rev) + num % 10
    num //= 10
  return rev
```
