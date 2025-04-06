```
Int16 <: Signed <: Integer
```

16-Bit vorzeichenbehafteter Ganzzahltyp.

Stellt Zahlen `n ∈ -32768:32767` dar. Beachten Sie, dass solche Ganzzahlen ohne Warnung überlaufen, daher gilt `typemax(Int16) + Int16(1) < 0`.

Siehe auch [`Int`](@ref Int64), [`widen`](@ref), [`BigInt`](@ref).
