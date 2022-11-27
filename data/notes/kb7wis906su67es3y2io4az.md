
> See [here](https://stackoverflow.com/a/73778031/6456163) for the original answer.

One way you can do this is via regex, by accepting any value that is not `"none"`:

```js
const NewUserSchema = Yup.object().shape({
  createDate: Yup.string().nullable().required('Create date is required'),
  boughtby: Yup.string().matches(/^(?!none).*$/, "Cannot be none").required("Cannot be none")
});
```
