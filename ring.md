---
weight: 5
draft: false
---

# `ring()`

Returns the ring of neighbor cells centered at `(row, col)` as a new quadrille.

# Example

(click on canvas, move mouse and press keys **1** to **4**)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="425" height="225" >}}
`use strict`;
Quadrille.cellLength = 20;
let quadrille, ring, hint;
let dimension = 1;
let lime, olive, yellow, fuchsia;

function setup() {
  createCanvas(400, 200);
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  fuchsia = color('fuchsia');
  quadrille = createQuadrille(10, 10, 25, lime);
  quadrille.rand(20, olive).rand(30, yellow).fill(fuchsia);
  ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
  hint = createQuadrille(dimension * 2 + 1, dimension * 2 + 1);
}

function draw() {
  background('coral');
  drawQuadrille(quadrille, { outline: 'white', row: 0, col: 0 });
  drawQuadrille(hint, { outline: 'coral', row: quadrille.mouseRow - dimension,
                        col: quadrille.mouseCol - dimension });
  drawQuadrille(ring, { outline: 'cyan', row: 0, col: 11 });
  text('dimension ' + dimension, 210, 195);
}

function mouseMoved() {
  ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
  return false;
}

function keyPressed() {
  // convert string to number using +
  dimension = +key;
  dimension = constrain(dimension ||= 1, 1, 4);
  ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
  hint.width = hint.height = dimension * 2 + 1;
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.cellLength = 20;
let quadrille, ring, hint;
let dimension = 1;
let lime, olive, yellow, fuchsia;

function setup() {
  createCanvas(400, 200);
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  fuchsia = color('fuchsia');
  quadrille = createQuadrille(10, 10, 25, lime);
  quadrille.rand(20, olive).rand(30, yellow).fill(fuchsia);
  ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
  hint = createQuadrille(dimension * 2 + 1, dimension * 2 + 1);
}

function draw() {
  background('coral');
  drawQuadrille(quadrille, { outline: 'white', row: 0, col: 0 });
  drawQuadrille(hint, { outline: 'coral', row: quadrille.mouseRow - dimension,
                        col: quadrille.mouseCol - dimension });
  drawQuadrille(ring, { outline: 'cyan', row: 0, col: 11 });
  text('dimension ' + dimension, 210, 195);
}

function mouseMoved() {
  ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
  return false;
}

function keyPressed() {
  // convert string to number using +
  dimension = +key;
  dimension = constrain(dimension ||= 1, 1, 4);
  ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
  hint.width = hint.height = dimension * 2 + 1;
}
```
{{< /details >}}

# Syntax

> `ring(row, col, [dimension = 1])`

# Parameters

| param     | description                                                                     |
|-----------|---------------------------------------------------------------------------------|
| row       | Number: col number of the cell to be read [\[0..height\]]({{< ref "height" >}}) |
| col       | Number: row number of the cell to be read [\[0..width\]]({{< ref "width" >}})   |
| dimension | Number: ring dimension default is 1                                             |