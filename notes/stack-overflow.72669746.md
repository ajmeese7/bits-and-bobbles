---
id: rkylsqztsz64wdm80bemzif
title: 'Center angled text in CSS'
desc: 'Adjusting text in html/css portfolio website project'
updated: 1664735129362
created: 1655574300000
tags:
  - html
  - css
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72669746/6456163) for the original answer.

I was able to get it looking how you want by modifying the `.front-person-titles>.t1` code to the following:

```css
.front-person-titles>.t1 {
  right: 0;
  bottom: 0;
  -webkit-transform: rotate(-90deg) translateY(-100%) translateX(-7.5%);
  -moz-transform: rotate(-90deg) translateY(-100%) translateX(-7.5%);
  -ms-transform: rotate(-90deg) translateY(-100%) translateX(-7.5%);
  -o-transform: rotate(-90deg) translateY(-100%) translateX(-7.5%);
  transform: rotate(-90deg) translateY(-100%) translateX(-7.5%);
  -webkit-transform-origin: 0% 0%;
  -moz-transform-origin: 0% 0%;
  -ms-transform-origin: 0% 0%;
  -o-transform-origin: 0% 0%;
  transform-origin: 0% 0%;
}
```

You can see a working JSFiddle [here](https://jsfiddle.net/ajmeese7/sjwL375g/1/).
