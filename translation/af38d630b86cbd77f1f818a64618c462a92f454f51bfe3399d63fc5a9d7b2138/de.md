```
MersenneTwister(seed)
MersenneTwister()
```

Erstellen Sie ein `MersenneTwister` RNG-Objekt. Verschiedene RNG-Objekte können ihre eigenen Seeds haben, was nützlich sein kann, um verschiedene Ströme von Zufallszahlen zu generieren. Der `seed` kann eine Ganzzahl, ein String oder ein Vektor von `UInt32` Ganzzahlen sein. Wenn kein Seed angegeben wird, wird ein zufällig generierter Seed erstellt (unter Verwendung von Entropie aus dem System). Siehe die [`seed!`](@ref) Funktion zum Neusetzen eines bereits vorhandenen `MersenneTwister` Objekts.

!!! compat "Julia 1.11"
    Das Übergeben eines negativen ganzzahligen Seeds erfordert mindestens Julia 1.11.


# Beispiele

```jldoctest
julia> rng = MersenneTwister(123);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x2 = rand(MersenneTwister(123), 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x1 == x2
true
```
