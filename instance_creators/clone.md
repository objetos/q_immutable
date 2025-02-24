---
weight: 1
title: "clone()"
---

Returns a [shallow copy](https://en.wikipedia.org/wiki/Object_copying#Shallow_copy) of the quadrille.

## Example

(click on canvas and / or press any key)\
{{< p5-global-iframe quadrille="true" width="675" height="325" >}}
'use strict';
Quadrille.cellLength = 50;
let quadrille, clone;
let color1, color2;

function setup() {
  createCanvas(650, 300);
  color1 = color('lime');
  color2 = color('tomato');
  quadrille = createQuadrille(6, 6, 18, color1).rand(18, color2);
  clone = quadrille.clone();
}

function draw() {
  background('darkkhaki');
  drawQuadrille(quadrille, { outline: 'white' });
  drawQuadrille(clone, { outline: 'cyan', col: 7 });
}

function mouseClicked() {
  color1.setRed(random(255));
  color1.setGreen(random(255));
  color1.setBlue(random(255));
}

function keyPressed() {
  let color2Update = color(random(255), random(255), random(255));
  clone.replace(color2, color2Update);
  color2 = color2Update;
}
{{< /p5-global-iframe >}}

{{% details title="code" open=true %}}
```js
Quadrille.cellLength = 50;
let quadrille, clone;
let color1, color2;

function setup() {
  createCanvas(650, 300);
  color1 = color('lime');
  color2 = color('tomato');
  quadrille = createQuadrille(6, 6, 18, color1).rand(18, color2);
  clone = quadrille.clone();
}

function draw() {
  background('darkkhaki');
  drawQuadrille(quadrille, { outline: 'white' });
  drawQuadrille(clone, { outline: 'cyan', col: 7 });
}

function mouseClicked() {
  color1.setRed(random(255));
  color1.setGreen(random(255));
  color1.setBlue(random(255));
}

function keyPressed() {
  let color2Update = color(random(255), random(255), random(255));
  clone.replace(color2, color2Update);
  color2 = color2Update;
}
```
{{% /details %}}

## Syntax

> `clone()`
