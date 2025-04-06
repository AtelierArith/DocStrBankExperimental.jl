```
Float32 <: AbstractFloat <: Real
```

32-Bit-Gleitkommazahltyp (IEEE 754-Standard). Das binäre Format besteht aus 1 Vorzeichen, 8 Exponenten und 23 Bruchbits.

Der Exponent für die wissenschaftliche Notation sollte in Kleinbuchstaben `f` eingegeben werden, also `2f3 === 2.0f0 * 10^3 === Float32(2_000)`. Bei Array-Literalen und -Komprehensionen kann der Elementtyp vor den eckigen Klammern angegeben werden: `Float32[1,4,9] == Float32[i^2 for i in 1:3]`.

Siehe auch [`Inf32`](@ref), [`NaN32`](@ref), [`Float16`](@ref), [`exponent`](@ref), [`frexp`](@ref).
