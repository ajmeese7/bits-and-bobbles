---
id: qjej22wp8dwm55t1y77tgkc
title: 'Creating HTML/Javascript Modal with dynamic text'
desc: ''
updated: 1664736530150
created: 1653589680000
tags:
  - javasript
  - nodelist
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72393463/6456163) for the original answer.

The problem with your code is that you are attempting to access the entirety of the `querySelectorAll` array instead of the individual element that you are interested in. See the code below for an example of a way to resolve this:

```js
for (let i = 0; i < btnsOpenModal.length; i++) {
  btnsOpenModal[i].addEventListener("click", function () {
    const modalText = btnsOpenModal[i].id;

    if (text[i].classList.contains(modalText)) {
      text[i].classList.remove("hidden");
    }

    modal.classList.remove("hidden");
    overlay.classList.remove("hidden");
  });
}
```
