```
Int8 <: Signed <: Integer
```

8 bit işaretli tam sayı türü.

`n ∈ -128:127` aralığındaki sayıları temsil eder. Bu tür tam sayılar uyarı vermeden taşar, bu nedenle `typemax(Int8) + Int8(1) < 0` ifadesi doğrudur.

Ayrıca bkz. [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
