---
id: xxoxf86n0sbb124pubr625g
title: 'Highest Scoring Word'
desc: ''
updated: 1664741531172
created: 1630084620000
tags:
  - elixir
  - 6-kyu
  - codewars
  - answer
---

### Elixir

```elixir
defmodule Kata do
  def high(str) do
    words = String.split(str, " ")
    word_values = Enum.map(words, fn word -> get_word_value(word) end)
    max_value = Enum.max(word_values)
    index = Enum.find_index(word_values, fn x -> x == max_value end)
    Enum.at(words, index)
  end

  def get_word_value(word) do
    chars = String.split(word, "", trim: true)
    Enum.reduce chars, 0, fn (char, acc) ->
      # https://elixirforum.com/t/get-ascii-value-of-a-character/16619/3
      <<val::utf8>> = char
      val - 96 + acc # a's codepoint is 97 and the intended value is 1
    end
  end
end
```
