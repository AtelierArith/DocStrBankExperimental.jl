```
Matrix{T}(missing, m, n)
```

Konstruiere eine [`Matrix{T}`](@ref) der Größe `m`×`n`, initialisiert mit [`missing`](@ref) Einträgen. Der Elementtyp `T` muss in der Lage sein, diese Werte zu halten, d.h. `Missing <: T`.

# Beispiele

```jldoctest
julia> Matrix{Union{Missing, String}}(missing, 2, 3)
2×3 Matrix{Union{Missing, String}}:
 missing  missing  missing
 missing  missing  missing
```
