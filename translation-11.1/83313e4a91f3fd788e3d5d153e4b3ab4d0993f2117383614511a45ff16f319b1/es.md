```
println([io::IO], xs...)
```

Imprime (usando [`print`](@ref)) `xs` en `io` seguido de una nueva línea. Si `io` no se proporciona, imprime en el flujo de salida predeterminado [`stdout`](@ref).

Véase también [`printstyled`](@ref) para agregar colores, etc.

# Ejemplos

```jldoctest
julia> println("Hello, world")
Hello, world

julia> io = IOBuffer();

julia> println(io, "Hello", ',', " world.")

julia> String(take!(io))
"Hello, world.\n"
```
