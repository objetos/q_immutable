---
bookCollapseSection: true  
weight: 4  
draft: false  
title: Accessors  
---

**Accessor methods** are powerful tools for extracting information or creating modified versions of a `quadrille` instance. These methods are strictly **non-mutative**, ensuring the original quadrille remains unchanged while offering detailed insights or generating derivative instances.

### **Queries**  
[Query methods]({{< relref "queries" >}}) provide computations and insights into the quadrille's structure. These include operations such as **[search(pattern, strict)]({{< relref "search" >}})** for finding cells matching specific patterns, **[magnitude(row)]({{< relref "magnitude" >}})** to calculate the number of non-empty cells in a row, and **[screenRow(pixelY, y, cellLength)]({{< relref "screen_row" >}})** or **[screenCol(pixelX, x, cellLength)]({{< relref "screen_col" >}})** for mapping pixel positions to grid indices.  

### **Cell Contents**  
[Cell content accessors]({{< relref "cell_contents" >}}) focus on retrieving information about the value and type of individual cells. You can use **[read(row, col)]({{< relref "read" >}})** to access a cell's content, or methods like **[isValid(row, col)]({{< relref "is_valid" >}})**, **[isEmpty(row, col)]({{< relref "is_empty" >}})**, **[isFilled(row, col)]({{< relref "is_filled" >}})**, **[isString(row, col)]({{< relref "is_string" >}})**, **[isNumber(row, col)]({{< relref "is_number" >}})**, **[isColor(row, col)]({{< relref "is_color" >}})**, **[isImage(row, col)]({{< relref "is_image" >}})**, **[isArray(row, col)]({{< relref "is_array" >}})**, **[isFunction(row, col)]({{< relref "is_function" >}})**, and **[isObject(row, col)]({{< relref "is_object" >}})** to determine the type of data in a specific cell.  

### **Instance Creators**  
[Instance creator methods]({{< relref "instance_creators" >}}) generate new quadrille instances derived from the original. These include **[clone()]({{< relref "clone" >}})** to create a shallow copy, **[row(row)]({{< relref "row" >}})** to extract a specific row, and **[ring(row, col, dimension)]({{< relref "ring" >}})** to construct a circular subset of cells around a specified position.

Through these categories, accessor methods provide a comprehensive way to analyze and derive data from quadrille instances without altering their original state.