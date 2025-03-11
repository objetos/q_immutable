---
bookCollapseSection: true
title: "Cell Contents"
weight: 2
draft: false
---

These methods focus on determining the **value** and **type** of cells at a specific `(row, col)` position:  

- **[read(row, col)]({{< relref "read" >}}):** Returns the content of the cell at the specified `row` and `col`.  
- **[isValid(row, col)]({{< relref "is_valid" >}}):** Checks if the specified cell at `row` and `col` lies within bounds.  
- **[isEmpty(row, col)]({{< relref "is_empty" >}}):** Checks if the specified cell at `row` and `col` is empty.  
- **[isFilled(row, col)]({{< relref "is_filled" >}}):** Checks if the specified cell at `row` and `col` contains non-empty content.  
- **[isString(row, col)]({{< relref "is_string" >}}):** Determines if the specified cell at `row` and `col` contains a string.  
- **[isNumber(row, col)]({{< relref "is_number" >}}):** Determines if the specified cell at `row` and `col` contains a number.  
- **[isColor(row, col)]({{< relref "is_color" >}}):** Checks if the specified cell at `row` and `col` contains a color.  
- **[isImage(row, col)]({{< relref "is_image" >}}):** Checks if the specified cell at `row` and `col` contains an image.  
- **[isArray(row, col)]({{< relref "is_array" >}}):** Determines if the specified cell at `row` and `col` contains an array.  
- **[isFunction(row, col)]({{< relref "is_function" >}}):** Determines if the specified cell at `row` and `col` contains a function.  
- **[isObject(row, col)]({{< relref "is_object" >}}):** Determines if the specified cell at `row` and `col` contains an object.

## Example

(hover over a cell to view its contents)  
{{< p5-global-iframe quadrille="true" width="625" height="450" >}}
'use strict';

let ps; // Image variable
let font; // Custom font
let quadrille;
let yellow, blue, red;
let value; // Checkbox for display toggle

function preload() {
  // Load image and font in preload
  ps = loadImage('/images/pola.jpg');
  font = loadFont('/fonts/noto_sans.ttf');
}

function setup() {
  createCanvas(6 * Quadrille.cellLength, 4 * Quadrille.cellLength, WEBGL);
  textFont(font);
  yellow = color('yellow');
  blue = color('blue');
  red = color('red');
  
  // Quadrille containing cell functions and other content
  quadrille = createQuadrille([
    ['hi', 100, ps, pulse, null, 0],
    [null, yellow, pulse, ':)'],
    [null, blue, pulse, 255, ':p'],
    [null, red, null, 185, ';)', pulse]
  ]);
  // Method to determine cell type
  quadrille.cellType = function (row, col) {
    if (this.isImage(row, col)) return `image`;
    if (this.isNumber(row, col)) return `number`;
    if (this.isColor(row, col)) return `color`;
    if (this.isFunction(row, col)) return `function`;
    if (this.isObject(row, col)) return `object`;
    if (this.isString(row, col)) return `string`;
    if (this.isArray(row, col)) return `array`;
    if (this.isEmpty(row, col)) return `empty`;
  };
  // Method to determine cell value
  quadrille.cellValue = function (row, col) {
    return this.isFilled(row, col) ? this.read(row, col) : 'null';
  };
  // Create checkbox
  value = createCheckbox('Display Value', false); // Default to false
  value.position(10, height + 10); // Position checkbox
}

function draw() {
  background('black');
  // Draw q1
  drawQuadrille(quadrille, { origin: CORNER });
  // Interactive cell details for quadrille
  displayCellDetails(quadrille);
}

function displayCellDetails(quadrille, offsetX = 0) {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  // Check if row and col are within bounds
  if (
    row >= 0 && row < quadrille.height && // Row is within bounds
    col >= 0 && col < quadrille.width    // Column is within bounds
  ) {
    const x = col * Quadrille.cellLength + offsetX - width / 2 + 5;
    const y = row * Quadrille.cellLength - height / 2 + 15;
    fill('magenta');
    const prefix = `cell(${row}, ${col}) ${value.checked() ? 'value' : 'type'}:`;
    const cellString = value.checked()
      ? quadrille.cellValue(row, col)
      : quadrille.cellType(row, col);
    text(`${prefix}\n${cellString}`, x, y);
  }
}

function pulse() {
  background('lime');
  const l = Quadrille.cellLength / 2;
  const radius = map(sin(frameCount * 0.1), -1, 1, 5, l);
  noStroke();
  fill('blue');
  circle(0, 0, radius);
}
{{< /p5-global-iframe >}}

