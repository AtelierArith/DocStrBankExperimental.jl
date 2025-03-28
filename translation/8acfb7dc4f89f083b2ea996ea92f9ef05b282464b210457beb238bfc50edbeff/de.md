```
result_style(s1::BroadcastStyle[, s2::BroadcastStyle]) -> BroadcastStyle
```

Nimmt einen oder zwei `BroadcastStyle`s und kombiniert sie mithilfe von [`BroadcastStyle`](@ref), um einen gemeinsamen `BroadcastStyle` zu bestimmen.

# Beispiele

```jldoctest
julia> Broadcast.result_style(Broadcast.DefaultArrayStyle{0}(), Broadcast.DefaultArrayStyle{3}())
Base.Broadcast.DefaultArrayStyle{3}()

julia> Broadcast.result_style(Broadcast.Unknown(), Broadcast.DefaultArrayStyle{1}())
Base.Broadcast.DefaultArrayStyle{1}()
```
