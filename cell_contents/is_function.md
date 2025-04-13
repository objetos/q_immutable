---
weight: 10
title: "isFunction(row, col)"
---

Returns `true` if the cell found at `(row, col)` is a function and `false` otherwise.

## Syntax

> `isFunction(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isFunction(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}