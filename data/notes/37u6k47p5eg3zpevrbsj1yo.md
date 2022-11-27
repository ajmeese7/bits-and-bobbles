
> See [here](https://stackoverflow.com/a/73804168/6456163) for the original answer.

I found the problem, the Keybase API just wasn't very helpful with the provided error message.

You need to put quotes around the `{}` in the `echo` statement, like such:

```python
cmd = "echo '{}' | keybase chat api > {}".format(q, json_out)
```
