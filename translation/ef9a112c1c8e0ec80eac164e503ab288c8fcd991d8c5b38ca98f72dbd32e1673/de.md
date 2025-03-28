```
\(x, y)
```

Linker-Operator: Multiplikation von `y` mit der Inversen von `x` von links. Gibt Fließkommaergebnisse für ganzzahlige Argumente zurück.

# Beispiele

```jldoctest
julia> 3 \ 6
2.0

julia> inv(3) * 6
2.0

julia> A = [4 3; 2 1]; x = [5, 6];

julia> A \ x
2-element Vector{Float64}:
  6.5
 -7.0

julia> inv(A) * x
2-element Vector{Float64}:
  6.5
 -7.0
```
