---
id: jsnioibk7sfsla5o6193037
title: 'User input validation in Bash'
desc: 'Checking for character in string'
updated: 1664737801077
created: 1664035980000
tags:
  - bash
  - regex
  - input
  - validation
  - stack-overflow
  - answer
---

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
