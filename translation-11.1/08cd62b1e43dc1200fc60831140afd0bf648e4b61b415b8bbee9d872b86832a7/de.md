```
sprand([rng],[T::Type],m,[n],p::AbstractFloat)
sprand([rng],m,[n],p::AbstractFloat,[rfn=rand])
```

Erstellt einen zufälligen Längen `m` spärlichen Vektor oder eine `m` mal `n` spärliche Matrix, in der die Wahrscheinlichkeit, dass ein Element ungleich null ist, unabhängig durch `p` gegeben ist (und somit die durchschnittliche Dichte der Nicht-Null-Werte ebenfalls genau `p` beträgt). Das optionale Argument `rng` gibt einen Zufallszahlengenerator an, siehe [Zufallszahlen](@ref). Das optionale Argument `T` gibt den Elementtyp an, der standardmäßig auf `Float64` gesetzt ist.

Standardmäßig werden Nicht-Null-Werte aus einer gleichmäßigen Verteilung unter Verwendung der [`rand`](@ref) Funktion ausgewählt, d.h. durch `rand(T)` oder `rand(rng, T)`, wenn `rng` angegeben ist; für das Standard `T=Float64` entspricht dies Nicht-Null-Werten, die gleichmäßig in `[0,1)` ausgewählt werden.

Sie können Nicht-Null-Werte aus einer anderen Verteilung auswählen, indem Sie eine benutzerdefinierte `rfn` Funktion anstelle von `rand` übergeben. Dies sollte eine Funktion `rfn(k)` sein, die ein Array von `k` Zufallszahlen zurückgibt, die aus der gewünschten Verteilung ausgewählt wurden; alternativ, wenn `rng` angegeben ist, sollte es stattdessen eine Funktion `rfn(rng, k)` sein.

# Beispiele

```jldoctest; setup = :(using Random; Random.seed!(1234))
julia> sprand(Bool, 2, 2, 0.5)
2×2 SparseMatrixCSC{Bool, Int64} mit 2 gespeicherten Einträgen:
 1  1
 ⋅  ⋅

julia> sprand(Float64, 3, 0.75)
3-element SparseVector{Float64, Int64} mit 2 gespeicherten Einträgen:
  [1]  =  0.795547
  [2]  =  0.49425
```
