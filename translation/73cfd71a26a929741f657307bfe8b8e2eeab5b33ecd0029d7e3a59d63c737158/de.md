```
repeat(c::AbstractChar, r::Integer) -> String
```

Wiederhole ein Zeichen `r` Mal. Dies kann auch erreicht werden, indem man [`c^r`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)) aufruft.

# Beispiele

```jldoctest
julia> repeat('A', 3)
"AAA"
```
