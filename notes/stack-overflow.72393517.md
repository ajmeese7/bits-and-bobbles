---
id: b8kj83pcqjap9qp0zfdqp1i
title: 'How to get a Value from NodeList?'
desc: ''
updated: 1664735167894
created: 1653589980000
tags:
  - javascript
  - nodelist
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72393517/6456163) for the original answer.

One way to access the items returned from `getElementsByNodeName` is from [W3 Schools](https://www.w3schools.com/jsref/met_doc_getelementsbyname.asp):

```js
const collection = document.getElementsByName("phone");
for (let i = 0; i < collection.length; i++) {
  let valueYouAreInterestedIn = collection[i].specialKeyYouWant;
  // Use the value below :)
}
```

Please comment if there is anything else you need help with!
