---
id: bij80n4f8pk6oocituo6bwu
title: 'altERnaTIng cAsE <=> ALTerNAtiNG CaSe'
desc: ''
updated: 1664741540648
created: 1629558180000
tags:
  - elixir
  - 8-kyu
  - codewars
  - answer
---

### Elixir

```elixir
defmodule Codewars.StringUtils do
  def alter_case(str) do
    to_string(
      Enum.map(
        String.graphemes(str),
        fn char -> change_char_case(char) end
      )
    )
  end

  def change_char_case(char) do
    if String.upcase(char) == char do
      String.downcase(char)
    else
      String.upcase(char)
    end
  end
end
```
