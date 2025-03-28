```
BigInt(x)
```

Créez un entier à précision arbitraire. `x` peut être un `Int` (ou tout ce qui peut être converti en `Int`). Les opérateurs mathématiques habituels sont définis pour ce type, et les résultats sont promus à un [`BigInt`](@ref).

Des instances peuvent être construites à partir de chaînes via [`parse`](@ref), ou en utilisant le littéral de chaîne `big`.

# Exemples

```jldoctest
julia> parse(BigInt, "42")
42

julia> big"313"
313

julia> BigInt(10)^19
10000000000000000000
```
