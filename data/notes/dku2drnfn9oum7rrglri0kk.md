
### Elixir

```elixir
defmodule ArrayDiff do
  def array_diff(a, b) do
    Enum.filter(a, fn(val) -> !Enum.member?(b, val) end)
  end
end
```
