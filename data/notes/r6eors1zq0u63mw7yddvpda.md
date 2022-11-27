
### Python

```py
def generate_hashtag(s):
    capital_sentence = "".join(w.capitalize() for w in s.split())
    length = len(capital_sentence)
    if length == 0 or length > 140:
        return False

    return "#" + capital_sentence
```
