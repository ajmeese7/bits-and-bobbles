
### JavaScript

```js
var mapSize = 8;
var uninhabitedIslands = [],
    marineIslands = [];

function conquerIsland(map) {
  findIslands(map);

  if (uninhabitedIslands.length == 1 && marineIslands.length == 0) {
    return uninhabitedIslands[0];
  } else if (marineIslands.length == 1 && !uninhabitedIslands) {
    return marineIslands[0];
  } else {
    var marineSolutions = getClosest([], marineIslands, true);
    var finalSolutions = getClosest(marineSolutions, uninhabitedIslands, false);
    if (finalSolutions.length == 1) finalSolutions = finalSolutions[0];

    return finalSolutions;
  }
}

function findIslands(map) {
  // Reset the arrays
  uninhabitedIslands = [];
  marineIslands = [];

  // iterate over the whole map, recording islands
  for (var x = 0; x < mapSize; x++) {
    for (var y = 0; y < mapSize; y++) {
      var coordinates = [x, y];
      var currentChar = map[x][y].charAt(0);
      if (currentChar == 'u') {
        // Uninhabited island; highest priority
        uninhabitedIslands.push(coordinates);
      } else if (currentChar == 'm') {
        // Marine island; lower priority
        marineIslands.push(coordinates);
      }
    }
  }
}

function getDistance(coordinates) {
  var x = coordinates[0], y = coordinates[1];
  return x + y;
}

/**
 * Returns the array of the closest island or islands.
 */
function getClosest(solutions, islands, marine) {
  var minDistance = [999, 'm'];

  for (let i = 0; i < islands.length; i++) {
    var currentIsland = islands[i];
    var distance = getDistance(currentIsland);

    if (distance <= minDistance[0]) {
      let previousMin = minDistance[1];
      minDistance = [distance, marine ? 'm' : 'u'];

      if (solutions[0] && distance == getDistance(solutions[0])) {
        // Already a solution of equivalent distance
        if (!marine && previousMin === 'u') {
          solutions.push(currentIsland);
        } else {
          solutions = [currentIsland];
        }
      } else {
        // Lowest solution found so far
        solutions = [currentIsland];
      }
    }
  }

  return solutions;
}
```
