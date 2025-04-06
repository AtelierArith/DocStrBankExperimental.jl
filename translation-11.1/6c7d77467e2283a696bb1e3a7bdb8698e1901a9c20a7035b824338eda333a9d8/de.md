```
BigInt(x)
```

Erstellt eine Ganzzahl mit beliebiger Präzision. `x` kann ein `Int` (oder alles, was in ein `Int` umgewandelt werden kann) sein. Die üblichen mathematischen Operatoren sind für diesen Typ definiert, und die Ergebnisse werden zu einem [`BigInt`](@ref) befördert.

Instanzen können aus Zeichenfolgen über [`parse`](@ref) oder mit dem `big`-Zeichenfolgenliteral erstellt werden.

# Beispiele

```jldoctest
julia> parse(BigInt, "42")
42

julia> big"313"
313

julia> BigInt(10)^19
10000000000000000000
```
