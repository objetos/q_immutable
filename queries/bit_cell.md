---
weight: 7
title: "bitCell(bitIndex, littleEndian?)"
---

Returns the `(row, col)` coordinates of the cell corresponding to a given `bitIndex` in a [bitboard](https://en.wikipedia.org/wiki/Bitboard), assuming row-major ordering.  
By default, the index follows **big-endian** layout, where the most significant bit (MSB) maps to the top-left cell.  
Set `littleEndian` to `true` to reverse this mapping, placing the least significant bit (LSB) at the top-left instead.

{{< callout type="info" >}}
Example for a 2×3 quadrille:  

* **Big-endian** layout (default):
```
| 5 | 4 | 3 |
| 2 | 1 | 0 |
```

* **Little-endian** layout:
```
| 0 | 1 | 2| 3 | 4 | 5 |
```

Calling `bitCell(4)` returns `(0,1)` in big-endian, and `(1,1)` in little-endian.
{{< /callout >}}

## Syntax

> `bitCell(bitIndex[, littleEndian])`

## Parameters

| Param          | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| `bitIndex`     | Number: the index of the bit to decode into `(row, col)` coordinates        |
| `littleEndian` | Optional Boolean: if `true`, interprets the bit index using little-endian layout |

{{< callout type="info" >}}
Also available as the static method `Quadrille.bitCell(bitIndex, width = 8, height = 8, littleEndian = false)`, which allows computing cell positions independently of any specific quadrille.
{{< /callout >}}