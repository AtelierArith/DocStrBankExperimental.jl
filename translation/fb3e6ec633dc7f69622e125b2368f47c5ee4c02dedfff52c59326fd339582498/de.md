```
Vector{T}(nichts, m)
```

Konstruiere einen [`Vector{T}`](@ref) der Länge `m`, initialisiert mit [`nichts`](@ref) Einträgen. Der Elementtyp `T` muss in der Lage sein, diese Werte zu halten, d.h. `Nichts <: T`.

# Beispiele

```jldoctest
julia> Vector{Union{Nichts, String}}(nichts, 2)
2-element Vector{Union{Nichts, String}}:
 nichts
 nichts
```
