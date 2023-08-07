---
weight: 5
draft: false
---

# Quadrille immutable methods

The `quadrille` immutable methods are the following:

1. `isEmpty(row, col)`: returns `true` if cell found at `(row, col)` is empty and `false` otherwise.
2. `isFilled(row, col)`: returns `true` if cell found at `(row, col)` is filled and `false` otherwise.
3. `isColor(row, col)`: returns `true` if cell found at `(row, col)` is a [color](https://p5js.org/reference/#/p5/p5.Color) and `false` otherwise.
4. `isNumber(row, col)`: returns `true` if cell found at `(row, col)` is a number and `false` otherwise.
5. `isString(row, col)`: returns `true` if cell found at `(row, col)` is a string and `false` otherwise.
6. `isImage(row, col)`: returns `true` if cell found at `(row, col)` is empty an [image](https://p5js.org/reference/#/p5.Image) or a [graphics](https://p5js.org/reference/#/p5.Graphics) and `false` otherwise.
7. `isArray(row, col)`: returns `true` if cell found at `(row, col)` is an array and `false` otherwise.
8. `isObject(row, col)`: returns `true` if cell found at `(row, col)` is an object and `false` otherwise.
9.  `read(row, col)`: returns the contents of the quadrille cell at `(row, col)`. Returns `undefined` if the cell doesn't exist.
10. `ring(row, col, [dimension=1])`: returns the ring of neighbor cells centered at (row, col) as a new quadrille.
11. `magnitude(row)`: returns the number of non-empty cells of a given quadrille `row`.
12. `clone()`: returns a [shallow copy](https://en.wikipedia.org/wiki/Object_copying#Shallow_copy) of the quadrille.

These methods are pretty straightforward and its usage is left out as an exercise.