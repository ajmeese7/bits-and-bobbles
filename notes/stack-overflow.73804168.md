---
id: 37u6k47p5eg3zpevrbsj1yo
title: 'Read team chats with Keybase Chat API'
desc: 'How to read team chats with Keybase Chat API?'
updated: 1664737716359
created: 1663792140000
tags:
  - keybase
  - api
  - python
  - json
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73804168/6456163) for the original answer.

I found the problem, the Keybase API just wasn't very helpful with the provided error message.

You need to put quotes around the `{}` in the `echo` statement, like such:

```python
cmd = "echo '{}' | keybase chat api > {}".format(q, json_out)
```
