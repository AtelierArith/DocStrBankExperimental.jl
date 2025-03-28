```
Int16 <: Signed <: Integer
```

Type d'entier signé de 16 bits.

Représente des nombres `n ∈ -32768:32767`. Notez que de tels entiers débordent sans avertissement, donc `typemax(Int16) + Int16(1) < 0`.

Voir aussi [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
