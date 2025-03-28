```
pairs(IndexLinear(), A)
pairs(IndexCartesian(), A)
pairs(IndexStyle(A), A)
```

Ein Iterator, der auf jedes Element des Arrays `A` zugreift und `i => x` zurückgibt, wobei `i` der Index für das Element und `x = A[i]` ist. Identisch zu `pairs(A)`, mit dem Unterschied, dass der Stil des Index ausgewählt werden kann. Ähnlich wie `enumerate(A)`, mit dem Unterschied, dass `i` ein gültiger Index für `A` sein wird, während `enumerate` immer von 1 zählt, unabhängig von den Indizes von `A`.

Die Angabe von [`IndexLinear()`](@ref) stellt sicher, dass `i` eine ganze Zahl ist; die Angabe von [`IndexCartesian()`](@ref) stellt sicher, dass `i` ein [`Base.CartesianIndex`](@ref) ist; die Angabe von `IndexStyle(A)` wählt denjenigen aus, der als der native Indexierungsstil für das Array `A` definiert wurde.

Die Mutation der Grenzen des zugrunde liegenden Arrays macht diesen Iterator ungültig.

# Beispiele

```jldoctest
julia> A = ["a" "d"; "b" "e"; "c" "f"];

julia> for (index, value) in pairs(IndexStyle(A), A)
           println("$index $value")
       end
1 a
2 b
3 c
4 d
5 e
6 f

julia> S = view(A, 1:2, :);

julia> for (index, value) in pairs(IndexStyle(S), S)
           println("$index $value")
       end
CartesianIndex(1, 1) a
CartesianIndex(2, 1) b
CartesianIndex(1, 2) d
CartesianIndex(2, 2) e
```

Siehe auch [`IndexStyle`](@ref), [`axes`](@ref).
