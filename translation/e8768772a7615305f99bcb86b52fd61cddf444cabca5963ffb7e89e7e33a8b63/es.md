```
permute!(v, p)
```

Permuta el vector `v` en su lugar, de acuerdo con la permutación `p`. No se realiza ninguna verificación para confirmar que `p` es una permutación.

Para devolver una nueva permutación, usa `v[p]`. Esto es generalmente más rápido que `permute!(v, p)`; es aún más rápido escribir en un array de salida preasignado con `u .= @view v[p]`. (A pesar de que `permute!` sobrescribe `v` en su lugar, internamente requiere alguna asignación para hacer un seguimiento de qué elementos han sido movidos.)

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


Ver también [`invpermute!`](@ref).

# Ejemplos

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> permute!(A, perm);

julia> A
4-element Vector{Int64}:
 1
 4
 3
 1
```
