
> See [here](https://stackoverflow.com/a/73802179/6456163) for the original answer.

One way to do this is to look for only empty lines at the end of the file and remove them all:

```regex
(\n,*)+$/g
```

An example can be found [here](https://regex101.com/r/YOk2nb/3), it just requires using an empty substitution as demonstrated.
