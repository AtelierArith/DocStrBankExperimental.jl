```
println([io::IO], xs...)
```

Imprime (en utilisant [`print`](@ref)) `xs` sur `io` suivi d'une nouvelle ligne. Si `io` n'est pas fourni, imprime sur le flux de sortie par défaut [`stdout`](@ref).

Voir aussi [`printstyled`](@ref) pour ajouter des couleurs, etc.

# Exemples

```jldoctest
julia> println("Hello, world")
Hello, world

julia> io = IOBuffer();

julia> println(io, "Hello", ',', " world.")

julia> String(take!(io))
"Hello, world.\n"
```
