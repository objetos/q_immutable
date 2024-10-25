---
weight: 4
draft: false
title: "row(row)"
---

Devuelve una fila como una nueva cuadrícula.

## Ejemplo

{{< p5-global-iframe quadrille="true" width="325" height="385" >}}
`use strict`;
Quadrille.cellLength = 30;
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
Quadrille.cellLength = 30;
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

## Sintaxis

> `row(row)`

## Parámetros

| parámetro | descripción                                                            |
|-----------|------------------------------------------------------------------------|
| row       | Número: número de la fila a leer [\[0..height\]]({{< ref "height" >}}) |