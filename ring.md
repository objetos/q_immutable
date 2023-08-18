---
weight: 10
draft: false
---

# `ring()`

Returns the ring of neighbor cells centered at `(row, col)` as a new quadrille.

# Example

# Syntax

> `ring(row, col, [dimension = 1])`

# Parameters

| param     | description                                                                     |
|-----------|---------------------------------------------------------------------------------|
| row       | Number: col number of the cell to be read [\[0..height\]]({{< ref "height" >}}) |
| col       | Number: row number of the cell to be read [\[0..width\]]({{< ref "width" >}})   |
| dimension | Number: ring dimension default is 1                                             |