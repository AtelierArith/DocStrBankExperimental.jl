```
promote_typejoin(T, S)
```

Calcula un tipo que contiene tanto `T` como `S`, que podría ser un padre de ambos tipos, o un `Union` si es apropiado. Recurre a [`typejoin`](@ref).

Ver también [`promote`](@ref), [`promote_type`](@ref).

# Ejemplos

```jldoctest
julia> Base.promote_typejoin(Int, Float64)
Real

julia> Base.promote_type(Int, Float64)
Float64
```
