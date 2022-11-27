
### JavaScript

```js
// Bomb #1 - the object property gives the answer
//console.log( Bomb );
Bomb.diffuse( 42 );

// Bomb #2 - needs to be called five times
for (let i = 0; i < 5; i++) Bomb.diffuse( i );

// Bomb #3 - use the answer from Node's global vars
//console.log(global);
Bomb.diffuse( global.BombKey );

// Bomb #4 - created the function that's called, which didn't exist before
//console.log(Bomb.diffuse.toString())
diffuseTheBomb = () => true;
Bomb.diffuse();

// Bomb #5 - decoded the base64 hint
Bomb.diffuse("3.14159");

// Bomb #6 - date exactly four years ago
Bomb.diffuse(new Date().setYear(2016));

// Bomb #7 - don't let the function modify the value of the key property
Bomb.diffuse(Object.freeze({ key: 43 }));

// Bomb #8 - make the implicit valueOf function explicit, to control the behavior
const hack = {
  valueOf: () => {
    if (!this.called) {
      this.called = true;
      return 0;
    } else { return 20 }
  }
}
Bomb.diffuse(hack);

// Bomb #9 - overwrite Math.random() valueOf prototype
Math.random = function() {
  return {
    valueOf: () => {
      if (!this.called) {
        this.called = true;
        return 0.5;
      } else { return 1 }
    }
  }
}
Bomb.diffuse(42);

// Bomb #10 - overwrite valueOf for arrays, to get the sum tested (42)
Array.prototype.valueOf = function() {
  return this.reduce((acc, val) => acc + val);
}
Bomb.diffuse(new Buffer("yes").toString("base64"));
```

```js
