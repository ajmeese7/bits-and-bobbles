
### Elixir

```elixir
defmodule Evaporator do

  @spec evaporator(number, number, number) :: number

  def evaporator(content, evap_per_day, threshold) do
    count = 0
    percent_remaining = 1 - (evap_per_day / 100)
    percent_thresh = evap_per_day * (threshold / 100)

    length(
      Stream.unfold({evap_per_day, count}, fn { x, count}  ->
        IO.puts x
        if x > percent_thresh do
          {x, {x * percent_remaining, count + 1} }
        else
          nil
        end
      end) |> Enum.to_list()
    )
  end

end
```
