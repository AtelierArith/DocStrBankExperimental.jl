```
Iterators.map(f, iterators...)
```

Crea un mapeo perezoso. Esta es otra sintaxis para escribir `(f(args...) for args in zip(iterators...))`.

!!! compat "Julia 1.6"
    Esta función requiere al menos Julia 1.6.


# Ejemplos

```jldoctest
julia> collect(Iterators.map(x -> x^2, 1:3))
3-element Vector{Int64}:
 1
 4
 9
```
