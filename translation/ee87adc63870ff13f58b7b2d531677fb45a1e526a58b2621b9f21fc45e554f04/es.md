```
replace!(A, old_new::Pair...; [count::Integer])
```

Para cada par `old=>new` en `old_new`, reemplaza todas las ocurrencias de `old` en la colección `A` por `new`. La igualdad se determina usando [`isequal`](@ref). Si se especifica `count`, entonces reemplaza como máximo `count` ocurrencias en total. Véase también [`replace`](@ref replace(A, old_new::Pair...)).

# Ejemplos

```jldoctest
julia> replace!([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace!(Set([1, 2, 3]), 1=>0)
Set{Int64} with 3 elements:
  0
  2
  3
```
