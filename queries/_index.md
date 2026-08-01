---
bookCollapseSection: true
title: "Queries"
weight: 1
draft: false
---

These non-mutative methods provide detailed information about a given `quadrille`:  

- **[search(pattern, strict)]({{< ref "search" >}}):** Searches for cells that match a specific quadrille `pattern`, with an optional `strict` mode for exact matches of cell values.  
- **[magnitude(row)]({{< ref "magnitude" >}}):** Calculates the number of non-empty cells in the specified `row`.  
- **[reach(row, col, directions)]({{< ref "reach" >}}):** Returns the seed cell's reach as a number-field quadrille — `0` at the seed, steps-to-reach elsewhere, empty where out of reach; filled cells are obstacles.  
- **[path(row1, col1, row2, col2, directions)]({{< ref "path" >}}):** Returns a shortest path between two cells as an array of `{row, col}` steps — empty on failure, uniformly.  
- **[screenRow(pixelY, y, cellLength)]({{< ref "screen_row" >}}):** Computes the `row` index from a vertical pixel position. Rarely used—consider using the **[mouseRow]({{< ref "mouse_row" >}})** property instead for simplicity.  
- **[screenCol(pixelX, x, cellLength)]({{< ref "screen_col" >}}):** Computes the `col` index from a horizontal pixel position. Rarely used—consider using the **[mouseCol]({{< ref "mouse_col" >}})** property instead for simplicity.  