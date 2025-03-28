```
Vector{T}(missing, m)
```

Konstruiere einen [`Vector{T}`](@ref) der Länge `m`, initialisiert mit [`missing`](@ref) Einträgen. Der Elementtyp `T` muss in der Lage sein, diese Werte zu halten, d.h. `Missing <: T`.

# Beispiele

```jldoctest
julia> Vector{Union{Missing, String}}(missing, 2)
2-element Vector{Union{Missing, String}}:
 missing
 missing
```
