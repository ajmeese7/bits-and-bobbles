
> See [here](https://stackoverflow.com/a/72680106/6456163) for the original answer.

You can always use `display: flex`. Here's an example:

```css
#container {
  display: flex;
  flex-direction: row;
  width: 100%;
  justify-content: space-around;
}

#text-container a {
  display: block;
}
```

```html
<div id="container">
  <img src="https://via.placeholder.com/150" />
  <div id="text-container">
    <a href="https://google.com">Link 1</a>
    <a href="https://google.com">Link 2</a>
    <a href="https://google.com">Link 3</a>
  </div>
  <img src="https://via.placeholder.com/150" />
</div>
```
