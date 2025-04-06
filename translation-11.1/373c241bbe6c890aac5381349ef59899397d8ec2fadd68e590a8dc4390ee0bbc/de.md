```
Matrix{T}(nothing, m, n)
```

Konstruiere eine [`Matrix{T}`](@ref) der Größe `m`×`n`, initialisiert mit [`nothing`](@ref) Einträgen. Der Elementtyp `T` muss in der Lage sein, diese Werte zu halten, d.h. `Nothing <: T`.

# Beispiele

```jldoctest
julia> Matrix{Union{Nothing, String}}(nothing, 2, 3)
2×3 Matrix{Union{Nothing, String}}:
 nothing  nothing  nothing
 nothing  nothing  nothing
```
