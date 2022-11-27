
### JavaScript

```js
class User {
  constructor() {
    this.rank = -8;
    this.progress = 0;
  }
  rank() {
    return this.rank;
  }
  progress() {
    return this.progress;
  }
  incProgress(rank) {
    // Make sure rank passed is valid
    if (rank > 8 || rank < -8 || rank == 0) {
      throw "Outside range";
      return null;
    }

    // Skip over 0 in difference calculations
    let diff = Math.abs(this.rank - rank);
    if (this.rank < 0 && rank > 0) diff -= 1;

    if (this.rank == 8) {
      // No progression once rank 8
      this.progress = 0;
    } else {
      if (this.rank == rank + 1) {
        // Activity rank is one less than user
        this.progress += 1;
      } else if (this.rank == rank) {
        // Same rank
        this.progress += 3;
      } else if (rank > this.rank) {
        this.progress += 10 * diff * diff;
      } else {
        // Because kata description does not match tests
        this.progress += 1;
      }

      this.incRank();
    }
  }
  incRank() {
    if (this.progress > 100 && this.rank != 8) {
      // Loop over progress and update rank for every 100 points
      for (let i = this.progress; i > 99; i -= 100) {
        this.rank += (this.rank == -1) ? 2 : 1;
        this.progress -= 100;

        // Reset progress if new rank is 8
        if (this.rank == 8) this.progress = 0;
      }
    }
  }
}
```

### CoffeeScript

```coffee
class User
  constructor: ->
    this.rank = -8;
    this.progress = 0;
  rank: ->
    return this.rank;
  progress: ->
    return this.progress;
  incProgress: (rank) ->
    # Make sure rank passed is valid
    if rank > 8 || rank < -8 || rank == 0
      throw "Outside range";
      return null;

    # Skip over 0 in difference calculations
    diff = Math.abs(this.rank - rank);
    if this.rank < 0 && rank > 0
      diff -= 1;

    if this.rank == 8
      # No progression once rank 8
      this.progress = 0;
    else
      if this.rank == rank + 1
        # Activity rank is one less than user
        this.progress += 1;
      else if this.rank == rank
        # Same rank
        this.progress += 3;
      else if rank > this.rank
        this.progress += 10 * diff * diff;
      else
        # Because kata description does not match tests
        this.progress += 1;

      this.incRank();
  incRank: ->
    if this.progress > 100 && this.rank != 8
      # Loop over progress and update rank for every 100 points
      while this.progress > 99
        this.rank += `(this.rank == -1) ? 2 : 1`;
        this.progress -= 100;

        # Reset progress if new rank is 8
        if this.rank == 8
          this.progress = 0;
```
