```
Int8 <: Signed <: Integer
```

8-Bit vorzeichenbehafteter Ganzzahltyp.

Stellt Zahlen `n ∈ -128:127` dar. Beachten Sie, dass solche Ganzzahlen ohne Warnung überlaufen, daher gilt `typemax(Int8) + Int8(1) < 0`.

Siehe auch [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
