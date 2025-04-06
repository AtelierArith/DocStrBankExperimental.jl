```
parentmodule(m::Module) -> Module
```

Obtiene el `Module` que encierra a un módulo. `Main` es su propio padre.

Véase también: [`names`](@ref), [`nameof`](@ref), [`fullname`](@ref), [`@__MODULE__`](@ref).

# Ejemplos

```jldoctest
julia> parentmodule(Main)
Main

julia> parentmodule(Base.Broadcast)
Base
```
