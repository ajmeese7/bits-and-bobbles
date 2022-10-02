---
id: myxha5t7mre67gwfqniubvg
title: 'Ignore `n` lines of `sed` output'
desc: 'Sed to add color to column for a specific pattern?'
updated: 1664735132369
created: 1655573760000
tags:
  - bash
  - sed
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72669696/6456163) for the original answer.

One way to do this is to ignore the first two lines of the output in sed:

```shell
sed "1,2 ! s/[^[:blank:]]\{1,\}/$green&$off/3";
```
