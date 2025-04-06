```
CartesianIndex(i, j, k...)   -> I
CartesianIndex((i, j, k...)) -> I
```

Erstellen Sie einen mehrdimensionalen Index `I`, der zum Indizieren eines mehrdimensionalen Arrays `A` verwendet werden kann. Insbesondere ist `A[I]` äquivalent zu `A[i,j,k...]`. Man kann ganzzahlige und `CartesianIndex`-Indizes frei mischen; zum Beispiel kann `A[Ipre, i, Ipost]` (wobei `Ipre` und `Ipost` `CartesianIndex`-Indizes und `i` ein `Int` ist) ein nützliches Ausdruck sein, wenn man Algorithmen schreibt, die entlang einer einzelnen Dimension eines Arrays beliebiger Dimensionalität arbeiten.

Ein `CartesianIndex` wird manchmal von [`eachindex`](@ref) erzeugt und immer, wenn man mit expliziten [`CartesianIndices`](@ref) iteriert.

Ein `I::CartesianIndex` wird als "Skalar" (nicht als Container) für `broadcast` behandelt. Um über die Komponenten eines `CartesianIndex` zu iterieren, konvertieren Sie ihn mit `Tuple(I)` in ein Tupel.

# Beispiele

```jldoctest
julia> A = reshape(Vector(1:16), (2, 2, 2, 2))
2×2×2×2 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

[:, :, 2, 1] =
 5  7
 6  8

[:, :, 1, 2] =
  9  11
 10  12

[:, :, 2, 2] =
 13  15
 14  16

julia> A[CartesianIndex((1, 1, 1, 1))]
1

julia> A[CartesianIndex((1, 1, 1, 2))]
9

julia> A[CartesianIndex((1, 1, 2, 1))]
5
```

!!! compat "Julia 1.10"
    Die Verwendung eines `CartesianIndex` als "Skalar" für `broadcast` erfordert Julia 1.10; in früheren Versionen verwenden Sie `Ref(I)`.

