```
Int64 <: Signed <: Integer
```

Type d'entier signé 64 bits.

Notez que de tels entiers débordent sans avertissement, donc `typemax(Int64) + Int64(1) < 0`.

Voir aussi [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
