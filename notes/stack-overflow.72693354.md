---
id: nu7i14lstj9bck6wisnvbqw
title: 'Excluding spaces from `text-decoration`'
desc: 'Can i exclude spaces from text decoration?'
updated: 1664738224090
created: 1655776320000
tags:
  - css
  - javascript
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72693354/6456163) for the original answer.

As you and @dippas figured out, this is currently not supported via pure CSS across all browsers.

I suggest doing this with JavaScript, by splitting the text you are interested in at the space character into separate span elements. You can then apply your `line-through` decoration to the span elements, which will not include the spaces.

Here is a simple example:

```html
<div>
  <del>All the text to be marked through here</del>
  <br />
  <del>Additional text to be marked through here</del>
</div>
```

```css
del {
  text-decoration: none;
}

del span {
  text-decoration: line-through;
}
```

```js
const elements = document.querySelectorAll("del");
for (let i = 0; i < elements.length; i++) {
  const elem = elements[i];
  const words = elem.innerText.split(" ");
  const spans = words.map((word) => {
    const span = document.createElement("span");
    span.innerText = word;
    return span;
  });

  elem.innerHTML = "";
  spans.forEach((span) => {
    elem.appendChild(span);
    elem.innerHTML += "&nbsp;";
  });
}
```
