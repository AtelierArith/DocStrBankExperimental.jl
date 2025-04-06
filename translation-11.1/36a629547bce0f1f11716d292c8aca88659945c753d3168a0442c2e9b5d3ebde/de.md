```
print([io::IO], xs...)
```

Schreibt in `io` (oder in den Standardausgabestrom [`stdout`](@ref), wenn `io` nicht angegeben ist) eine kanonische (un-dekorierte) Textdarstellung. Die von `print` verwendete Darstellung umfasst minimale Formatierung und versucht, Julia-spezifische Details zu vermeiden.

`print` greift auf `show` zurück, sodass die meisten Typen einfach `show` definieren sollten. Definieren Sie `print`, wenn Ihr Typ eine separate "einfache" Darstellung hat. Zum Beispiel zeigt `show` Zeichenfolgen mit Anführungszeichen an, und `print` zeigt Zeichenfolgen ohne Anführungszeichen an.

Siehe auch [`println`](@ref), [`string`](@ref), [`printstyled`](@ref).

# Beispiele

```jldoctest
julia> print("Hello World!")
Hello World!
julia> io = IOBuffer();

julia> print(io, "Hello", ' ', :World!)

julia> String(take!(io))
"Hello World!"
```
