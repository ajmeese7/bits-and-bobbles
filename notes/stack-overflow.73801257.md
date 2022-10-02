---
id: 51y48nm7vp27rg0h6336iew
title: 'Pass JSON to Keybase Chat API'
desc: 'flags need an argument keybase chat api example'
updated: 1664737550087
created: 1663779960000
tags:
  - keybase
  - api
  - json
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73801257/6456163) for the original answer.

The `-m` flag is intended to take a JSON string directly instead of reading from STDIN, which is what your `echo` statement is passing.

If you want to read from `echo`, simply remove the `-m` flag entirely. If you wish to use the `-m` flag and read from a string, try the following format:

```shell
keybase chat api -m "{'method': 'send', 'params': {'options': {'channel': {'name': 'you', 'public': true}, 'message': {'body': 'Still going...'}}}}"
```
