---
weight: 4
title: "isFilled(row, col)"
---

Returns `true` if the cell found at `(row, col)` is filled and `false` otherwise. Cells not defined as `null` are considered filled.

## Syntax

> `isFilled(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isFilled(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}