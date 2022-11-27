
> See [here](https://stackoverflow.com/a/72393858/6456163) for the original answer.

One way to do this that's even shorter than the other answers:

```js
document.onkeydown = (e) => console.log(e.key);
```

This uses an inline function to further reduce the length of the answer by [zer00ne](https://stackoverflow.com/a/72393774/6456163).

If you are more interested in form validation than just logging to the console, you can also do something along the lines of the following:

```js
function alphaOnly(event) {
  let key = event.keyCode;
  return ((key >= 65 && key <= 90) || key == 8);
};
```
