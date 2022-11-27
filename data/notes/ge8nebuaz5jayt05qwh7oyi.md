
> See [here](https://stackoverflow.com/a/72393715/6456163) for the original answer.

One answer to this question can be found [here](https://stackoverflow.com/a/11365819/6456163), if you are only interested in getting the `nth` row of a table via JavaScript:

```js
var cells = document.getElementById('table').getElementsByTagName('td');
```

This will contain all your table cells. Use array notation to access a specific one:

```js
cells[4]
```

Here's a quick demo which changes the background color:

http://jsfiddle.net/jackwanders/W7RAu/
