```
sparsevec(I, V, [m, combine])
```

Erstellt einen spärlichen Vektor `S` der Länge `m`, so dass `S[I[k]] = V[k]`. Duplikate werden mit der `combine`-Funktion kombiniert, die standardmäßig `+` ist, wenn kein `combine`-Argument angegeben ist, es sei denn, die Elemente von `V` sind Booleans, in diesem Fall ist `combine` standardmäßig `|`.

# Beispiele

```jldoctest
julia> II = [1, 3, 3, 5]; V = [0.1, 0.2, 0.3, 0.2];

julia> sparsevec(II, V)
5-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  0.5
  [5]  =  0.2

julia> sparsevec(II, V, 8, -)
8-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  -0.1
  [5]  =  0.2

julia> sparsevec([1, 3, 1, 2, 2], [true, true, false, false, false])
3-element SparseVector{Bool, Int64} with 3 stored entries:
  [1]  =  1
  [2]  =  0
  [3]  =  1
```
