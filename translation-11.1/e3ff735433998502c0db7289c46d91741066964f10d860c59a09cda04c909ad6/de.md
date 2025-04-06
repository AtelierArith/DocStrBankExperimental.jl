```
hvncat(dim::Int, row_first, values...)
hvncat(dims::Tuple{Vararg{Int}}, row_first, values...)
hvncat(shape::Tuple{Vararg{Tuple}}, row_first, values...)
```

Horizontale, vertikale und n-dimensionale Verkettung vieler `values` in einem Aufruf.

Diese Funktion wird für die Blockmatrix-Syntax aufgerufen. Das erste Argument gibt entweder die Form der Verkettung an, ähnlich wie `hvcat`, als ein Tupel von Tupeln, oder die Dimensionen, die die Schlüsselanzahl der Elemente entlang jeder Achse angeben, und wird verwendet, um die Ausgabedimensionen zu bestimmen. Die `dims`-Form ist leistungsfähiger und wird standardmäßig verwendet, wenn die Verkettungsoperation die gleiche Anzahl von Elementen entlang jeder Achse hat (z. B. [a b; c d;;; e f ; g h]). Die `shape`-Form wird verwendet, wenn die Anzahl der Elemente entlang jeder Achse unausgewogen ist (z. B. [a b ; c]). Unaustarierte Syntax benötigt zusätzlichen Validierungsaufwand. Die `dim`-Form ist eine Optimierung für die Verkettung entlang nur einer Dimension. `row_first` gibt an, wie `values` angeordnet sind. Die Bedeutung der ersten und zweiten Elemente von `shape` wird ebenfalls basierend auf `row_first` vertauscht.

# Beispiele

```jldoctest
julia> a, b, c, d, e, f = 1, 2, 3, 4, 5, 6
(1, 2, 3, 4, 5, 6)

julia> [a b c;;; d e f]
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6

julia> hvncat((2,1,3), false, a,b,c,d,e,f)
2×1×3 Array{Int64, 3}:
[:, :, 1] =
 1
 2

[:, :, 2] =
 3
 4

[:, :, 3] =
 5
 6

julia> [a b;;; c d;;; e f]
1×2×3 Array{Int64, 3}:
[:, :, 1] =
 1  2

[:, :, 2] =
 3  4

[:, :, 3] =
 5  6

julia> hvncat(((3, 3), (3, 3), (6,)), true, a, b, c, d, e, f)
1×3×2 Array{Int64, 3}:
[:, :, 1] =
 1  2  3

[:, :, 2] =
 4  5  6
```

# Beispiele zur Konstruktion der Argumente

```
[a b c ; d e f ;;;
 g h i ; j k l ;;;
 m n o ; p q r ;;;
 s t u ; v w x]
⇒ dims = (2, 3, 4)

[a b ; c ;;; d ;;;;]
 ___   _     _
 2     1     1 = Elemente in jeder Zeile (2, 1, 1)
 _______     _
 3           1 = Elemente in jeder Spalte (3, 1)
 _____________
 4             = Elemente in jedem 3D-Slice (4,)
 _____________
 4             = Elemente in jedem 4D-Slice (4,)
⇒ shape = ((2, 1, 1), (3, 1), (4,), (4,)) mit `row_first` = true
```
