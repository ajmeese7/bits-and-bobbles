
> See [here](https://stackoverflow.com/a/72392318/6456163) for the original answer.

This should be sufficient for your use case:

```regex
/(?<!\S)(?:https?:\/\/)?(?:(?:(?!example)\w+[.-])+[a-z]{2,11})(?!\S)/gi
```

See [here](https://regex101.com/r/NdOxKt/1) for a demonstration of the regex at work. Below is a rough explanation of what the regex is doing:

- The leading and trailing `(?<!\S)` essentially splits the string into segments on space characters, including whitespace and newlines
- The `?:` syntax makes each set of parenthesis it is in a non-capture group, saving memory on the machine where it is ran and speeding up your execution time
- `(?:https?:\/\/)?` optionally matches both `http` and `https` for URLs without matching the invalid characters `:` and `/` anywhere else in the URL
- `(?:(?!example)\w+[.-])+` looks for one or more words that do not match `example`, followed by either a hyphen or a period
- `[a-z]{2,11}` matches the final domain extension, i.e. `com`, `org`, or `enterprises`
