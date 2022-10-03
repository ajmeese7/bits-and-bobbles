---
id: y4z6yi08xz82s0ogdfwgam3
title: 'Crack the PIN'
desc: ''
updated: 1664741595890
created: 1596551160000
tags:
  - php
  - 6-kyu
  - codewars
  - answer
---

### PHP

```php
function crack($hash) {
  $pin = "00000";
  $passHash = md5($pin);

  while ($passHash != $hash) {
    $pin++;
    $pin = str_pad($pin, 5, "0", STR_PAD_LEFT);
    $passHash = md5($pin);
  }

  return $pin;
}
```
