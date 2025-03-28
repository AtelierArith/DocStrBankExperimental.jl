```
empty(v::AbstractVector, [eltype])
```

Erstellt einen leeren Vektor, der `v` ähnlich ist, wobei optional der `eltype` geändert werden kann.

Siehe auch: [`empty!`](@ref), [`isempty`](@ref), [`isassigned`](@ref).

# Beispiele

```jldoctest
julia> empty([1.0, 2.0, 3.0])
Float64[]

julia> empty([1.0, 2.0, 3.0], String)
String[]
```
