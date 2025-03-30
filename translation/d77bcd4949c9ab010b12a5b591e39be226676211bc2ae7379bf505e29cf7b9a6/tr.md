```
repeat(s::AbstractString, r::Integer)
```

Bir dizeyi `r` kez tekrarlar. Bu, `s^r` olarak yazılabilir.

Ayrıca bkz. [`^`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)).

# Örnekler

```jldoctest
julia> repeat("ha", 3)
"hahaha"
```
