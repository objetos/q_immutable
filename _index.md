---
bookCollapseSection: true
weight: 4
draft: false
---

# Accessors

Accessor methods are designed to provide information about the `quadrille` or to create modified copies of it without altering the original `quadrille`.

These methods are strictly non-mutative and can be categorized into two types: _query accessors_, which provide information about the state of the `quadrille`, e.g., [read(row, col)]({{< ref "read" >}}), [isNumber(row, col)]({{< ref "is_number" >}}), [isFilled(row, col)]({{< ref "is_filled" >}}); and, _instance accessors_ which generate new `quadrille` instances based on the original, e.g., [clone]({{< ref "clone" >}}), [row(row)]({{< ref "row" >}}), [ring(row, col)]({{< ref "ring" >}}).