
### Python

```py
from collections import Counter

def duplicate_count(text):
    if not text: return 0
    frequencies = Counter(text.lower())
    return len(list(
        filter(lambda x: x > 1, frequencies.values())
    ))
```
