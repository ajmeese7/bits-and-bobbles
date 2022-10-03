---
id: e7308g3r3xhpvxzh5eyugj1
title: 'Human Readable Time'
desc: ''
updated: 1664741426217
created: 1630936080000
tags:
  - javascript
  - elixir
  - 5-kyu
  - codewars
  - answer
---

### Elixir

```elixir
defmodule HumanReadable do
  def format(seconds) do
    sec = "#{ rem seconds, 60 }"
    min = "#{ rem trunc(seconds / 60), 60 }"
    hour = "#{ trunc(seconds / 60 / 60) }"
    Enum.map_join [hour, min, sec], ":", &(String.pad_leading(&1, 2, "0"))
  end
end
```

### JavaScript

```js
function humanReadable(seconds) {
  sec = seconds % 60
  min = Math.trunc(seconds / 60) % 60
  hour = Math.trunc(seconds / 60 / 60)
  return [hour, min, sec].map(x => `${x}`.padStart(2, "0")).join(":")
}
```
