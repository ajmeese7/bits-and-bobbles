
> See [here](https://stackoverflow.com/a/57674854/6456163) for the original answer.

[This page](https://expressjs.com/en/guide/error-handling.html) describing basic error handling in Express might be helpful to you. It's hard to give any more specific information because we do not know what type of errors you anticipate getting.

If you mean specifically with `createReadStream`, the methods discussed [here](https://github.com/adaltas/node-csv/issues/155#issuecomment-36191678) might be helpful to you:

```js
readStream = filesys.createReadStream(
  path.join(__dirname, "static", "post_request.html")
);
readStream.on("error", function() { /*handle error*/ });
res.writeHead(200, { "Content-type": "text/html" });
readStream.pipe(res);
```
