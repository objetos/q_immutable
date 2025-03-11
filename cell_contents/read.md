---
weight: 1
title: "read(row, col)"
---

Returns the contents of the quadrille cell at `(row, col)`. Returns `undefined` if the cell doesn't exist.

## Syntax

> `read(row, col)`

## Parameters

| Param    | Description                                                                     |
|----------|---------------------------------------------------------------------------------|
| `row`    | Number: col number of the cell to be read [[0..height]]({{< ref "height" >}}) |
| `col`    | Number: row number of the cell to be read [[0..width]]({{< ref "width" >}})   |