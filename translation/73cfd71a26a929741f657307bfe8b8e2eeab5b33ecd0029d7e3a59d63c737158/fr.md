```
repeat(c::AbstractChar, r::Integer) -> String
```

Répète un caractère `r` fois. Cela peut également être accompli en appelant [`c^r`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)).

# Exemples

```jldoctest
julia> repeat('A', 3)
"AAA"
```
