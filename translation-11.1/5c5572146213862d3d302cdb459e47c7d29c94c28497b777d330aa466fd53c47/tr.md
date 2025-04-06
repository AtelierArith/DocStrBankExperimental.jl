```
parentmodule(m::Module) -> Module
```

Bir modülün kapsayıcı `Module`'sini alır. `Main` kendi ebeveynidir.

Ayrıca bakınız: [`names`](@ref), [`nameof`](@ref), [`fullname`](@ref), [`@__MODULE__`](@ref).

# Örnekler

```jldoctest
julia> parentmodule(Main)
Main

julia> parentmodule(Base.Broadcast)
Base
```
