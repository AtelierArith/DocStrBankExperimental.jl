```
invpermute!(v, p)
```

Como [`permute!`](@ref), pero se aplica la inversa de la permutación dada.

Ten en cuenta que si tienes un arreglo de salida preasignado (por ejemplo, `u = similar(v)`), es más rápido emplear `u[p] = v`. (`invpermute!` asigna internamente una copia de los datos.)

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


# Ejemplos

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> invpermute!(A, perm);

julia> A
4-element Vector{Int64}:
 4
 1
 3
 1
```
