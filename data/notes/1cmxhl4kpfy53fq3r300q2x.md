
> See [here](https://stackoverflow.com/a/57680411/6456163) for the original answer.

What I would suggest is an array filled with objects. What you are trying to do right now is not valid. Here's an example of the proper formatting:

```js
[
  { name: 'test1', id: 1 },
  { name: 'test2', id: 2 },
]
```

This is how I would refactor your code:

```js
let data = [];
const res = JSON.parse(body);

for (let i = 0; i < res.teams.length; i++) {
  data.push({ name: res.teams[i].name, id: res.teams[i].id });
}
console.log(data);
```

This way you will have to loop over the array to access each object, such as getting `{ name: 'test1', id: 1 }` by accessing `data[0]`.
