```
sparse(I, J, V,[ m, n, combine])
```

Créez une matrice creuse `S` de dimensions `m x n` telle que `S[I[k], J[k]] = V[k]`. La fonction `combine` est utilisée pour combiner les doublons. Si `m` et `n` ne sont pas spécifiés, ils sont définis sur `maximum(I)` et `maximum(J)` respectivement. Si la fonction `combine` n'est pas fournie, `combine` par défaut est `+` à moins que les éléments de `V` ne soient des booléens, auquel cas `combine` par défaut est `|`. Tous les éléments de `I` doivent satisfaire `1 <= I[k] <= m`, et tous les éléments de `J` doivent satisfaire `1 <= J[k] <= n`. Les zéros numériques dans (`I`, `J`, `V`) sont conservés comme des non-zéros structurels ; pour supprimer les zéros numériques, utilisez [`dropzeros!`](@ref).

Pour une documentation supplémentaire et un pilote expert, voir `SparseArrays.sparse!`.

# Exemples

```jldoctest
julia> Is = [1; 2; 3];

julia> Js = [1; 2; 3];

julia> Vs = [1; 2; 3];

julia> sparse(Is, Js, Vs)
3×3 SparseMatrixCSC{Int64, Int64} avec 3 entrées stockées :
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3
```
