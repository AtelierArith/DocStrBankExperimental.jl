```
Array{T}(missing, dims)
Array{T,N}(missing, dims)
```

Konstruiere ein `N`-dimensionales [`Array`](@ref), das Elemente des Typs `T` enthält, initialisiert mit [`missing`](@ref) Einträgen. Der Elementtyp `T` muss in der Lage sein, diese Werte zu halten, d.h. `Missing <: T`.

# Beispiele

```jldoctest
julia> Array{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing

julia> Array{Union{Missing, Int}}(missing, 2, 3)
2×3 Matrix{Union{Missing, Int64}}:
 missing  missing  missing
 missing  missing  missing
```
