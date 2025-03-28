```
Int
```

Sys.WORD_SIZE-Bit vorzeichenbehafteter Ganzzahltyp, `Int <: Signed <: Integer <: Real`.

Dies ist der Standardtyp der meisten Ganzzahl-Literale und ist ein Alias für entweder `Int32` oder `Int64`, abhängig von `Sys.WORD_SIZE`. Es ist der Typ, der von Funktionen wie [`length`](@ref) zurückgegeben wird, und der Standardtyp für das Indizieren von Arrays.

Beachten Sie, dass Ganzzahlen ohne Warnung überlaufen, daher gilt `typemax(Int) + 1 < 0` und `10^19 < 0`. Überlauf kann vermieden werden, indem [`BigInt`](@ref) verwendet wird. Sehr große Ganzzahl-Literale verwenden einen breiteren Typ, zum Beispiel `10_000_000_000_000_000_000 isa Int128`.

Die ganzzahlige Division ist [`div`](@ref) Alias `÷`, während [`/`](@ref), das auf Ganzzahlen wirkt, [`Float64`](@ref) zurückgibt.

Siehe auch [`Int64`](@ref), [`widen`](@ref), [`typemax`](@ref), [`bitstring`](@ref).
