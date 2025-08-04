---
weight: 5
title: "isBoolean(row, col)"
---

Returns `true` if the cell at `(row, col)` contains a boolean; otherwise, returns `false`.

## Syntax

> `isBoolean(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isBoolean(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}