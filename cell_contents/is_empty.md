---
weight: 3
title: "isEmpty(row, col)"
---

Returns `true` if the cell found at `(row, col)` is empty and `false` otherwise. Only cells defined as `null` are considered empty.

## Syntax

> `isEmpty(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isEmpty(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}