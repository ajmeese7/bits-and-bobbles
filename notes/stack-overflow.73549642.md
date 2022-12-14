---
id: d4kiep2vqjl211lepbknph5
title: 'Match Reaper `BYPASS` with regex'
desc: 'Regex XML Selection Extract Element'
updated: 1664736724320
created: 1661919120000
tags:
  - python
  - regex
  - reaper
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73549642/6456163) for the original answer.

[Here](https://regex101.com/r/XqVTds/2) is an example of the following matching regex at work:

```regex
BYPASS.*?(?:WAK \d \d)
```

This is how you implement the regex in Python:

```python
import re
matches = re.findall(r'BYPASS.*?(?:WAK \d \d)', string, flags=re.S|re.M)
```

I had to get rid of the capture group with `?:` and set the flags as a parameter to get it to work, but this should be what you need.
