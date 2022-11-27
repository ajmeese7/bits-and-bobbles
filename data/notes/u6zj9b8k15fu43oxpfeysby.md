
> See [here](https://stackoverflow.com/a/73515160/6456163) for the original answer.

I recommend using `localStorage` for this particular use case, because it can easily be implemented alongside your current method:

```js
const triggerElement = document.getElementById("trigger-element");
const header = document.getElementById("h");

const animationTriggered = localStorage.getItem("animationTriggered") === "true";
let initialLoad = true;

const menuChange = function() {
  if (animationTriggered && initialLoad) {
    header.style.background = "black";
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

window.addEventListener("scroll", menuChange);
```

This will remember the previous state and apply the black background color if the animation was previously triggered. This adds a small amount of overhead, but in a real-world scenario it should not have any noticeable impact on the performance of the application.
