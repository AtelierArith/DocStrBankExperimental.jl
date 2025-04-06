```
sparse(I, J, V,[ m, n, combine])
```

Crea una matriz dispersa `S` de dimensiones `m x n` tal que `S[I[k], J[k]] = V[k]`. La función `combine` se utiliza para combinar duplicados. Si `m` y `n` no se especifican, se establecen en `maximum(I)` y `maximum(J)` respectivamente. Si la función `combine` no se proporciona, `combine` por defecto es `+` a menos que los elementos de `V` sean Booleanos, en cuyo caso `combine` por defecto es `|`. Todos los elementos de `I` deben satisfacer `1 <= I[k] <= m`, y todos los elementos de `J` deben satisfacer `1 <= J[k] <= n`. Los ceros numéricos en (`I`, `J`, `V`) se retienen como no ceros estructurales; para eliminar ceros numéricos, utiliza [`dropzeros!`](@ref).

Para documentación adicional y un controlador experto, consulta `SparseArrays.sparse!`.

# Ejemplos

```jldoctest
julia> Is = [1; 2; 3];

julia> Js = [1; 2; 3];

julia> Vs = [1; 2; 3];

julia> sparse(Is, Js, Vs)
3×3 SparseMatrixCSC{Int64, Int64} con 3 entradas almacenadas:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3
```
