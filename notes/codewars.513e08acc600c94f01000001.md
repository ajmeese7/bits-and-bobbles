---
id: n37j1vg5zbv8hz7elazk8j9
title: 'RGB To Hex Conversion'
desc: ''
updated: 1664741500813
created: 1630854240000
tags:
  - elixir
  - 5-kyu
  - codewars
  - answer
---

### Elixir

```elixir
defmodule Kata do
  def rgb(r,g,b) do
    Enum.map_join([r, g, b], fn x ->
      convert_to_hex(
        make_valid_value(x)
      )
    end)
  end

  def make_valid_value(num) do
    cond do
      num > 255 -> 255
      num < 0 -> 0
      true -> num
    end
  end

  def convert_to_hex(num) do
    hex = Integer.to_string(num, 16)
    if String.length(hex) == 1, do: "0" <> hex, else: hex
  end
end
```
