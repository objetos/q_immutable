---
weight: 3
draft: false
title: "search(pattern, strict)"
---

Searches for `pattern` within this quadrille and returns an array of `{row, col}` matches. The array length may be 0 if no matches are found. In `strict` mode (i.e., `strict = true`), for a `pattern` to be successfully found within a `quadrille`, the values inside the `pattern` must be identical instances to those in the `quadrille`. Conversely, in non-`strict` mode (i.e., `strict = false`), only the presence of filled cells is required, without regard for their contents.

For instance, here:
```js
let value;
let quadrille, pattern;

function setup() {
  value = createColor('blue'); // 'blue' is created once and stored in 'value'
  quadrille = createQuadrille([125, value, 'hi']); 
  pattern = createQuadrille([value, 'hi']);
  // quadrille and pattern share the same 'blue' instance stored in 'value'
  // quadrille.read(0, 1) === pattern.read(0, 0) // is true
  quadrille.search(pattern, true); // finds it
  // quadrille.search(pattern, false); // would find it as well
}
```
both `quadrille` and `pattern` are using the same instance of the color `'blue'` stored in the variable `value`. Therefore, when comparing the values in `quadrille` and `pattern`, they match in memory reference.

Whereas here:
```js
let quadrille, pattern;

function setup() {
  quadrille = createQuadrille([125, createColor('blue'), 'hi']);
  pattern = createQuadrille([createColor('blue'), 'hi']);
  // quadrille and pattern have their own separate instances of 'blue'
  // quadrille.read(0, 1) === pattern.read(0, 0) // is false
  quadrille.search(pattern, true); // doesn't find
  // quadrille.search(pattern, false); // would find it
}
```
`quadrille` and `pattern` are using different instances of the color `'blue'`, created separately by two calls to `createColor('blue')`. Even though both instances represent the color `'blue'`, they are distinct objects in memory. Therefore, when comparing the values in `quadrille` and `pattern`, they don't match in memory reference.

## Example

(click cells to edit pattern and quadrille; left / right arrow keys to move to next found hit)\
{{< p5-global-iframe quadrille="true" width="625" height="470" >}}
'use strict';
const COLS = 20, ROWS = 14;
let grid, pattern, board, hint;
let col1 = 7, row1 = 1;
let col2 = 1, row2 = 6;
let colors;
let back, tomatoColor, limeColor, slateblueColor;
let hit = 0, hits;
let mode, strict;

function setup() {
  back = color('darkkhaki');
  tomatoColor = color('tomato');
  limeColor = color('lime');
  slateblueColor = color('slateblue');
  colors = {
    tomato: tomatoColor,
    lime: limeColor,
    slateblue: slateblueColor
  };
  Quadrille.cellLength = 30;
  createCanvas(COLS * Quadrille.cellLength, ROWS * Quadrille.cellLength);
  grid = createQuadrille(COLS, ROWS, COLS * ROWS, back);
  mode = createSelect();
  mode.option('tomato');
  mode.option('lime');
  mode.option('slateblue');
  mode.option('clear');
  mode.selected('clear');
  mode.position(10, height + 15);
  strict = createCheckbox('strict', false);
  strict.position(100, height + 15);
  strict.style('color', 'magenta');
  reset();
  update();
}

function draw() {
  drawQuadrille(grid, { outlineWeight: 0.5 });
  drawQuadrille(pattern, { col: col1, row: row1, outline: 'yellow' });
  drawQuadrille(board, { col: col2, row: row2, outline: 'magenta' });
  if (hits.length > 0) {
    hit = ((hit % hits.length) + hits.length) % hits.length;
    drawQuadrille(hint, { row: row2 + hits[hit].row, 
                          col: col2 + hits[hit].col, outline: 'yellow' });
  }
}

function keyPressed() {
  if (hits.length) {
    hit += (keyCode === LEFT_ARROW) ? -1 : (keyCode === RIGHT_ARROW) ? 1 : 0;
  }
  if (key === 'r') {
    reset();
    update();
  }
}

function mouseClicked() {
  fillQuadrille(pattern);
  fillQuadrille(board);
  update();
}

function fillQuadrille(quadrille) {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  const value = mode.value();
  mode.value() === 'clear' ? quadrille.clear(row, col) : 
                             quadrille.fill(row, col, colors[mode.value()]);
}

