```
Int32 <: Signed <: Integer
```

32-bit işaretli tam sayı türü.

Bu tür tam sayıların uyarı vermeden taşma yaptığını unutmayın, bu nedenle `typemax(Int32) + Int32(1) < 0`.

Ayrıca bkz. [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
