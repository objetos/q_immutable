---
weight: 2
draft: false
---

# `ring()`

Returns the ring of neighbor cells centered at `(row, col)` as a new quadrille.

# Example

{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="625" height="425" >}}
`use strict`;
let quadrille, ring;
let dimension;
//let dimension = 1;
Quadrille.CELL_LENGTH = 20;
const w = 600 / Quadrille.CELL_LENGTH;
const h = 400 / Quadrille.CELL_LENGTH;
let lime, olive, yellow;

function setup() {
  createCanvas(600, 400);
  dimension = createSlider(1, 4, 1, 1);
  dimension.position(width - 160, height - 20);
  dimension.input(() => ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension.value()));
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  quadrille = createQuadrille(w - 2, (h / 2) - 2, 30, lime);
  quadrille.rand(60, olive);
  quadrille.rand(90, yellow);
  ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension.value());
  //ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
}

function draw() {
  background('coral');
  drawQuadrille(quadrille, { outline: 'white', row: 1, col: 1 });
  drawQuadrille(ring, { outline: 'cyan', row: h / 2, col: 1 });
}

function mouseMoved() {
  ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension.value());
  //ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
}

function keyPressed() {
  dimension = constrain(parseInt(key), 1, 4);
  //ring = quadrille.ring(quadrille.mouseRow, quadrille.mouseCol, dimension);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js

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