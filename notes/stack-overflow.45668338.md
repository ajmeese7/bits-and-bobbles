---
id: cjwzqnbs9yont3zjbxilsgd
title: 'Apply CSS class to focused element with jQuery'
desc: 'How to make only 1 input box do animation on focus using Jquery'
updated: 1664735226843
created: 1502705340000
tags:
  - jquery
  - html
  - focus
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/45668338/6456163) for the original answer.

You just have to add separate ID's to access the different fields:

```html
<span class="fakeplaceholder" id="first">First Name</span>
<span class="fakeplaceholder" id="last">Last Name</span>
```

Then apply the `fakeplaceholdertop` class to the specific element:

```js
$(".firstname").focus(function() {
    $("#first").addClass("fakeplaceholdertop");
});

$(".lastname").focus(function() {
    $("#last").addClass("fakeplaceholdertop");
});
```
