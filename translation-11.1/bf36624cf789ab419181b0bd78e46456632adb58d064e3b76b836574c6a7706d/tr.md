```
Int128 <: Signed <: Integer
```

128 bit işaretli tam sayı türü.

Bu tür tam sayıların uyarı vermeden taşma yaptığını unutmayın, bu nedenle `typemax(Int128) + Int128(1) < 0`.

Ayrıca bkz. [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
