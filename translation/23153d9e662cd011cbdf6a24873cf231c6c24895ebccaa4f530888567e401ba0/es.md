```
map(f, c...) -> colección
```

Transforma la colección `c` aplicando `f` a cada elemento. Para múltiples argumentos de colección, aplica `f` elemento por elemento, y detente cuando cualquiera de ellos se agote.

Ver también [`map!`](@ref), [`foreach`](@ref), [`mapreduce`](@ref), [`mapslices`](@ref), [`zip`](@ref), [`Iterators.map`](@ref).

# Ejemplos

```jldoctest
julia> map(x -> x * 2, [1, 2, 3])
3-element Vector{Int64}:
 2
 4
 6

julia> map(+, [1, 2, 3], [10, 20, 30, 400, 5000])
3-element Vector{Int64}:
 11
 22
 33
```
