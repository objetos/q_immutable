---
weight: 1
draft: false
---

# `read()`

Returns the contents of the quadrille cell at `(row, col)`. Returns `undefined` if the cell doesn't exist.

# Example

{{< p5-global-iframe quadrille="true" width="225" height="325" >}}
`use strict`;
let quadrille;
let al;

function preload() {
  al = loadImage('../abraham_lincoln.jpg');
}

function setup() {
  createCanvas(200, 300);
  quadrille = createQuadrille([['hi', 100],
                               [null, color('magenta')],
                               [al]]);
  fill('yellow');
}

function draw() {
  background('green');
  drawQuadrille(quadrille);
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  const cell = quadrille.read(row, col);
  const x = col * Quadrille.cellLength + 5;
  const y = row * Quadrille.cellLength + 15;
  text(cell === null ? 'null' : quadrille.isImage(row, col) ? 
                                'abraham' : cell, x, y);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
let quadrille;
let al;

function preload() {
  al = loadImage('../abraham_lincoln.jpg');
}

function setup() {
  createCanvas(200, 300);
  quadrille = createQuadrille([['hi', 100],
                               [null, color('magenta')],
                               [al]]);
  fill('yellow');
}

function draw() {
  background('green');
  drawQuadrille(quadrille);
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  const cell = quadrille.read(row, col);
  const x = col * Quadrille.cellLength + 5;
  const y = row * Quadrille.cellLength + 15;
  text(cell === null ? 'null' : quadrille.isImage(row, col) ? 
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