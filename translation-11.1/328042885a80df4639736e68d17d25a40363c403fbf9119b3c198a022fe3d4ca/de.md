```
Int32 <: Signed <: Integer
```

32-Bit vorzeichenbehafteter Ganzzahltyp.

Beachten Sie, dass solche Ganzzahlen ohne Warnung überlaufen, daher ist `typemax(Int32) + Int32(1) < 0`.

Siehe auch [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
