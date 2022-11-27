
### JavaScript

The first line is `constructor` and the second is `fromCharCode`. Answer heavily inspired by [this answer](https://www.codewars.com/kata/reviews/594a7f6742fc693231000022/groups/60e0577031ed6b0001806469), combined with a little [JSFuck](http://www.jsfuck.com/) magic.

To see what `s` is, use `console.log(s)` for the function contents. It appears to be the `it` function contents from Jasmine, which we have access to thanks to the Codewars test runner.

```js
const $ = (s=`${it}`) => ""
  [`c${s[6]}nst${s[36]}` + ([][[]]+[])[+[]] + `ct${s[6]}${s[36]}`]
  [`f${s[36]}${s[6]}${s[10]}C${s[48]}${s[64]}${s[36]}C${s[6]}${s[32]}${s[33]}`]
  (65,85,82,85,77)
```
