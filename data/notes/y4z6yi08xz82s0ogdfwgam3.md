
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
