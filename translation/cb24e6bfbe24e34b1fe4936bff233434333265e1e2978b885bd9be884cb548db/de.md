```
Array{T}(nichts, dims)
Array{T,N}(nichts, dims)
```

Konstruiere ein `N`-dimensionales [`Array`](@ref), das Elemente des Typs `T` enthält, initialisiert mit [`nichts`](@ref) Einträgen. Der Elementtyp `T` muss in der Lage sein, diese Werte zu halten, d.h. `Nothing <: T`.

# Beispiele

```jldoctest
julia> Array{Union{Nothing, String}}(nichts, 2)
2-element Vector{Union{Nothing, String}}:
 nichts
 nichts

julia> Array{Union{Nothing, Int}}(nichts, 2, 3)
2×3 Matrix{Union{Nothing, Int64}}:
 nichts  nichts  nichts
 nichts  nichts  nichts
```
