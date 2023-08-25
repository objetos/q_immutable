---
weight: 1
draft: false
---

# `read()`

Returns the contents of the quadrille cell at `(row, col)`. Returns `undefined` if the cell doesn't exist.

# Example

{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="225" height="325" >}}
`use strict`;
let quadrille;
let al;

function preload() {
  al = loadImage('../abraham_lincoln.jpg');
}

function setup() {
  createCanvas(200, 300);
  quadrille = createQuadrille([['hi', 100],
                               [null, color('red')],
                               [al]]);
  fill('yellow');
}

function draw() {
  background('blue');
  drawQuadrille(quadrille);
  const cell = quadrille.read(quadrille.mouseRow, quadrille.mouseCol);
  const x = quadrille.mouseCol * Quadrille.CELL_LENGTH + 5;
  const y = quadrille.mouseRow * Quadrille.CELL_LENGTH + 15;
  text(cell === null ? 'null' : cell instanceof p5.Image ? 
                                'abraham' : cell, x, y);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
let quadrille;
let al;

function preload() {
  al = loadImage('abraham_lincoln.jpg');
}

function setup() {
  createCanvas(200, 300);
  quadrille = createQuadrille([['hi', 100],
                               [null, color('red')],
                               [al]]);
  fill('yellow');
}

function draw() {
  background('blue');
  drawQuadrille(quadrille);
  const cell = quadrille.read(quadrille.mouseRow, quadrille.mouseCol);
  const x = quadrille.mouseCol * Quadrille.CELL_LENGTH + 5;
  const y = quadrille.mouseRow * Quadrille.CELL_LENGTH + 15;
  text(cell === null ? 'null' : cell instanceof p5.Image ? 
                                'abraham' : cell, x, y);
}
```
{{< /details >}}

# Syntax

> `read(row, col)`

# Parameters

| param    | description                                                                     |
|----------|---------------------------------------------------------------------------------|
| row      | Number: col number of the cell to be read [\[0..height\]]({{< ref "height" >}}) |
| col      | Number: row number of the cell to be read [\[0..width\]]({{< ref "width" >}})   |