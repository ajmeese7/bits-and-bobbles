---
id: khnlrwl005sy77xwat19onq
title: 'Setting relative dates in JavaScript with `setDate`'
desc: Why does Javascript's Date.getDate() .setDate() behave so unpredictably?
updated: 1664736529011
created: 1655765820000
tags:
  - javascript
  - date
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/72691782/6456163) for the original answer.

In answer to your question, the `setDate()` function is behaving so strangely for you because each time you are setting the date you are setting it relative to the previous setting, so incrementing each time by 31, 32, or 33 days instead of by 1, 2, or 3. See the brilliant answer by @Quentin for more information, this finding was entirely his and I just wanted to mention the root cause in my answer as well as my own fix to your problem.

---

An alternative solution if you just want to generate the dates:

```js
const dayOfMonth = 30;
const date = new Date();
date.setDate(dayOfMonth);
console.log("Date:", date);

const timestamp = Date.parse(date);
for (let i = 1; i <= 14; i++) {
  const newTimestamp = timestamp + i * (1000 * 60 * 60 * 24);
  const newDate = new Date(newTimestamp);
  console.log("New date:", newDate);
}
```

This method will manipulate the timestamp and generate new dates for each of the timestamps added to the number of milliseconds in a day.

You could use your date logic within the loop to populate the calendar as you mentioned.
