
> See [here](https://stackoverflow.com/a/73313760/6456163) for the original answer.

One way to accomplish this is by looking for the last occurrence of the backslash character, since your examples indicated that the presence of at least once can be relied on.

The `find` regex:

```regex
(href|src)=".*\\(.*)"
```

The `replace` regex:

```regex
$1="images\\$2"
```

You can see this in action [here](https://regex101.com/r/8c6QoA/1) with the examples you have provided.
