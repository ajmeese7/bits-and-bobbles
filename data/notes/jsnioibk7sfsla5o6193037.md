
> See [here](https://stackoverflow.com/a/73837133/6456163) for the original answer.

See [this thread](https://unix.stackexchange.com/a/562776/370076) for an example of validating user input in Bash.

Here is the code modified for your use case:

```shell
#!/usr/bin/bash

REGEX='^[YyNn]$'

CHECK="your_user_input_var"

if [[ ! $CHECK =~ $REGEX ]]
then
  echo "Not ok"
else
  echo "ok"
fi
```
