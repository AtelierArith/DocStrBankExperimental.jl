```
keepat!(a::Vector, inds)
keepat!(a::BitVector, inds)
```

Elimina los elementos en todos los índices que no están dados por `inds`, y devuelve el `a` modificado. Los elementos que se mantienen se desplazan para llenar los huecos resultantes.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


`inds` debe ser un iterador de índices enteros únicos y ordenados. Ver también [`deleteat!`](@ref).

!!! compat "Julia 1.7"
    Esta función está disponible desde Julia 1.7.


# Ejemplos

```jldoctest
julia> keepat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 6
 4
 2
```
