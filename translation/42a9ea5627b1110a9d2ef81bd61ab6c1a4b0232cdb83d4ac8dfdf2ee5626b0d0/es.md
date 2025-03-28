```
unique(itr)
```

Devuelve un array que contiene solo los elementos únicos de la colección `itr`, según lo determinado por [`isequal`](@ref) y [`hash`](@ref), en el orden en que aparece por primera vez cada conjunto de elementos equivalentes. Se preserva el tipo de elemento de la entrada.

Véase también: [`unique!`](@ref), [`allunique`](@ref), [`allequal`](@ref).

# Ejemplos

```jldoctest
julia> unique([1, 2, 6, 2])
3-element Vector{Int64}:
 1
 2
 6

julia> unique(Real[1, 1.0, 2])
2-element Vector{Real}:
 1
 2
```
