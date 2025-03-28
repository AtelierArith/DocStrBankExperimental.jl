```
replace(A, old_new::Pair...; [count::Integer])
```

Devuelve una copia de la colección `A` donde, para cada par `old=>new` en `old_new`, todas las ocurrencias de `old` son reemplazadas por `new`. La igualdad se determina usando [`isequal`](@ref). Si se especifica `count`, entonces se reemplazarán como máximo `count` ocurrencias en total.

El tipo de elemento del resultado se elige usando promoción (ver [`promote_type`](@ref)) basado en el tipo de elemento de `A` y en los tipos de los valores `new` en los pares. Si se omite `count` y el tipo de elemento de `A` es un `Union`, el tipo de elemento del resultado no incluirá tipos singleton que son reemplazados por valores de un tipo diferente: por ejemplo, `Union{T,Missing}` se convertirá en `T` si `missing` es reemplazado.

Ver también [`replace!`](@ref), [`splice!`](@ref), [`delete!`](@ref), [`insert!`](@ref).

!!! compat "Julia 1.7"
    Se requiere la versión 1.7 para reemplazar elementos de un `Tuple`.


# Ejemplos

```jldoctest
julia> replace([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace([1, missing], missing=>0)
2-element Vector{Int64}:
 1
 0
```
