```
spdiagm(v::AbstractVector)
spdiagm(m::Integer, n::Integer, v::AbstractVector)
```

Konstruiere eine spärliche Matrix mit den Elementen des Vektors als Diagonalelemente. Standardmäßig (ohne angegebenes `m` und `n`) ist die Matrix quadratisch und ihre Größe wird durch `length(v)` bestimmt, aber eine nicht-quadratische Größe `m`×`n` kann angegeben werden, indem `m` und `n` als die ersten Argumente übergeben werden.

!!! compat "Julia 1.6"
    Diese Funktionen erfordern mindestens Julia 1.6.


# Beispiele

```jldoctest
julia> spdiagm([1,2,3])
3×3 SparseMatrixCSC{Int64, Int64} mit 3 gespeicherten Einträgen:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3

julia> spdiagm(sparse([1,0,3]))
3×3 SparseMatrixCSC{Int64, Int64} mit 2 gespeicherten Einträgen:
 1  ⋅  ⋅
 ⋅  ⋅  ⋅
 ⋅  ⋅  3
```
