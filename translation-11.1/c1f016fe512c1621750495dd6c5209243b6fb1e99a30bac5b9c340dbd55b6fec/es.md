```
union!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

Construye la [`union`](@ref) de los conjuntos pasados y sobrescribe `s` con el resultado. Mantiene el orden con los arreglos.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


# Ejemplos

```jldoctest
julia> a = Set([3, 4, 5]);

julia> union!(a, 1:2:7);

julia> a
Set{Int64} con 5 elementos:
  5
  4
  7
  3
  1
```
