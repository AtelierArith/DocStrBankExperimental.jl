```
repeat(c::AbstractChar, r::Integer) -> String
```

Repite un carácter `r` veces. Esto se puede lograr de manera equivalente llamando a [`c^r`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)).

# Ejemplos

```jldoctest
julia> repeat('A', 3)
"AAA"
```
