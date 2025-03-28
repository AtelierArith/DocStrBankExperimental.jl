```
Int64 <: Signed <: Integer
```

64-Bit vorzeichenbehafteter Ganzzahltyp.

Beachten Sie, dass solche Ganzzahlen ohne Warnung überlaufen, daher ist `typemax(Int64) + Int64(1) < 0`.

Siehe auch [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
