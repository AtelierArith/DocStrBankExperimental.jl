```
peek(stream[, T=UInt8])
```

Lee y devuelve un valor del tipo `T` de un flujo sin avanzar la posición actual en el flujo. Ver también [`startswith(stream, char_or_string)`](@ref).

# Ejemplos

```jldoctest
julia> b = IOBuffer("julia");

julia> peek(b)
0x6a

julia> position(b)
0

julia> peek(b, Char)
'j': ASCII/Unicode U+006A (categoría Ll: Letra, minúscula)
```

!!! compat "Julia 1.5"
    El método que acepta un tipo requiere Julia 1.5 o posterior.

