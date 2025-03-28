```
Int16 <: Signed <: Integer
```

Tipo de entero con signo de 16 bits.

Representa números `n ∈ -32768:32767`. Tenga en cuenta que tales enteros se desbordan sin advertencia, por lo tanto `typemax(Int16) + Int16(1) < 0`.

Véase también [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
