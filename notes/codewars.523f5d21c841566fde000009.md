---
id: dku2drnfn9oum7rrglri0kk
title: 'Array.diff'
desc: ''
updated: 1664741489270
created: 1630347960000
tags:
  - elixir
  - 6-kyu
  - codewars
  - answer
---

### Elixir

```elixir
defmodule ArrayDiff do
  def array_diff(a, b) do
    Enum.filter(a, fn(val) -> !Enum.member?(b, val) end)
  end
end
```
