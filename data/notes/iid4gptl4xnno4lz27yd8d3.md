
> See [here](https://stackoverflow.com/a/72885945/6456163) for the original answer.

The way the project I'm working on captures the `stdout` is with `contextlib`. Below is a small code sample that should get the information you are looking for, which you can then append to the value of the textarea:

```python
from contextlib import redirect_stdout
import io

with redirect_stdout(io.StringIO()) as output:
    # Your code that generates output here
    ...

    # This will get the lines from the output
    lines = output.getvalue().splitlines()

    # Append `lines` to the textarea content here
    ...
```
