---
id: rdwkzmaakd49u16qdor8mz8
title: 'How to add or remove a className when screen size change in react'
desc: ''
updated: 1664735187359
created: 1599926700000
tags:
  - react
  - hooks
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/63860125/6456163) for the original answer.

If you're looking to do this with hooks instead of classes, here is a simple example for this case:

```js
const [isMobile, setIsMobile] = useState(window.innerWidth < 1200);

{/* Performs similarly to componentDidMount in classes */}
useEffect(() => {
    window.addEventListener("resize", () => {
        const ismobile = window.innerWidth < 1200;
        if (ismobile !== isMobile) setIsMobile(ismobile);
    }, false);
}, [isMobile]);

{/* There is no need for a render function with Hooks */}
return (
    <p className={`${isMobile ? "mobile-class" : "non-mobile-class"}`}>Your text here</p>
);
```

For a more in-depth explanation of the useEffect hook, check out the official React documentation [here](https://reactjs.org/docs/hooks-state.html). Please note that you must be using React 16.8 or higher to take advantage of hooks.
