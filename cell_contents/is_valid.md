---
weight: 2
title: "isValid(row, col)"
---

Checks if the specified cell coordinates `(row, col)` lie within quadrille bounds, i.e., returns `true` if `row` `∈` [[0..height]]({{< ref "height" >}}) and `col` `∈` [[0..width]]({{< ref "width" >}}), and `false` otherwise.

## Syntax

> `isValid(row, col)`

## Parameters

| Param    | Description                               |
|----------|-------------------------------------------|
| `row`    | Number: col number of the cell to be read |
| `col`    | Number: row number of the cell to be read |