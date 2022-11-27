
> See [here](https://stackoverflow.com/a/57730165/6456163) for the original answer.

This can be solved by adding random parameters to the image src, as shown [here](https://stackoverflow.com/a/729623/6456163). For example, turn this:

```html
<img src="image.png" />
```

Into this:

```html
<img src="image.jpg?1222259157.415">
```

In the second src, the numbers after the question mark are the current timestamp. This is demonstrated in [this](https://stackoverflow.com/a/6116854/6456163) answer, which sets the timestamp in JavaScript and appends it to the src using `Date.now()`.
