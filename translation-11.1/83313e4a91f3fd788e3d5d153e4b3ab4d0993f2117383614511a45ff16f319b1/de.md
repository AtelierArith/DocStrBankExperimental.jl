```
println([io::IO], xs...)
```

Druckt (unter Verwendung von [`print`](@ref)) `xs` auf `io`, gefolgt von einem Zeilenumbruch. Wenn `io` nicht angegeben ist, wird auf den Standardausgabestrom [`stdout`](@ref) gedruckt.

Siehe auch [`printstyled`](@ref), um Farben usw. hinzuzufügen.

# Beispiele

```jldoctest
julia> println("Hello, world")
Hello, world

julia> io = IOBuffer();

julia> println(io, "Hello", ',', " world.")

julia> String(take!(io))
"Hello, world.\n"
```
