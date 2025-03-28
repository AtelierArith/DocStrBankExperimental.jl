```
empty(v::AbstractVector, [eltype])
```

Crea un vector vacío similar a `v`, cambiando opcionalmente el `eltype`.

Véase también: [`empty!`](@ref), [`isempty`](@ref), [`isassigned`](@ref).

# Ejemplos

```jldoctest
julia> empty([1.0, 2.0, 3.0])
Float64[]

julia> empty([1.0, 2.0, 3.0], String)
String[]
```
