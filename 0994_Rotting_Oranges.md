```javascript
var orangesRotting = function (grid: number[][]) {
  // get rows and cols length
  const rows = grid.length,
    cols = grid[0].length;

  // define neighbor directions for rows and cols
  const rowDirections = [1, -1, 0, 0],
    colDirections = [0, 0, 1, -1];

  // define our que as row, col tuples
  let queue: [number, number][] = [],
    // initialize minute and #of fresh oranges
    minute = 0,
    fresh = 0;

  // loop thorugh matrix
  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      // if we find rot, we push to queue
      if (grid[r][c] === 2) {
        queue.push([r, c]);
      }

      // if orange is fresh
      else if (grid[r][c] === 1) {
        // we found a fresh orange
        fresh++;
      }
    }
  }

  // loop through while there are fresh oranges and a queue
  while (fresh && queue.length) {
    // look at next
    const next: [number, number][] = [];

    // go through quue
    for (let [row, col] of queue) {
      // looking at neighbors
      for (let i = 0; i < rowDirections.length; i++) {
        const rowNeighbor = row + rowDirections[i],
          colNeighbor = col + colDirections[i];

        // checks to see if in bounds or if there are fresh oranges as neighbors
        if (
          rowNeighbor < rows &&
          rowNeighbor >= 0 &&
          colNeighbor < cols &&
          colNeighbor >= 0 &&
          grid[rowNeighbor][colNeighbor] === 1
        ) {
          // one less fresh orange
          fresh--;

          // update this to be a rotten orange in grid
          grid[rowNeighbor][colNeighbor] = 2;

          // add to next
          next.push([rowNeighbor, colNeighbor]);
        }
      }
    }

    // after looking at all directions, increment our timer
    minute++;

    // update our queue
    queue = next;
  }

  // if we still have fresh oranges, -1 else return time
  return !!fresh ? -1 : minute;
};
```
