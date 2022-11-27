
> See [here](https://stackoverflow.com/a/73671452/6456163) for the original answer.

The fix to this is to escape your underscore characters, as they are currently being interpreted as italics instead of as part of the mathematical equation:

```md
1. First she must calculate the inverse of $e \ (d)$ in $\mathbb{Z}\_{1440}$. Recall that $e$ has an inverse in $\mathbb{Z}\_{n}$ if $e$ * $e^{-1} \equiv 1 \ mod \ n$. This is easily done using Euclidian's algorithm. <br>
```

Example of this rendered in the GitHub markdown editor:

[![rendered markdown][1]][1]


  [1]: https://i.stack.imgur.com/xq0uQ.png
