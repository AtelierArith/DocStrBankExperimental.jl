```
Float64 <: AbstractFloat <: Real
```

64-Bit-Gleitkommazahltyp (IEEE 754-Standard). Das binäre Format besteht aus 1 Vorzeichen, 11 Exponenten und 52 Bruchbits. Siehe [`bitstring`](@ref), [`signbit`](@ref), [`exponent`](@ref), [`frexp`](@ref) und [`significand`](@ref), um auf verschiedene Bits zuzugreifen.

Dies ist der Standard für Gleitkommaliterale, `1.0 isa Float64`, und für viele Operationen wie `1/2, 2pi, log(2), range(0,90,length=4)`. Im Gegensatz zu Ganzzahlen ändert sich dieser Standard nicht mit `Sys.WORD_SIZE`.

Der Exponent für wissenschaftliche Notation kann als `e` oder `E` eingegeben werden, somit ist `2e3 === 2.0E3 === 2.0 * 10^3`. Dies wird dringend gegenüber `10^n` bevorzugt, da Ganzzahlen überlaufen, somit ist `2.0 * 10^19 < 0`, aber `2e19 > 0`.

Siehe auch [`Inf`](@ref), [`NaN`](@ref), [`floatmax`](@ref), [`Float32`](@ref), [`Complex`](@ref).