{{% details title="code" open=true %}}
```js
let ps; // Image variable
let font; // Custom font
let quadrille;
let yellow, blue, red;
let value; // Checkbox for display toggle

function preload() {
  // Load image and font in preload
  ps = loadImage('/images/pola.jpg');
  font = loadFont('/fonts/noto_sans.ttf');
}

function setup() {
  createCanvas(6 * Quadrille.cellLength, 4 * Quadrille.cellLength, WEBGL);
  textFont(font);
  yellow = color('yellow');
  blue = color('blue');
  red = color('red');
  
  // Quadrille containing cell functions and other content
  quadrille = createQuadrille([
    ['hi', 100, ps, pulse, null, 0],
    [null, yellow, pulse, ':)'],
    [null, blue, pulse, 255, ':p'],
    [null, red, null, 185, ';)', pulse]
  ]);
  // Method to determine cell type
  quadrille.cellType = function (row, col) {
    if (this.isImage(row, col)) return `image`;
    if (this.isNumber(row, col)) return `number`;
    if (this.isColor(row, col)) return `color`;
    if (this.isFunction(row, col)) return `function`;
    if (this.isObject(row, col)) return `object`;
    if (this.isString(row, col)) return `string`;
    if (this.isArray(row, col)) return `array`;
    if (this.isEmpty(row, col)) return `empty`;
  };
  // Method to determine cell value
  quadrille.cellValue = function (row, col) {
    return this.isFilled(row, col) ? this.read(row, col) : 'null';
  };
  // Create checkbox
  value = createCheckbox('Display Value', false); // Default to false
  value.position(10, height + 10); // Position checkbox
}

function draw() {
  background('black');
  // Draw q1
  drawQuadrille(quadrille, { origin: CORNER });
  // Interactive cell details for quadrille
  displayCellDetails(quadrille);
}

function displayCellDetails(quadrille, offsetX = 0) {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  // Check if row and col are within bounds
  if (
    row >= 0 && row < quadrille.height && // Row is within bounds
    col >= 0 && col < quadrille.width    // Column is within bounds
  ) {
    const x = col * Quadrille.cellLength + offsetX - width / 2 + 5;
    const y = row * Quadrille.cellLength - height / 2 + 15;
    fill('magenta');
    const prefix = `cell(${row}, ${col}) ${value.checked() ? 'value' : 'type'}:`;
    const cellString = value.checked()
      ? quadrille.cellValue(row, col)
      : quadrille.cellType(row, col);
    text(`${prefix}\n${cellString}`, x, y);
  }
}

function pulse() {
  background('lime');
  const l = Quadrille.cellLength / 2;
  const radius = map(sin(frameCount * 0.1), -1, 1, 5, l);
  noStroke();
  fill('blue');
  circle(0, 0, radius);
}
```
{{% /details %}}

{{< callout type="info" >}}  
- This example builds on the [createQuadrille(jagged_array)]({{< relref "create_quadrille_jagged_array#example" >}}) approach—check it out to understand the foundation.  
- **Dynamic Quadrille Methods**: The `cellType` and `cellValue` methods are appended to the `quadrille` object, allowing runtime customization without requiring subclasses. These methods leverage most of the cell content accessors discussed in this section (`is*` methods for type checking and `read(row, col)` for value retrieval, respectively).
- **Positioning in `displayCellDetails`**: Text positioning dynamically accounts for canvas centering and padding; abstracting this logic can simplify reuse.  
- **Interactive Features**: A checkbox toggles between displaying cell `type` or `value`, while the `pulse` function provides animated cell feedback.  
{{< /callout >}}

<!-- 
## Example 2: Using Class Inheritance to Implement `cellType` and `cellValue`

{{< p5-global-iframe quadrille="true" width="635" height="450" >}}
'use strict';

let ps; // Image variable
let font; // Custom font
let q1, q2;
let yellow, blue, red;
let value; // Checkbox for display toggle

class Cuadricula extends Quadrille {
  // Method to determine cell type
  cellType(row, col) {
    if (this.isImage(row, col)) return `image`;
    if (this.isNumber(row, col)) return `number`;
    if (this.isColor(row, col)) return `color`;
    if (this.isFunction(row, col)) return `function`;
    if (this.isObject(row, col)) return `object`;
    if (this.isString(row, col)) return `string`;
    if (this.isArray(row, col)) return `array`;
    if (this.isEmpty(row, col)) return `empty`;
  }

  // Method to determine cell value
  cellValue(row, col) {
    return this.isFilled(row, col) ? this.read(row, col) : 'null';
  }
}

function preload() {
  ps = loadImage('/images/pola.jpg'); // Load image
  font = loadFont('/fonts/noto_sans.ttf'); // Load font
}

function setup() {
  createCanvas(6 * Quadrille.cellLength + 10, 4 * Quadrille.cellLength, WEBGL);
  textFont(font);
  yellow = color('yellow');
  blue = color('blue');
  red = color('red');
  q1 = new Cuadricula([
    ['hi', 100, ps],
    [null, yellow, pulse],
    [null, blue, pulse],
    [null, red, null]
  ]);
  q2 = new Cuadricula([
    [pulse, null, 0],
    [':)'],
    [255, ':p'],
    [185, ';)', pulse]
  ]);
  // Create checkbox for value/type toggle
  value = createCheckbox('Display Value', false); // Default to false
  value.position(10, height + 10); // Position checkbox
}

function draw() {
  background('black');
  // Draw q1 and q2 side by side
  drawQuadrille(q1, { origin: CORNER });
  drawQuadrille(q2, { origin: CORNER, x: q1.width * Quadrille.cellLength + 10 }); // Offset q2 horizontally
  // Interactive cell details for q1 and q2
  displayCellDetails(q1);
  displayCellDetails(q2, q1.width * Quadrille.cellLength + 10); // Match q2's offset
}

function displayCellDetails(quadrille, offsetX = 0) {
  const row = quadrille.mouseRow;
  const col = quadrille.mouseCol;
  // Check if row and col are within bounds
  if (
    row >= 0 && row < quadrille.height && // Row is within bounds
    col >= 0 && col < quadrille.width    // Column is within bounds
  ) {
    const x = col * Quadrille.cellLength + offsetX - width / 2 + 5;
    const y = row * Quadrille.cellLength - height / 2 + 15;
    fill('magenta');
    const prefix = `cell(${row}, ${col}) ${value.checked() ? 'value' : 'type'}:`;
    const cellString = value.checked()
      ? quadrille.cellValue(row, col)
      : quadrille.cellType(row, col);
    text(`${prefix}\n${cellString}`, x, y);
  }
}

function pulse() {
  background('lime');
  const radius = map(sin(frameCount * 0.1), -1, 1, 5, Quadrille.cellLength / 2);
  noStroke();
  fill('blue');
  circle(0, 0, radius);
}
{{< /p5-global-iframe >}}
-->