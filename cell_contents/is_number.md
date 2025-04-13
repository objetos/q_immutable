---
weight: 6
title: "isNumber(row, col)"
---

Returns `true` if the cell found at `(row, col)` has a number and `false` otherwise.

## Syntax

> `isNumber(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isNumber(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}