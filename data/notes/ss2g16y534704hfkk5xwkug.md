
> See [here](https://stackoverflow.com/a/57675174/6456163) for the original answer.

Depending on how specific you need it to be, you could create a range of +-1 second or some similar number with `toBeWithinRange` from the [Jasmine Matchers](https://www.npmjs.com/package/jasmine-expect) package:

```js
expect(createdTime).toBeWithinRange(Date.now() - 1000, Date.now() + 1000)
```

With this method you will have to test the `createdTime` separately from the other test, but that shouldn't be too big of an issue. You just need to assign the return property that you want to the variable `createdTime`.

**Edit**- A similar method with a more clear matcher is using `toBeNear`:

```js
expect(createdTime).toBeNear(Date.now(), 2);
```

This will be true if the date assigned to createdTime is within two seconds of the date when the test runs.

**Edit 2**- to exclude object keys when testing, you can follow an example [here](https://stackoverflow.com/a/24487384/6456163). This is how you would do it in your case:

```js
var joc = jasmine.objectContaining;
expect(fun("abc", 1))
.toEqual(joc({
  name: "abc",
  id: 1
}));
```
