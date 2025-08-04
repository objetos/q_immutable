---
weight: 7
title: "isBigInt(row, col)"
---

Returns `true` if the cell at `(row, col)` contains a bigint; otherwise, returns `false`.

## Syntax

> `isBigInt(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isBigInt(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}