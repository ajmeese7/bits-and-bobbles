---
id: dp2kjinfge5kncyuas0tgtj
title: "Scroll debounce in JavaScript"
desc: "Invoke A Debounce Function After A Scroll Has Happened Or After An Initial Delay - Javascript"
updated: 1664738177628
created: 1661793060000
tags:
  - javascript
  - debounce
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73529341/6456163) for the original answer.

One solution is to simply have a different initial `eventListener`, since you already have tracking of whether the page is initially loading, and after the initial load then transition it to your `debounce` listener:

```js
// deBounce function
const debounce = (method, delay) => {
  clearTimeout(method._tId);
  method._tId= setTimeout(() => {
    method();
  }, delay);
}

const triggerElement = document.getElementById("trigger-element");
const header = document.getElementById("h");

const animationTriggered = localStorage.getItem("animationTriggered") === "true";
let initialLoad = true;

const menuChange = function() {
  if (initialLoad) {
    if (animationTriggered) {
      header.style.background = "black";
    }

    removeEventListener("scroll", scrollFunc);
    addEventListener("scroll", scrollFunc = function() {
      // menuChange function invoked WITH the debounce function
        debounce(menuChange, 100);
    });
  } else if (triggerElement.getBoundingClientRect().top < 50) {
    header.style.background = "black";
    header.style.transition = "1s";
    localStorage.setItem("animationTriggered", "true");
  } else {
    header.style.background = "red";
    header.style.transition = ".15s";
    localStorage.setItem("animationTriggered", "false");
  }

  initialLoad = false;
}

// menuChange function invoked WITHOUT the debounce function
addEventListener("scroll", scrollFunc = function() {
  menuChange();
});
```

```css
body {
  margin: 0;
  height: 200vh;
}

#h {
  display: flex;
  justify-content: center;
  background: red;
  color: #fff;
  position: fixed;
  top: 0;
  width: 100%;
}

#trigger-element {
  margin-top: 150px;
  padding: 1rem;
  background:blue;
  color: #fff;
}
```

```html
<header id="h">
  <p>HEADER CONTENT</p>
</header>
<div id="trigger-element">Trigger Element</div>
```

This is possible by transitioning the `eventListener` from an anonymous arrow function to a named function, allowing us to call `removeEventListener` on that particular listener so a new one can replace it.
