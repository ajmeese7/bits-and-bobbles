
> See [here](https://stackoverflow.com/a/73723939/6456163) for the original answer.

What you're looking for is the `re.sub()` method:

```python
import re

l = ['S;V;iPad\r', 'C;M;mouse pad\r', 'C;C;code swarm\r', 'S;C;OrangeHighlighter']
l_new = [re.sub(r'\r', '', i) for i in l]
print(l_new)
```

This will remove all occurrences of the `\r` escape sequence.
