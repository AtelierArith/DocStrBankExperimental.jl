```
>>>(x, n)
```

Unsignierter rechter Bitverschiebungsoperator, `x >>> n`. Für `n >= 0` ist das Ergebnis `x`, das um `n` Bits nach rechts verschoben wird, wobei mit `0`s aufgefüllt wird. Für `n < 0` entspricht dies `x << -n`.

Für [`Unsigned`](@ref) Ganzzahltypen entspricht dies [`>>`](@ref). Für [`Signed`](@ref) Ganzzahltypen entspricht dies `signed(unsigned(x) >> n)`.

# Beispiele

```jldoctest
julia> Int8(-14) >>> 2
60

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(60))
"00111100"
```

[`BigInt`](@ref)s werden behandelt, als hätten sie eine unendliche Größe, sodass kein Auffüllen erforderlich ist und dies entspricht [`>>`](@ref).

Siehe auch [`>>`](@ref), [`<<`](@ref).
