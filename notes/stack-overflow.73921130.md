---
id: zt8b9aov0n9enp5e5jnwuvl
title: 'Regex for all active SCSS variables'
desc: 'How to target all scss variables which is used for styling with regex'
updated: 1664737957678
created: 1664666537000
tags:
  - regex
  - scss
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73921130/6456163) for the original answer.

If you are looking for all occurrences of SCSS variables that are being used, this will work for you:

```regex
:.*(\$[\w-]+)
```

A demo can be found [here](https://regex101.com/r/WtyoF6/2).
