```
nameof(m::Module) -> Symbol
```

Obtiene el nombre de un `Module` como un [`Symbol`](@ref).

# Ejemplos

```jldoctest
julia> nameof(Base.Broadcast)
:Broadcast
```
