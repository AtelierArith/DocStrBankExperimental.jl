```
nameof(m::Module) -> Symbol
```

Bir `Module`'ün adını [`Symbol`](@ref) olarak alır.

# Örnekler

```jldoctest
julia> nameof(Base.Broadcast)
:Broadcast
```
