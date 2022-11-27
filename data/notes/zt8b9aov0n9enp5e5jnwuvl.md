
> See [here](https://stackoverflow.com/a/73921130/6456163) for the original answer.

If you are looking for all occurrences of SCSS variables that are being used, this will work for you:

```regex
:.*(\$[\w-]+)
```

A demo can be found [here](https://regex101.com/r/WtyoF6/2).
