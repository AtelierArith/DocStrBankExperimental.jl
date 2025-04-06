```
reshape(A, dims...) -> AbstractArray
reshape(A, dims) -> AbstractArray
```

Gibt ein Array mit denselben Daten wie `A` zurück, jedoch mit unterschiedlichen Dimensionen oder Anzahl der Dimensionen. Die beiden Arrays teilen sich die gleichen zugrunde liegenden Daten, sodass das Ergebnis veränderbar ist, wenn und nur wenn `A` veränderbar ist, und das Setzen von Elementen eines Arrays die Werte des anderen ändert.

Die neuen Dimensionen können entweder als Liste von Argumenten oder als Form-Tuple angegeben werden. Höchstens eine Dimension darf mit einem `:` angegeben werden, in diesem Fall wird ihre Länge so berechnet, dass ihr Produkt mit allen angegebenen Dimensionen gleich der Länge des ursprünglichen Arrays `A` ist. Die Gesamtanzahl der Elemente darf sich nicht ändern.

# Beispiele

```jldoctest
julia> A = Vector(1:16)
16-element Vector{Int64}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16

julia> reshape(A, (4, 4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reshape(A, 2, :)
2×8 Matrix{Int64}:
 1  3  5  7   9  11  13  15
 2  4  6  8  10  12  14  16

julia> reshape(1:6, 2, 3)
2×3 reshape(::UnitRange{Int64}, 2, 3) with eltype Int64:
 1  3  5
 2  4  6
```
