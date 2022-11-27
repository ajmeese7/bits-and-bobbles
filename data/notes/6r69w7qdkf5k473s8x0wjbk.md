
> See [here](https://stackoverflow.com/a/71191077/6456163) for the original answer.

[This answer](https://stackoverflow.com/a/41558029/6456163) helped me to solve this problem. As link-only answers are discouraged, below I have included the original answer by [bnjmnhndrsn](https://stackoverflow.com/users/3712767/bnjmnhndrsn).

I encountered this specific problem recently and creating your own transform preprocesser will solve it. This was my set up:

**package.json**

```json
"jest": {
  "moduleFileExtensions": [
    "js",
    "html"
  ],
  "transform": {
    "^.+\\.js$": "babel-jest",
    "^.+\\.html$": "<rootDir>/test/utils/htmlLoader.js"
  }
}
```

NOTE: babel-jest is normally included by default, but if you specify a custom transform preprocessor, you seem to have to include it manually.

**test/utils/htmlLoader.js:**

```javascript
const htmlLoader = require("html-loader");

module.exports = {
  process(src, filename, config, options) {
    return htmlLoader(src);
  }
}
```
