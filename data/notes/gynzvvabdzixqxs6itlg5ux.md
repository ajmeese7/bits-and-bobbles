
## Instructions

Given a list of white pawns on a chessboard (any number of them, meaning from 0 to 64 and with the possibility to be positioned everywhere), determine how many of them have their backs covered by another. Pawns attacking upwards since we have only white ones.

Please remember that a pawn attack(and defend as well) only the 2 square on the sides in front of him. https://en.wikipedia.org/wiki/Pawn_(chess)#/media/File:Pawn_(chess)_movements.gif

### JavaScript

```js
// https://stackoverflow.com/a/12504132/6456163
String.prototype.nextChar = function() {
  return String.fromCharCode(this.charCodeAt(0) + 1);
}
String.prototype.prevChar = function() {
  return String.fromCharCode(this.charCodeAt(0) - 1);
}

function coveredPawns(pawns) {
  const covered = [];

  pawns.forEach((pawn) => {
    const nextRow = parseInt(pawn[1]) + 1;
    const left = pawn[0].nextChar() + nextRow;
    const right = pawn[0].prevChar() + nextRow;

    for (const pawn of [left, right])
      if (pawns.includes(pawn) && !covered.includes(pawn))
        covered.push(pawn);
  });

  return covered.length;
}
```

### Python

```py
def covered_pawns(pawns):
    covered = []

    for pawn in pawns:
        nextRow = int(pawn[1]) + 1
        left = chr(ord(pawn[0]) + 1) + str(nextRow)
        right = chr(ord(pawn[0]) - 1) + str(nextRow)

        for pawn in [left, right]:
            if (pawn in pawns and pawn not in covered):
                covered.append(pawn)

    return len(covered)
```
