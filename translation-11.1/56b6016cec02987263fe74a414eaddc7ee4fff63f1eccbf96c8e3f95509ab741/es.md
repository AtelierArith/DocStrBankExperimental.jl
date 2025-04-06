```
pop!(colección) -> elemento
```

Elimina un elemento en `colección` y lo devuelve. Si `colección` es un contenedor ordenado, se devuelve el último elemento; para contenedores desordenados, se devuelve un elemento arbitrario.

Véase también: [`popfirst!`](@ref), [`popat!`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref), y [`push!`](@ref).

# Ejemplos

```jldoctest
julia> A=[1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> pop!(A)
3

julia> A
2-element Vector{Int64}:
 1
 2

julia> S = Set([1, 2])
Set{Int64} con 2 elementos:
  2
  1

julia> pop!(S)
2

julia> S
Set{Int64} con 1 elemento:
  1

julia> pop!(Dict(1=>2))
1 => 2
```
