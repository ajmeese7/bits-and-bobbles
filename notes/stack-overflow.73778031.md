---
id: kb7wis906su67es3y2io4az
title: 'Custom `Yup` validation messages'
desc: 'Yup validation throw error on specific word'
updated: 1664737365557
created: 1663627800000
tags:
  - nodejs
  - react
  - yup
  - stack-overflow
  - answer
---

> See [here](https://stackoverflow.com/a/73778031/6456163) for the original answer.

One way you can do this is via regex, by accepting any value that is not `"none"`:

```js
const NewUserSchema = Yup.object().shape({
  createDate: Yup.string().nullable().required('Create date is required'),
  boughtby: Yup.string().matches(/^(?!none).*$/, "Cannot be none").required("Cannot be none")
});
```
