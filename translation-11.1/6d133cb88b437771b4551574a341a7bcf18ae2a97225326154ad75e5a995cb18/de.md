```
sprandn([rng][,Typ],m[,n],p::AbstractFloat)
```

Erstellt einen zufälligen spärlichen Vektor der Länge `m` oder eine spärliche Matrix der Größe `m` mal `n` mit der angegebenen (unabhängigen) Wahrscheinlichkeit `p`, dass ein Eintrag ungleich null ist, wobei ungleich null Werte aus der Normalverteilung entnommen werden. Das optionale Argument `rng` gibt einen Zufallszahlengenerator an, siehe [Zufallszahlen](@ref).

!!! compat "Julia 1.1"
    Die Angabe des Ausgabeelementtyps `Typ` erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> sprandn(2, 2, 0.75)
2×2 SparseMatrixCSC{Float64, Int64} mit 3 gespeicherten Einträgen:
 -1.20577     ⋅
  0.311817  -0.234641
```
