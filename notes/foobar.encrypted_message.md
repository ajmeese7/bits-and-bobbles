---
id: ea5bta1m7crmtpzddhkx61b
title: Encrypted Message
desc: ''
updated: 1666221881412
created: 1666221865011
tags:
  - python
  - foobar
  - google
---

```py
import base64

MESSAGE = """
Gk0eEAYQAEQSTU1fRVQCRQQLGUJJU0JUDgYBAAQUEFJGSldFQhYWQwQPAAABVEkXRg8LAwoBEURG
SldFQhoLVBMPCQwHHwAQTUpKBAYbDFIXDwAACwdCF1tKShALHwpUCg8JQklTQkUACA8MEQBCF1tK
ShYEFQAQTUpKAwocQhdbSkoSDB1EEBw=
"""

KEY = "ajmeese7"

result = []
for i, c in enumerate(base64.b64decode(MESSAGE)):
    result.append(chr(c ^ ord(KEY[i % len(KEY)])))

print("".join(result))
```
