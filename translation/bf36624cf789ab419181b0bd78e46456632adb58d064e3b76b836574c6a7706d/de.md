```
Int128 <: Signed <: Integer
```

128-Bit vorzeichenbehafteter Ganzzahltyp.

Beachten Sie, dass solche Ganzzahlen ohne Warnung überlaufen, daher gilt `typemax(Int128) + Int128(1) < 0`.

Siehe auch [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
