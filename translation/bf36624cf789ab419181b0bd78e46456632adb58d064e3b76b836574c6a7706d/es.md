```
Int128 <: Signed <: Integer
```

Tipo de entero con signo de 128 bits.

Tenga en cuenta que tales enteros se desbordan sin advertencia, por lo tanto `typemax(Int128) + Int128(1) < 0`.

Véase también [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
