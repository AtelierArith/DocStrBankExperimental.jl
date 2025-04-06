```
popfirst!(colección) -> elemento
```

Elimina el primer `elemento` de `colección`.

Esta función se llama `shift` en muchos otros lenguajes de programación.

Ver también: [`pop!`](@ref), [`popat!`](@ref), [`delete!`](@ref).

# Ejemplos

```jldoctest
julia> A = [1, 2, 3, 4, 5, 6]
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> popfirst!(A)
1

julia> A
5-element Vector{Int64}:
 2
 3
 4
 5
 6
```
