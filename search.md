---
weight: 6
draft: false
---

# search()

Searches for `pattern` within this quadrille and returns an array of `{row, col}` matches. The array length may be 0 if no matches are found.

# Example

(mouse click to edit pattern and quadrille; left / right arrow keys to move to next found hit)\
{{< p5-global-iframe lib1="https://cdn.jsdelivr.net/gh/objetos/p5.quadrille.js/p5.quadrille.js" width="625" height="470" >}}
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
  Quadrille.CELL_LENGTH = 30;
  createCanvas(COLS * Quadrille.CELL_LENGTH, ROWS * Quadrille.CELL_LENGTH);
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
  hint = Quadrille.NEG(hint, color(red(back), green(back), blue(back), 210));
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
  Quadrille.CELL_LENGTH = 30;
  createCanvas(COLS * Quadrille.CELL_LENGTH, ROWS * Quadrille.CELL_LENGTH);
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
  hint = Quadrille.NEG(hint, color(red(back), green(back), blue(back), 210));
}
```
{{< /details >}}

# Syntax

> `search(pattern, [strict])`

# Parameters

| parameter | description                                                                                                      |
|-----------|------------------------------------------------------------------------------------------------------------------|
| pattern   | Quadrille: pattern to be searched                                                                                |
| strict    | Boolean: If `false` (default), searches only for coincidences; if `true`, searches for both coincides and values |