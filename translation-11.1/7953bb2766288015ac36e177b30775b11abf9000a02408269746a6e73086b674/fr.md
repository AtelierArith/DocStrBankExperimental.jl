```
Int8 <: Signed <: Integer
```

Type d'entier signé de 8 bits.

Représente des nombres `n ∈ -128:127`. Notez que de tels entiers débordent sans avertissement, donc `typemax(Int8) + Int8(1) < 0`.

Voir aussi [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
