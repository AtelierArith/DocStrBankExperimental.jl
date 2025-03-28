```
Int128 <: Signed <: Integer
```

Type d'entier signé de 128 bits.

Notez que de tels entiers débordent sans avertissement, donc `typemax(Int128) + Int128(1) < 0`.

Voir aussi [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
