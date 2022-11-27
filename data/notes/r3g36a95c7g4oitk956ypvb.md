
> See [here](https://stackoverflow.com/a/73225506/6456163) for the original answer.

I have modified your example to get it working [here](https://regex101.com/r/wp0XGj/1). What you needed to do is escape the square brackets so they would be interpreted literally, since they have special meaning in regex, and you needed to use a capture group to store the matching value in `$1` so you could use it in the replacement.

Regular expression:

```regex
!\[\[.*\/(.*_image[0-9]{1,2}\.png)\]\]
```

Substitution format:

```regex
![image]\($1\)
```
