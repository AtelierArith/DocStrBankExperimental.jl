```
repeat(s::AbstractString, r::Integer)
```

Repite una cadena `r` veces. Esto se puede escribir como `s^r`.

Véase también [`^`](@ref :^(::Union{AbstractString, AbstractChar}, ::Integer)).

# Ejemplos

```jldoctest
julia> repeat("ha", 3)
"hahaha"
```
