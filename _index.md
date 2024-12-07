---
bookCollapseSection: true  
weight: 4  
draft: false  
title: Accessors  
---

**Accessor methods** are designed to retrieve information about a `quadrille` instance or generate modified copies of it without altering the original `quadrille`. These methods are strictly **non-mutative**, ensuring the integrity of the original instance.  

Accessor methods are divided into two categories:  

## Query Accessors  

_Query accessors_ provide insights into the current state of a `quadrille`. Use these methods to inspect cell content or check specific conditions at given positions:  
- **[read(row, col)]({{< ref "read" >}}):** Returns the content of the cell at the specified `row` and `col`.  
- **[magnitude(row)]({{< ref "magnitude" >}}):** Calculates the number of non-empty cells in the specified `row`.  
- **[search(pattern, strict)]({{< ref "search" >}}):** Searches for cells that match a specific quadrille `pattern`, with an optional `strict` mode for exact matches of cell values.  
- **[isEmpty(row, col)]({{< ref "is_empty" >}}):** Checks if the specified cell at `row` and `col` is empty.  
- **[isFilled(row, col)]({{< ref "is_filled" >}}):** Checks if the specified cell at `row` and `col` contains non-empty content.  
- **[isString(row, col)]({{< ref "is_string" >}}):** Determines if the specified cell at `row` and `col` contains a string.  
- **[isNumber(row, col)]({{< ref "is_number" >}}):** Determines if the specified cell at `row` and `col` contains a number.  
- **[isColor(row, col)]({{< ref "is_color" >}}):** Checks if the specified cell at `row` and `col` contains a color.  
- **[isImage(row, col)]({{< ref "is_image" >}}):** Checks if the specified cell at `row` and `col` contains an image.  
- **[isArray(row, col)]({{< ref "is_array" >}}):** Determines if the specified cell at `row` and `col` contains an array.  
- **[isFunction(row, col)]({{< ref "is_function" >}}):** Determines if the specified cell at `row` and `col` contains a function.  
- **[isObject(row, col)]({{< ref "is_object" >}}):** Determines if the specified cell at `row` and `col` contains an object.  
- **[screenRow(pixelY, y, cellLength)]({{< ref "screen_row" >}}):** Computes the `row` index from a vertical pixel position. Rarely used—consider using the **[mouseRow]({{< ref "mouse_row" >}})** property instead for simplicity.  
- **[screenCol(pixelX, x, cellLength)]({{< ref "screen_col" >}}):** Computes the `col` index from a horizontal pixel position. Rarely used—consider using the **[mouseCol]({{< ref "mouse_col" >}})** property instead for simplicity.  

## Instance Accessors  

_Instance accessors_ generate new `quadrille` instances derived from the original. These methods allow you to create modified versions while preserving the original quadrille’s state:  
- **[clone()]({{< ref "clone" >}}):** Creates a [shallow copy](https://en.wikipedia.org/wiki/Object_copying#Shallow_copy) of the quadrille.  
- **[row(row)]({{< ref "row" >}}):** Generates a new quadrille containing only the specified `row`.  
- **[ring(row, col, dimension)]({{< ref "ring" >}}):** Produces a new quadrille representing a ring of cells around the specified `row` and `col` with the given `dimension`.  

These accessor methods provide a robust and non-intrusive way to inspect, analyze, and transform quadrilles while maintaining the original instance’s integrity.  