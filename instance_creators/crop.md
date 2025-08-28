---
weight: 4
title: "crop(row, col, width, height)"
---

Returns the rectangular **region** anchored at `(row, col)` as a **new quadrille**.

* `width > 0` grows **right**, `width < 0` grows **left**.
* `height > 0` grows **down**, `height < 0` grows **up**.
* If either `width` or `height` is `0`, nothing is cropped.
* If the rectangle extends beyond the grid, the out-of-bounds area is filled with empty cells, so the result is always a quadrille of size `width × height`.

## Example

(click on canvas, move the mouse, and press the arrow keys)
{{< p5-global-iframe quadrille="true" width="425" height="225" >}}
'use strict';

Quadrille.cellLength = 20;
let quadrille, cropped, hint;
let w = -3, h = 3;
let lime, olive, yellow, fuchsia;

function setup() {
  createCanvas(400, 200);
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  fuchsia = color('fuchsia');
  quadrille = createQuadrille(10, 10, 25, lime);
  quadrille.rand(20, olive).rand(30, yellow).fill(fuchsia);
  update();
}

function draw() {
  background('coral');
  // Base quadrille (left)
  drawQuadrille(quadrille, { outline: 'white', row: 0, col: 0 });
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  // Hint rectangle (only if defined)
  if (hint) {
    const absW = Math.abs(w), absH = Math.abs(h);
    const top  = (h >= 0 ? row : row - (absH - 1));
    const left = (w >= 0 ? col : col - (absW - 1));
    drawQuadrille(hint, { outline: 'cyan', row: top, col: left });
  }
  // Cropped preview on the right (only if defined)
  if (cropped) {
    drawQuadrille(cropped, { outline: 'cyan', row: 0, col: 11 });
  }
  noStroke();
  fill(0);
  text(`w ${w}  h ${h}`, 210, 195);
}

function mouseMoved() {
  update();
}

function keyPressed() {
  if (key === 'ArrowLeft')  w--;
  else if (key === 'ArrowRight') w++;
  else if (key === 'ArrowUp')    h--;
  else if (key === 'ArrowDown')  h++;
  update();
  return false; // prevent page scroll
}

function update() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  // If either dimension is zero, skip drawing both hint and result
  if (w === 0 || h === 0) {
    hint = undefined;
    cropped = undefined;
    return;
  }
  // Keep the hint sized to |w| × |h|
  hint = createQuadrille(Math.abs(w), Math.abs(h));
  // Try cropping; may return undefined if out of bounds
  cropped = quadrille.crop(row, col, w, h);
}
{{< /p5-global-iframe >}}

{{% details title="code" open=true %}}
```js
Quadrille.cellLength = 20;
let quadrille, cropped, hint;
let w = -3, h = 3;
let lime, olive, yellow, fuchsia;

function setup() {
  createCanvas(400, 200);
  lime = color('lime');
  yellow = color('yellow');
  olive = color('olive');
  fuchsia = color('fuchsia');
  quadrille = createQuadrille(10, 10, 25, lime);
  quadrille.rand(20, olive).rand(30, yellow).fill(fuchsia);
  update();
}

function draw() {
  background('coral');
  // Base quadrille (left)
  drawQuadrille(quadrille, { outline: 'white', row: 0, col: 0 });
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  // Hint rectangle (only if defined)
  if (hint) {
    const absW = Math.abs(w), absH = Math.abs(h);
    const top  = (h >= 0 ? row : row - (absH - 1));
    const left = (w >= 0 ? col : col - (absW - 1));
    drawQuadrille(hint, { outline: 'cyan', row: top, col: left });
  }
  // Cropped preview on the right (only if defined)
  if (cropped) {
    drawQuadrille(cropped, { outline: 'cyan', row: 0, col: 11 });
  }
  noStroke();
  fill(0);
  text(`w ${w}  h ${h}`, 210, 195);
}

function mouseMoved() {
  update();
}

function keyPressed() {
  if (key === 'ArrowLeft')  w--;
  else if (key === 'ArrowRight') w++;
  else if (key === 'ArrowUp')    h--;
  else if (key === 'ArrowDown')  h++;
  update();
  return false; // prevent page scroll
}

function update() {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  // If either dimension is zero, skip drawing both hint and result
  if (w === 0 || h === 0) {
    hint = undefined;
    cropped = undefined;
    return;
  }
  // Keep the hint sized to |w| × |h|
  hint = createQuadrille(Math.abs(w), Math.abs(h));
  // Try cropping; may return undefined if out of bounds
  cropped = quadrille.crop(row, col, w, h);
}
```
{{% /details %}}

## Syntax

> `crop(row, col, width, height)`

## Parameters

| Param    | Description                                                                  |
| -------- | ---------------------------------------------------------------------------- |
| `row`    | Number: anchor row (the starting cell’s row)                                 |
| `col`    | Number: anchor column (the starting cell’s column)                           |
| `width`  | Number: rectangle width; `> 0` to the right, `< 0` to the left; `0` disables |
| `height` | Number: rectangle height; `> 0` downward, `< 0` upward; `0` disables         |