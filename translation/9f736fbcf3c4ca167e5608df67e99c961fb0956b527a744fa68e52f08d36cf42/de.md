```
logrange(start, stop, length)
logrange(start, stop; length)
```

Konstruiere ein spezialisiertes Array, dessen Elemente logarithmisch zwischen den gegebenen Endpunkten verteilt sind. Das heißt, das Verhältnis aufeinanderfolgender Elemente ist konstant und wird aus der Länge berechnet.

Dies ist ähnlich wie `geomspace` in Python. Im Gegensatz zu `PowerRange` in Mathematica gibst du die Anzahl der Elemente an, nicht das Verhältnis. Im Gegensatz zu `logspace` in Python und Matlab sind die `start`- und `stop`-Argumente immer die ersten und letzten Elemente des Ergebnisses, nicht Potenzen, die auf eine Basis angewendet werden.

# Beispiele

```jldoctest
julia> logrange(10, 4000, length=3)
3-element Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 10.0, 200.0, 4000.0

julia> ans[2] ≈ sqrt(10 * 4000)  # mittleres Element ist das geometrische Mittel
true

julia> range(10, 40, length=3)[2] ≈ (10 + 40)/2  # arithmetisches Mittel
true

julia> logrange(1f0, 32f0, 11)
11-element Base.LogRange{Float32, Float64}:
 1.0, 1.41421, 2.0, 2.82843, 4.0, 5.65685, 8.0, 11.3137, 16.0, 22.6274, 32.0

julia> logrange(1, 1000, length=4) ≈ 10 .^ (0:3)
true
```

Siehe den [`LogRange`](@ref Base.LogRange) Typ für weitere Details.

Siehe auch [`range`](@ref) für linear verteilte Punkte.

!!! compat "Julia 1.11"
    Diese Funktion erfordert mindestens Julia 1.11.

