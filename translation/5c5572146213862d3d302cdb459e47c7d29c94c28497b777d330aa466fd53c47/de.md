```
parentmodule(m::Module) -> Modul
```

Holen Sie sich das umschließende `Modul` eines Moduls. `Main` ist sein eigener Elternteil.

Siehe auch: [`names`](@ref), [`nameof`](@ref), [`fullname`](@ref), [`@__MODULE__`](@ref).

# Beispiele

```jldoctest
julia> parentmodule(Main)
Main

julia> parentmodule(Base.Broadcast)
Base
```
