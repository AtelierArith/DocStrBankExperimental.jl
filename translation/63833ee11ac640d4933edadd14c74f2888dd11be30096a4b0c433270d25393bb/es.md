```
^(s::Union{AbstractString,AbstractChar}, n::Integer) -> AbstractString
```

Repite una cadena o carácter `n` veces. Esto también se puede escribir como `repeat(s, n)`.

Véase también [`repeat`](@ref).

# Ejemplos

```jldoctest
julia> "Test "^3
"Test Test Test "
```
