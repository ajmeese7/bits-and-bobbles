
> See [here](https://stackoverflow.com/a/72653154/6456163) for the original answer.

It's difficult to pinpoint the exact problem without knowing what your `webpack` configuration looks like, but my guess is that you don't have a loader for TypeScript files set up. I recommend adding something like the following to your `module.exports` and seeing if that solves your issue:

```js
module: {
  rules:[
    {
      test: /\.ts$/,
      use: "ts-loader",
      include: [path.resolve(__dirname, "src")]
    }
  ],
  resolve: {
    extensions: [".ts", ".js"],
  },
},
```
