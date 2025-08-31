---
weight: 4
title: "ring(row, col, dimension, wrap)"
---

Returns a new quadrille representing the **square ring of neighboring cells** of radius `dimension` centered at `(row, col)`. When `wrap` is `true`, indices wrap toroidally across borders; when `false` (default), out-of-bounds positions are treated as empty. The result has size `(2·dimension + 1) × (2·dimension + 1)`.

## Example

(click on canvas, move mouse and press keys **1** to **4**)\
{{< p5-global-iframe quadrille="true" width="425" height="225" >}}
'use strict';

Quadrille.cellLength = 20;
let quadrille, ring, hint;
let dimension = 1;
let lime, olive, yellow, fuchsia;
let wrap;

function setup() {
  createCanvas(400, 200);
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  fuchsia = color('fuchsia');
  quadrille = createQuadrille(10, 10, 25, lime);
  quadrille.rand(20, olive).rand(30, yellow).fill(fuchsia);
  hint = createQuadrille(dimension * 2 + 1, dimension * 2 + 1);
  wrap = createCheckbox(' wrap', false);
  wrap.position(400 - 70, 200 - 22);
  wrap.changed(() => update());
  update();
}

function draw() {
  background('coral');
  drawQuadrille(quadrille, { outline: 'white', row: 0, col: 0 });
  drawQuadrille(hint, { outline: 'cyan', row: quadrille.mouseRow - dimension,
                        col: quadrille.mouseCol - dimension });
  drawQuadrille(ring, { outline: 'cyan', row: 0, col: 11 });
  text('dimension ' + dimension, 210, 195);
}

function mouseMoved() {
  update();
}

function keyPressed() {
  // convert string to number using +
  dimension = +key;
  dimension = constrain(dimension ||= 1, 1, 4);
  hint.width = hint.height = dimension * 2 + 1;
  update();
}

function update() {
  ring = quadrille.ring(quadrille.mouseRow,
                        quadrille.mouseCol,
                        dimension,
                        wrap.checked());
}
{{< /p5-global-iframe >}}

{{% details title="code" open=true %}}
```js
Quadrille.cellLength = 20;
let quadrille, ring, hint;
let dimension = 1;
let lime, olive, yellow, fuchsia;
let wrap;

function setup() {
  createCanvas(400, 200);
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  fuchsia = color('fuchsia');
  quadrille = createQuadrille(10, 10, 25, lime);
  quadrille.rand(20, olive).rand(30, yellow).fill(fuchsia);
  hint = createQuadrille(dimension * 2 + 1, dimension * 2 + 1);
  wrap = createCheckbox(' wrap', false);
  wrap.position(400 - 70, 200 - 22);
  wrap.changed(() => update());
  update();
}

function draw() {
  background('coral');
  drawQuadrille(quadrille, { outline: 'white', row: 0, col: 0 });
  drawQuadrille(hint, { outline: 'cyan', row: quadrille.mouseRow - dimension,
                        col: quadrille.mouseCol - dimension });
  drawQuadrille(ring, { outline: 'cyan', row: 0, col: 11 });
  text('dimension ' + dimension, 210, 195);
}

function mouseMoved() {
  update();
}

function keyPressed() {
  // convert string to number using +
  dimension = +key;
  dimension = constrain(dimension ||= 1, 1, 4);
  hint.width = hint.height = dimension * 2 + 1;
  update();
}

function update() {
  ring = quadrille.ring(quadrille.mouseRow,
                        quadrille.mouseCol,
                        dimension,
                        wrap.checked());
}
```
{{% /details %}}

## Syntax

> `ring(row, col, [dimension = 1], [wrap = false])`

## Parameters

| Param       | Description                                                                   |
|-------------|-------------------------------------------------------------------------------|
| `row`       | Number: col number of the cell to be read [[0..height]]({{< ref "height" >}}) |
| `col`       | Number: row number of the cell to be read [[0..width]]({{< ref "width" >}})   |
| `dimension` | Number: ring dimension default is 1                                           |
| `wrap`      | Boolean: when `true`, indices wrap toroidally at borders; when `false` (default), out-of-bounds cells are taken as empty |