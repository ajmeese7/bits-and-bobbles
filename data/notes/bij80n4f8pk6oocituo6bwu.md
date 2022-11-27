
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
