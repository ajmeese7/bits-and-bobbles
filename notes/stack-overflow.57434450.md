---
id: ttqxfax797mnwg6vg3jtg75
title: 'Show `n` columns side-by-side with CSS'
desc: 'Third element ends up in new line in Safari'
updated: 1664732509870
created: 1565384580000
tags:
  - css
  - bootstrap
  - safari
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/57434450/6456163) for the original answer.

I fixed this [here](https://jsfiddle.net/ajmeese7/k5o60dwy/5/). The problem was the flex was overriding the default width.

This is what the CSS is now:

```css
.col-md-4 {
  flex: none;
  max-width: 33.3333333333%;
  width: 20%;
}
```

It successfully sets the width of the columns to 20% instead of 33.3%.
