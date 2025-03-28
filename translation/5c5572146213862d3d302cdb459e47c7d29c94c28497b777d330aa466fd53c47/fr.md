```
parentmodule(m::Module) -> Module
```

Obtenez le `Module` englobant d'un module. `Main` est son propre parent.

Voir aussi : [`names`](@ref), [`nameof`](@ref), [`fullname`](@ref), [`@__MODULE__`](@ref).

# Exemples

```jldoctest
julia> parentmodule(Main)
Main

julia> parentmodule(Base.Broadcast)
Base
```
