---
id: orsf7j9wung58kxg0pg5s36
title: 'Anchor progress bar to element border'
desc: 'How to attach a progress bar as a border to div'
updated: 1664736530122
created: 1657474020000
tags:
  - css
  - typescript
  - react
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72928841/6456163) for the original answer.

I was able to get your example working with a few CSS changes, below are the only two parts I needed to change:

```css
.App {
  overflow: hidden;
}

.emptyProgressBar {
  border-radius: 0px;
}

.fillingProgressBar {
  width: 102%;
}
```

Then in `App.tsx`, change your left style to `-101`, like the following:

```tsx
left: props.percent - 101 + "%",
```

A working example forked from your sandbox is available [here](https://codesandbox.io/s/linear-progress-bar-forked-hgv7kq?file=/src/styles.css).
