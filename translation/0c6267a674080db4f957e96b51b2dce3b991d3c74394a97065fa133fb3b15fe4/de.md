```
seed!([rng=default_rng()], seed) -> rng
seed!([rng=default_rng()]) -> rng
```

Setze den Zufallszahlengenerator zurück: `rng` gibt eine reproduzierbare Zahlenfolge nur dann zurück, wenn ein `seed` bereitgestellt wird. Einige RNGs akzeptieren keinen Seed, wie `RandomDevice`. Nach dem Aufruf von `seed!` ist `rng` gleichwertig zu einem neu erstellten Objekt, das mit demselben Seed initialisiert wurde. Die Arten von akzeptierten Seeds hängen vom Typ von `rng` ab, aber im Allgemeinen sollten ganze Zahlen als Seeds funktionieren.

Wenn `rng` nicht angegeben ist, wird standardmäßig der Zustand des gemeinsamen, aufgabenlokalen Generators initialisiert.

# Beispiele

```julia-repl
julia> Random.seed!(1234);

julia> x1 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> Random.seed!(1234);

julia> x2 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true

julia> rng = Xoshiro(1234); rand(rng, 2) == x1
true

julia> Xoshiro(1) == Random.seed!(rng, 1)
true

julia> rand(Random.seed!(rng), Bool) # nicht reproduzierbar
true

julia> rand(Random.seed!(rng), Bool) # auch nicht reproduzierbar
false

julia> rand(Xoshiro(), Bool) # auch nicht reproduzierbar
true
```
