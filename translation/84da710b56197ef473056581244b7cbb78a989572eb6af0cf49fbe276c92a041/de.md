```
LinRange{T,L}
```

Ein Bereich mit `len` linear verteilten Elementen zwischen `start` und `stop`. Die Größe des Abstands wird durch `len` gesteuert, das eine `Integer` sein muss.

# Beispiele

```jldoctest
julia> LinRange(1.5, 5.5, 9)
9-element LinRange{Float64, Int64}:
 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0, 5.5
```

Im Vergleich zur Verwendung von [`range`](@ref) sollte die direkte Konstruktion eines `LinRange` weniger Overhead haben, wird jedoch nicht versuchen, Floating-Point-Fehler zu korrigieren:

```jldoctest
julia> collect(range(-0.1, 0.3, length=5))
5-element Vector{Float64}:
 -0.1
  0.0
  0.1
  0.2
  0.3

julia> collect(LinRange(-0.1, 0.3, 5))
5-element Vector{Float64}:
 -0.1
 -1.3877787807814457e-17
  0.09999999999999999
  0.19999999999999998
  0.3
```

Siehe auch [`Logrange`](@ref Base.LogRange) für logarithmisch verteilte Punkte.
