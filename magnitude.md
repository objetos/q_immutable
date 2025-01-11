---
weight: 2
title: "magnitude(row)"
---

Returns the number of non-empty cells of a given quadrille row.

## Example

{{< p5-global-iframe quadrille="true" width="425" height="425" >}}
'use strict';
Quadrille.cellLength = 50;
let quadrille;

function setup() {
  createCanvas(8 * Quadrille.cellLength, 8 * Quadrille.cellLength);
  quadrille = createQuadrille(int(random(3, 9)), int(random(3, 9)));
  quadrille.rand(int(quadrille.size * 0.6), '🐍');
}

function draw() {
  background('#6495ED');
  drawQuadrille(quadrille);
  text(`magnitude(${quadrille.mouseRow}): ` + 
        quadrille.magnitude(quadrille.mouseRow), 20, 20);
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
Quadrille.cellLength = 50;
let quadrille;

function setup() {
  createCanvas(8 * Quadrille.cellLength, 8 * Quadrille.cellLength);
  quadrille = createQuadrille(int(random(3, 9)), int(random(3, 9)));
  quadrille.rand(int(quadrille.size * 0.6), '🐍');
}

function draw() {
  background('#6495ED');
  drawQuadrille(quadrille);
  text(`magnitude(${quadrille.mouseRow}): ` + 
        quadrille.magnitude(quadrille.mouseRow), 20, 20);
}
```
{{< /details >}}

## Syntax

> `magnitude(row)`
 
## Parameters

| Param    | Description                                                                     |
|----------|---------------------------------------------------------------------------------|
| `row`    | Number: col number of the cell to be read [\[0..height\]]({{< ref "height" >}}) |