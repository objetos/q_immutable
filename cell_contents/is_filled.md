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