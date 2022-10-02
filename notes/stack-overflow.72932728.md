---
id: jbftpogwwizzzjrtq29h6nr
title: 'Remove empty space after HTML body'
desc: 'How can solve the empty space at bottom of page?'
updated: 1664736529878
created: 1657513320000
tags:
  - html
  - css
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72932728/6456163) for the original answer.

I can help! The problem is the height of your body, which can be solved with the following CSS:

```css
body {
  min-height: 100%;
}
```

Then to give the appearance of no empty space, you can position your footer element all the way at the base of the page, like so:

```css
footer {
  position: fixed;
  bottom: 0;
  width: 100%;
}
```
