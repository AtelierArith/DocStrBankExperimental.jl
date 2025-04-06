```
repeat(s::AbstractString, r::Integer)
```

Wiederhole einen String `r` Mal. Dies kann als `s^r` geschrieben werden.

Siehe auch [`^`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)).

# Beispiele

```jldoctest
julia> repeat("ha", 3)
"hahaha"
```
