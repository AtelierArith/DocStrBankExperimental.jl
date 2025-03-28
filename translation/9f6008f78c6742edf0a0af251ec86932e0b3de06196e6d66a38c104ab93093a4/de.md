```
deleteat!(a::Vector, i::Integer)
```

Entfernt das Element an der angegebenen `i` und gibt das modifizierte `a` zurück. Nachfolgende Elemente werden verschoben, um die resultierende Lücke zu füllen.

Siehe auch: [`keepat!`](@ref), [`delete!`](@ref), [`popat!`](@ref), [`splice!`](@ref).

# Beispiele

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 2)
5-element Vector{Int64}:
 6
 4
 3
 2
 1
```
