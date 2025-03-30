```
Int64 <: Signed <: Integer
```

64-bit işaretli tam sayı türü.

Bu tür tam sayıların uyarı vermeden taşma yaptığını unutmayın, bu nedenle `typemax(Int64) + Int64(1) < 0`.

Ayrıca bkz. [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
