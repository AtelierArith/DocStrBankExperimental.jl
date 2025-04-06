```
Int32 <: Signed <: Integer
```

Type d'entier signé 32 bits.

Notez que de tels entiers débordent sans avertissement, donc `typemax(Int32) + Int32(1) < 0`.

Voir aussi [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
