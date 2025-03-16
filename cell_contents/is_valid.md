---
weight: 2
title: "isValid(row, col)"
---

Checks if the specified cell coordinates `(row, col)` lie within quadrille bounds, i.e., returns `true` if `row` `∈` [[0..height]]({{< ref "height" >}}) and `col` `∈` [[0..width]]({{< ref "width" >}}), and `false` otherwise.

{{< callout type="info" >}}  
To check bounds individually, you can call `quadrille.isValid(row, 0)` to test only if `row` is within bounds, or `quadrille.isValid(0, col)` to test only if `col` is within bounds.  
{{< /callout >}}

## Syntax

> `isValid(row, col)`

## Parameters

| Param | Description                                    |
|-------|------------------------------------------------|
| `row` | Number: row index of the cell to be checked    |
| `col` | Number: column index of the cell to be checked |
