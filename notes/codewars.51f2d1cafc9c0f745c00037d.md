---
id: fyhho17k0o9ufi6avxhxjli
title: 'String ends with?'
desc: ''
updated: 1664741590437
created: 1630271400000
tags:
  - elixir
  - 7-kyu
  - codewars
  - answer
---

### Elixir

```elixir
defmodule EndsWith do
  def solution(str, ending) when ending == "", do: true

  def solution(str, ending) do
    string_len = String.length(str)
    search_len = String.length(ending)
    ending == String.slice(str, -search_len, string_len)
  end

end
```
