---
weight: 5
draft: false
title: "path(row1, col1, row2, col2, directions)"
---

Returns a [shortest path](https://en.wikipedia.org/wiki/Shortest_path_problem) between two cells as an array of `{row, col}` steps — excluding start, including end (the moves, not the position) — following the [search]({{< ref "search" >}}) return convention. Sugar over [reach]({{< ref "reach" >}}) plus [greedy](https://en.wikipedia.org/wiki/Greedy_algorithm) descent: from the target, step to any neighbor one ring closer; the wavefront invariant guarantees such a neighbor exists. Failure is uniform: unreachable target, filled endpoint (either one), off-board endpoint, and `start === end` all yield an empty array.

## Example

(move the mouse to lead the 🐭; click to regenerate the maze)\
{{< p5 quadrille="true" >}}
'use strict';
Quadrille.cellLength = 30;
let board, trail;
let wall, stepColor;

function setup() {
  createCanvas(15 * Quadrille.cellLength, 11 * Quadrille.cellLength);
  wall = color('#0b332b');
  stepColor = color(255, 255, 255, 120);
  board = createQuadrille(15, 11).maze(wall);
  trail = createQuadrille(15, 11);
}

function draw() {
  background('#138a72');
  trail.clear();
  board.path(0, 0, board.mouseRow, board.mouseCol).forEach(
    ({ row, col }) => trail.fill(row, col, stepColor));
  trail.fill(0, 0, '🐭');
  drawQuadrille(board, { outlineWeight: 0.5 });
  drawQuadrille(trail, { outlineWeight: 0 });
}

function mousePressed() {
  board.maze(wall);
}
{{< /p5 >}}

{{% details title="code" open=true %}}
```js
Quadrille.cellLength = 30;
let board, trail;
let wall, stepColor;

function setup() {
  createCanvas(15 * Quadrille.cellLength, 11 * Quadrille.cellLength);
  wall = color('#0b332b');
  stepColor = color(255, 255, 255, 120);
  board = createQuadrille(15, 11).maze(wall);
  trail = createQuadrille(15, 11);
}

function draw() {
  background('#138a72');
  trail.clear();
  board.path(0, 0, board.mouseRow, board.mouseCol).forEach(
    ({ row, col }) => trail.fill(row, col, stepColor));
  trail.fill(0, 0, '🐭');
  drawQuadrille(board, { outlineWeight: 0.5 });
  drawQuadrille(trail, { outlineWeight: 0 });
}

function mousePressed() {
  board.maze(wall);
}
```
{{% /details %}}

{{< callout type="info" >}}
The 🐭 sits at `(0, 0)` — always open in a generated maze — and the trail redraws each frame from `path`'s answer. Hover a wall, leave the board, or hover the 🐭 itself and the trail vanishes: failure is uniformly the empty array, with no special cases to test for.
{{< /callout >}}

{{< callout type="info" >}}
The docs say *a* shortest path, not *the*: ties are broken deterministically by neighbor order, and other equally short paths may exist. Like [reach]({{< ref "reach" >}}), `path` works on **any** quadrille — filled cells are obstacles — so move validity on a game board is simply the emptiness of the answer: `board.path(row1, col1, row2, col2).length`. No separate predicate exists, on purpose.
{{< /callout >}}

{{< callout type="info" >}}
`directions` mirrors [flood fill](https://en.wikipedia.org/wiki/Flood_fill): `4` (default) or `8` (corner-cutting); other values warn and fall back to `4`.
{{< /callout >}}

## Syntax

> `path(row1, col1, row2, col2, [directions = 4])`

## Parameters

| Param        | Description                                                                                   |
|--------------|-----------------------------------------------------------------------------------------------|
| `row1`       | Number: start row index [[0..height]]({{< ref "height" >}})                                   |
| `col1`       | Number: start column index [[0..width]]({{< ref "width" >}})                                  |
| `row2`       | Number: target row index [[0..height]]({{< ref "height" >}})                                  |
| `col2`       | Number: target column index [[0..width]]({{< ref "width" >}})                                 |
| `directions` | Number: neighborhood, `4` (default) or `8` (corner-cutting); other values warn and fall back to `4` |
