---
bookCollapseSection: true
title: "Queries"
weight: 1
draft: false
---

These non-mutative methods provide detailed information about a given `quadrille`:  

- **[search(pattern, strict)]({{< ref "search" >}}):** Searches for cells that match a specific quadrille `pattern`, with an optional `strict` mode for exact matches of cell values.  
- **[magnitude(row)]({{< ref "magnitude" >}}):** Calculates the number of non-empty cells in the specified `row`.  
- **[screenRow(pixelY, y, cellLength)]({{< ref "screen_row" >}}):** Computes the `row` index from a vertical pixel position. Rarely used—consider using the **[mouseRow]({{< ref "mouse_row" >}})** property instead for simplicity.  
- **[screenCol(pixelX, x, cellLength)]({{< ref "screen_col" >}}):** Computes the `col` index from a horizontal pixel position. Rarely used—consider using the **[mouseCol]({{< ref "mouse_col" >}})** property instead for simplicity.  