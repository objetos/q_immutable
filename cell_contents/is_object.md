---
weight: 11
title: "isObject(row, col)"
---

Returns `true` if the cell at `(row, col)` contains a value that qualifies as an object, excluding specific types such as [colors]({{< relref "is_color" >}}), [images]({{< relref "is_image" >}}), [arrays]({{< relref "is_array" >}}), or [functions]({{< relref "is_function" >}}), and `false` otherwise.

## Syntax

> `isObject(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |

{{< callout type="info" >}}
Also available as the static method `Quadrille.isObject(value)`, which takes a `value` instead of a cell position.
{{< /callout >}}