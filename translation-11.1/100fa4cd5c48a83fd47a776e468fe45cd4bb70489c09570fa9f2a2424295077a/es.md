```
Int64 <: Signed <: Integer
```

Tipo de entero con signo de 64 bits.

Tenga en cuenta que tales enteros se desbordan sin advertencia, por lo tanto `typemax(Int64) + Int64(1) < 0`.

Véase también [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
