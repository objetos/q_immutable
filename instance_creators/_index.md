---
bookCollapseSection: true
title: "Instance Creators"
weight: 3
draft: false
---

_Instance accessors_ generate new `quadrille` instances derived from the original. These methods allow you to create modified versions while preserving the original quadrille’s state:  

- **[clone()]({{< ref "clone" >}}):** Creates a [shallow copy](https://en.wikipedia.org/wiki/Object_copying#Shallow_copy) of the quadrille.  
- **[row(row)]({{< ref "row" >}}):** Creates a new quadrille containing only the specified `row`.  
- **[ring(row, col, dimension)]({{< ref "ring" >}}):** Creates a new quadrille representing a ring of cells around the specified `row` and `col` with the given `dimension`.  