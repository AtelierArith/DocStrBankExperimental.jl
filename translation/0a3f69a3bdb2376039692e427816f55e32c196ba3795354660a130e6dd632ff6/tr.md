```
Int16 <: Signed <: Integer
```

16-bit işaretli tam sayı türü.

`n ∈ -32768:32767` sayılarını temsil eder. Bu tür tam sayılar uyarı olmadan taşar, bu nedenle `typemax(Int16) + Int16(1) < 0` ifadesi geçerlidir.

Ayrıca bkz. [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
