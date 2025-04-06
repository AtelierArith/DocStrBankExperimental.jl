```
codeunit(s::AbstractString, i::Integer) -> Union{UInt8, UInt16, UInt32}
```

Devuelve el valor de la unidad de código en la cadena `s` en el índice `i`. Nota que

```
codeunit(s, i) :: codeunit(s)
```

Es decir, el valor devuelto por `codeunit(s, i)` es del tipo devuelto por `codeunit(s)`.

# Ejemplos

```jldoctest
julia> a = codeunit("Hello", 2)
0x65

julia> typeof(a)
UInt8
```

Ver también [`ncodeunits`](@ref), [`checkbounds`](@ref).
