---
weight: 4
draft: false
---

# `row()`

Returns a row as a new quadrille.

# Example

{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="325" height="385" >}}
`use strict`;
Quadrille.CELL_LENGTH = 30;
let quadrille, row, hint;
let lime, olive, yellow, fuchsia;

function setup() {
  createCanvas(300, 360);
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  fuchsia = color('fuchsia');
  quadrille = createQuadrille(10, 10, 25, lime);
  quadrille.rand(20, olive).rand(30, yellow).fill(fuchsia);
  row = quadrille.row(0);
  hint = createQuadrille(10, 1);
}

function draw() {
  background('coral');
  drawQuadrille(quadrille, { outline: 'white', row: 0, col: 0 });
  drawQuadrille(hint, { outline: 'coral', row: quadrille.mouseRow });
  drawQuadrille(row, { outline: 'cyan', row: 11 });
}

function mouseMoved() {
  row = quadrille.row(quadrille.mouseRow) || row;
  return false;
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 30;
let quadrille, row, hint;
let lime, olive, yellow, fuchsia;

function setup() {
  createCanvas(300, 360);
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  fuchsia = color('fuchsia');
  quadrille = createQuadrille(10, 10, 25, lime);
  quadrille.rand(20, olive).rand(30, yellow).fill(fuchsia);
  row = quadrille.row(0);
  hint = createQuadrille(10, 1);
}

function draw() {
  background('coral');
  drawQuadrille(quadrille, { outline: 'white', row: 0, col: 0 });
  drawQuadrille(hint, { outline: 'coral', row: quadrille.mouseRow });
  drawQuadrille(row, { outline: 'cyan', row: 11 });
}

function mouseMoved() {
  row = quadrille.row(quadrille.mouseRow) || row;
  return false;
}
```
{{< /details >}}

# Syntax

> `row(row)`
 
# Parameters

| param    | description                                                                     |
|----------|---------------------------------------------------------------------------------|
| row      | Number: col number of the cell to be read [\[0..height\]]({{< ref "height" >}}) |