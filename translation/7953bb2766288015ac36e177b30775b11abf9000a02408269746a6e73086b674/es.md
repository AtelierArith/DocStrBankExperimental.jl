```
Int8 <: Signed <: Integer
```

Tipo de entero con signo de 8 bits.

Representa números `n ∈ -128:127`. Tenga en cuenta que tales enteros desbordarán sin advertencia, por lo tanto `typemax(Int8) + Int8(1) < 0`.

Véase también [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
