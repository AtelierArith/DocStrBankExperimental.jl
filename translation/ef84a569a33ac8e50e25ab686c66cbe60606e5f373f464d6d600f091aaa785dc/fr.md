```
nameof(m::Module) -> Symbol
```

Obtenez le nom d'un `Module` sous forme de [`Symbol`](@ref).

# Exemples

```jldoctest
julia> nameof(Base.Broadcast)
:Broadcast
```
