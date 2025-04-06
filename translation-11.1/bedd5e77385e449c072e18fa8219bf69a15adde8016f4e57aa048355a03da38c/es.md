```
product(iters...)
```

Devuelve un iterador sobre el producto de varios iteradores. Cada elemento generado es una tupla cuyo `i`-ésimo elemento proviene del `i`-ésimo iterador de argumento. El primer iterador cambia más rápido.

Véase también: [`zip`](@ref), [`Iterators.flatten`](@ref).

# Ejemplos

```jldoctest
julia> collect(Iterators.product(1:2, 3:5))
2×3 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (1, 4)  (1, 5)
 (2, 3)  (2, 4)  (2, 5)

julia> ans == [(x,y) for x in 1:2, y in 3:5]  # recoge un generador que involucra Iterators.product
true
```