function reset() {
  pattern = createQuadrille(int(random(4, 8)), int(random(2, 5)));
  pattern.rand(int(pattern.size * 0.3), tomatoColor);
  board = createQuadrille(18, 7);
  board.rand(30, tomatoColor).rand(30, limeColor).rand(30, slateblueColor);
}

function update() {
  hits = board.search(pattern, strict.checked());
  hint = pattern.clone();
  hint = Quadrille.neg(hint, color(red(back), green(back), blue(back), 210));
}
{{< /p5-global-iframe >}}

{{< details title="code" open=false >}}
```js
const COLS = 20, ROWS = 14;
let grid, pattern, board, hint;
let col1 = 7, row1 = 1;
let col2 = 1, row2 = 6;
let colors;
let back, tomatoColor, limeColor, slateblueColor;
let hit = 0, hits;
let mode, strict;

function setup() {
  back = color('darkkhaki');
  tomatoColor = color('tomato');
  limeColor = color('lime');
  slateblueColor = color('slateblue');
  colors = {
    tomato: tomatoColor,
    lime: limeColor,
    slateblue: slateblueColor
  };
  Quadrille.cellLength = 30;
  createCanvas(COLS * Quadrille.cellLength, ROWS * Quadrille.cellLength);
  grid = createQuadrille(COLS, ROWS, COLS * ROWS, back);
  mode = createSelect();
  mode.option('tomato');
  mode.option('lime');
  mode.option('slateblue');
  mode.option('clear');
  mode.selected('clear');
  mode.position(10, height + 15);
  strict = createCheckbox('strict', false);
  strict.position(100, height + 15);
  strict.style('color', 'magenta');
  reset();
  update();
}

function draw() {
  drawQuadrille(grid, { outlineWeight: 0.5 });
  drawQuadrille(pattern, { col: col1, row: row1, outline: 'yellow' });
  drawQuadrille(board, { col: col2, row: row2, outline: 'magenta' });
  if (hits.length > 0) {
    hit = ((hit % hits.length) + hits.length) % hits.length;
    drawQuadrille(hint, { row: row2 + hits[hit].row, 
                          col: col2 + hits[hit].col, outline: 'yellow' });
  }
}

function keyPressed() {
  if (hits.length) {
    hit += (keyCode === LEFT_ARROW) ? -1 : (keyCode === RIGHT_ARROW) ? 1 : 0;
  }
  if (key === 'r') {
    reset();
    update();
  }
}

function mouseClicked() {
  fillQuadrille(pattern);
  fillQuadrille(board);
  update();
}

function fillQuadrille(quadrille) {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  const value = mode.value();
  mode.value() === 'clear' ? quadrille.clear(row, col) : 
                             quadrille.fill(row, col, colors[mode.value()]);
}

function reset() {
  pattern = createQuadrille(int(random(4, 8)), int(random(2, 5)));
  pattern.rand(int(pattern.size * 0.3), tomatoColor);
  board = createQuadrille(18, 7);
  board.rand(30, tomatoColor).rand(30, limeColor).rand(30, slateblueColor);
}

function update() {
  hits = board.search(pattern, strict.checked());
  hint = pattern.clone();
  hint = Quadrille.neg(hint, color(red(back), green(back), blue(back), 210));
}
```
{{< /details >}}

{{< callout type="info" >}}
**Observations**  
- The `reset` function initializes the `pattern` and `board` quadrilles with random sizes and colors. The `pattern` is smaller and random, while the `board` represents the larger search area, containing various colors. This setup is useful for generating new data sets to test the `search` functionality.  
- The `update` function recalculates the matches (stored in the `hits` array) between the `pattern` and the `board` quadrilles. It also creates a `hint` quadrille, which visually highlights the current `pattern` match during navigation. Without `update`, the application would not reflect changes after editing or randomizing quadrilles.  
{{< /callout >}}

## Syntax

> `search(pattern, [strict = false])`

## Parameters

| Param | Description                                                                                                      |
|-----------|------------------------------------------------------------------------------------------------------------------|
| `pattern` | Quadrille: pattern to be searched                                                                                |
| `strict`  | Boolean: If `false` (default), searches only the presence of filled cells; if `true`, searches for identical value instances |