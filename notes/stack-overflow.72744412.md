---
id: 2c330oc0v1okd2d0mzhe96q
title: 'Listening for `close` event of `datetime-local` input'
desc: 'How to listen for close event of datetime-local in pure JavaScript?'
updated: 1664736530119
created: 1656089640000
tags:
  - javascript
  - event
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72744412/6456163) for the original question.

I was able to get this working by using the `onchange` event, but it only works when the user actually interacts with the popup. If they click the default selected date (today) then it functions fine, but if they just leave it selected and close the popup then it doesn't work.

See example code below:

```js
const picker = document.getElementById("datePicker");

picker.onchange = function() {
  alert("This works when the input is changed, but not when the picker is closed without user interaction.");
};
```

This is more of a workaround than the actual solution I was looking for, so other answers are welcome.
