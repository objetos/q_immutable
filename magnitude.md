---
weight: 3
draft: false
---

# `magnitude()`

Returns the number of non-empty cells of a given quadrille row.

# Example

{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="425" height="425" >}}
`use strict`;
Quadrille.CELL_LENGTH = 50;
let quadrille;

function setup() {
  createCanvas(8 * Quadrille.CELL_LENGTH, 8 * Quadrille.CELL_LENGTH);
  quadrille = createQuadrille(int(random(1, 9)), int(random(1, 9)),
                              int(random(5, 30)), '🐍');
}

function draw() {
  background('#6495ED');
  drawQuadrille(quadrille);
  text(`magnitude(${quadrille.mouseRow}) ` + 
        quadrille.magnitude(quadrille.mouseRow), 20, 20);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.CELL_LENGTH = 50;
let quadrille;

function setup() {
  createCanvas(8 * Quadrille.CELL_LENGTH, 8 * Quadrille.CELL_LENGTH);
  quadrille = createQuadrille(int(random(1, 9)), int(random(1, 9)),
                              int(random(5, 30)), '🐍');
}

function draw() {
  background('#6495ED');
  drawQuadrille(quadrille);
  text(`magnitude(${quadrille.mouseRow}) ` + 
        quadrille.magnitude(quadrille.mouseRow), 20, 20);
}
```
{{< /details >}}

# Syntax

> `magnitude(row)`
 
# Parameters

| param    | description                                                                     |
|----------|---------------------------------------------------------------------------------|
| row      | Number: col number of the cell to be read [\[0..height\]]({{< ref "height" >}}) |