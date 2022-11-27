
### Python

```py
def solution(s):
    solution_array = []
    for i in range(0, len(s), 2):
        string = s[i] + (s[i+1] if i+1 < len(s) else '_')
        solution_array.append(string)
    return solution_array
```
