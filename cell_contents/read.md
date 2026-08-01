---
weight: 1
title: "read(row, col)"
---

Returns the contents of the quadrille cell at `(row, col)`. Returns `undefined` if the cell doesn't exist (out of bounds) — and note `undefined == null`, so such reads count as **empty** to [isEmpty]({{< ref "is_empty" >}}).

## Syntax

> `read(row, col)`

## Parameters

| Param | Description                                                                       |
|-------|-----------------------------------------------------------------------------------|
| `row` | Number: row index of the cell to be read `∈` [[0..height]]({{< ref "height" >}})  |
| `col` | Number: column index of the cell to be read `∈` [[0..width]]({{< ref "width" >}}) |