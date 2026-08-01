---
weight: 4
draft: false
title: "reach(row, col, directions)"
---

Returns the seed cell's reach as a **number-field quadrille** — `0` at the seed, steps-to-reach elsewhere, and empty where out of reach — computed as a [breadth-first](https://en.wikipedia.org/wiki/Breadth-first_search) wavefront over any quadrille: filled cells are obstacles, empty cells are passable. The field renders as gray levels for free, and one field serves any number of agents: compute it from the *target* and every agent descends it. Seeding on a filled or invalid cell yields a fully empty field — an agent cannot stand in a wall.

## Example

(move the mouse to seed the field; click to regenerate the maze)\
{{< p5 quadrille="true" >}}
'use strict';
Quadrille.cellLength = 30;
let board;
let wall;
let dirs;

function setup() {
  createCanvas(15 * Quadrille.cellLength, 11 * Quadrille.cellLength);
  wall = color('#0b332b');
  board = createQuadrille(15, 11).maze(wall);
  dirs = createCheckbox('8 directions', false);
  dirs.position(10, height + 15);
  dirs.style('color', 'magenta');
}

function draw() {
  background('#138a72');
  const field = board.reach(board.mouseRow, board.mouseCol, dirs.checked() ? 8 : 4);
  drawQuadrille(field, {
    outlineWeight: 0,
    numberDisplay: ({ value, cellLength }) => {
      noStroke();
      fill(constrain(255 - 5 * value, 40, 255));
      rect(0, 0, cellLength, cellLength);
    }
  });
  drawQuadrille(board, { outlineWeight: 0.5 });
}

function mousePressed() {
  board.maze(wall);
}
{{< /p5 >}}

{{% details title="code" open=true %}}
```js
Quadrille.cellLength = 30;
let board;
let wall;
let dirs;

function setup() {
  createCanvas(15 * Quadrille.cellLength, 11 * Quadrille.cellLength);
  wall = color('#0b332b');
  board = createQuadrille(15, 11).maze(wall);
  dirs = createCheckbox('8 directions', false);
  dirs.position(10, height + 15);
  dirs.style('color', 'magenta');
}

function draw() {
  background('#138a72');
  const field = board.reach(board.mouseRow, board.mouseCol, dirs.checked() ? 8 : 4);
  drawQuadrille(field, {
    outlineWeight: 0,
    numberDisplay: ({ value, cellLength }) => {
      noStroke();
      fill(constrain(255 - 5 * value, 40, 255));
      rect(0, 0, cellLength, cellLength);
    }
  });
  drawQuadrille(board, { outlineWeight: 0.5 });
}

function mousePressed() {
  board.maze(wall);
}
```
{{% /details %}}

{{< callout type="info" >}}
The wavefront brightens toward the seed (`0` renders lightest under this `numberDisplay` override) and vanishes where it cannot go: hover a wall — or leave the board — and the field goes fully empty. With **8 directions** the wave cuts corners, mirroring [flood fill](https://en.wikipedia.org/wiki/Flood_fill) semantics; any other `directions` value warns and falls back to `4`.
{{< /callout >}}

{{< callout type="info" >}}
`reach` is defined and meaningful on **any** quadrille, not only mazes: on a game board it is pathfinding distance around the pieces; on an empty quadrille it is plain grid distance. Its natural companion is [path]({{< ref "path" >}}), which descends the field.
{{< /callout >}}

{{< callout type="info" >}}
Emptiness is the field's failure signal, and it composes with the [read]({{< ref "read" >}}) convention: `field.isEmpty(row, col)` reads as *out of reach* — including out-of-bounds cells, since an out-of-bounds `read` returns `undefined`, which counts as empty.
{{< /callout >}}

## Syntax

> `reach(row, col, [directions = 4])`

## Parameters

| Param        | Description                                                                                   |
|--------------|-----------------------------------------------------------------------------------------------|
| `row`        | Number: seed row index [[0..height]]({{< ref "height" >}})                                    |
| `col`        | Number: seed column index [[0..width]]({{< ref "width" >}})                                   |
| `directions` | Number: neighborhood, `4` (default) or `8` (corner-cutting); other values warn and fall back to `4` |
