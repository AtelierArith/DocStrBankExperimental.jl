```
parent(A)
```

Gibt das zugrunde liegende Elternobjekt der Ansicht zurück. Dieses Elternobjekt von Typen `SubArray`, `SubString`, `ReshapedArray` oder `LinearAlgebra.Transpose` ist das, was als Argument an `view`, `reshape`, `transpose` usw. während der Objekterstellung übergeben wurde. Wenn die Eingabe kein gewickeltes Objekt ist, wird die Eingabe selbst zurückgegeben. Wenn die Eingabe mehrfach gewickelt ist, wird nur der äußerste Wrapper entfernt.

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> V = view(A, 1:2, :)
2×2 view(::Matrix{Int64}, 1:2, :) mit eltype Int64:
 1  2
 3  4

julia> parent(V)
2×2 Matrix{Int64}:
 1  2
 3  4
```
