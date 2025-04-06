```
sparse(I, J, V,[ m, n, combine])
```

Erstellen Sie eine spärliche Matrix `S` der Dimensionen `m x n`, so dass `S[I[k], J[k]] = V[k]`. Die Funktion `combine` wird verwendet, um Duplikate zu kombinieren. Wenn `m` und `n` nicht angegeben sind, werden sie auf `maximum(I)` und `maximum(J)` gesetzt. Wenn die Funktion `combine` nicht bereitgestellt wird, ist `combine` standardmäßig `+`, es sei denn, die Elemente von `V` sind Booleans, in diesem Fall ist `combine` standardmäßig `|`. Alle Elemente von `I` müssen die Bedingung `1 <= I[k] <= m` erfüllen, und alle Elemente von `J` müssen die Bedingung `1 <= J[k] <= n` erfüllen. Numerische Nullen in (`I`, `J`, `V`) werden als strukturelle Nicht-Nullwerte beibehalten; um numerische Nullen zu entfernen, verwenden Sie [`dropzeros!`](@ref).

Für zusätzliche Dokumentation und einen Experten-Treiber siehe `SparseArrays.sparse!`.

# Beispiele

```jldoctest
julia> Is = [1; 2; 3];

julia> Js = [1; 2; 3];

julia> Vs = [1; 2; 3];

julia> sparse(Is, Js, Vs)
3×3 SparseMatrixCSC{Int64, Int64} mit 3 gespeicherten Einträgen:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3
```
