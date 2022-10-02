---
id: jee328a8o98akt59c4a4qrj
title: 'Get all elements at point with `elementsFromPoint` in JavaScript'
desc: 'how do i trigger onMouseEnter for elements behind other elements'
updated: 1664738106793
created: 1660236677000
tags:
  - javascript
  - dom
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73320961/6456163) for the original answer.

According to [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Element/mouseenter_event#usage_notes), the `mouseenter` event does not bubble, whereas the `mouseover` event does. However, even if it DID bubble, your elements currently have no relation to one another, thus the mouse events are captured by the upper element.

One possible way around this is with the amazing `elementsFromPoint` function in JavaScript, which makes quick work of solving your issue:

```js
// Only the IDs of the elments you are interested in
const elems = ["1", "2"];

// Modified from https://stackoverflow.com/a/71268477/6456163
window.onload = function() {
  this.addEventListener("mousemove", checkMousePosition);
};

function checkMousePosition(e) {
  // All the elements the mouse is currently overlapping with
  const _overlapped = document.elementsFromPoint(e.pageX, e.pageY);

  // Check to see if any element id matches an id in elems
  const _included = _overlapped.filter((el) => elems.includes(el.id));
  const ids = _included.map((el) => el.id);

  for (const index in elems) {
    const id = elems[index];
    const elem = document.getElementById(id);

    if (ids.includes(id)) {
      elem.style.background = "yellow";
    } else {
      elem.style.background = "green";
    }
  }
}
```

```css
div {
  width: 100px;
  height: 100px;
  background: green;
  border: 2px solid black;
}
.second {
  transform: translateX(50%) translateY(-50%);
}
```

```html
<div id="1"></div>
<div id="2" class="second"></div>
```
