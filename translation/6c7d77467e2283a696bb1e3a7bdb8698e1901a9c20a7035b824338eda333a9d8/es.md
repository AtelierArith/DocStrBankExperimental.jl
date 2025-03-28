```
BigInt(x)
```

Crea un entero de precisión arbitraria. `x` puede ser un `Int` (o cualquier cosa que se pueda convertir a un `Int`). Los operadores matemáticos habituales están definidos para este tipo, y los resultados se promueven a un [`BigInt`](@ref).

Las instancias se pueden construir a partir de cadenas a través de [`parse`](@ref), o utilizando el literal de cadena `big`.

# Ejemplos

```jldoctest
julia> parse(BigInt, "42")
42

julia> big"313"
313

julia> BigInt(10)^19
10000000000000000000
```
