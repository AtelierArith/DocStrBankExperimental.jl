```
filter(f, a)
```

Devuelve una copia de la colección `a`, eliminando los elementos para los cuales `f` es `false`. La función `f` recibe un argumento.

!!! compat "Julia 1.4"
    El soporte para `a` como una tupla requiere al menos Julia 1.4.


Véase también: [`filter!`](@ref), [`Iterators.filter`](@ref).

# Ejemplos

```jldoctest
julia> a = 1:10
1:10

julia> filter(isodd, a)
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
