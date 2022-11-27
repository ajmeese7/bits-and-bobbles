
> See [here](https://stackoverflow.com/a/72959497/6456163) for the original answer.

Use the following in your find and replace tool for the find portion:

```regex
<a[^>]*>(.[^<]*)</a>
```

Then use the capture group for the replace portion:

```regex
$1
```

What this does is looks for `<a` then any number of characters that are not the closing angle bracket (`>`). Next it matches all characters up until the next opening angle bracket (`<`), then looks for the closing `</a>`. Finally, all the characters in the middle are what is used to replace the matched text, thanks to the capturing group `$1`.
