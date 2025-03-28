```
randn([rng=default_rng()], [T=Float64], [dims...])
```

Generiert eine normalverteilte Zufallszahl vom Typ `T` mit einem Mittelwert von 0 und einer Standardabweichung von 1. Gegebenenfalls werden mit dem optionalen Argument `dims` ein Array der Größe `dims` solcher Zahlen generiert. Die Standardbibliothek von Julia unterstützt `randn` für jeden Fließkommatyp, der [`rand`](@ref) implementiert, z. B. die `Base`-Typen [`Float16`](@ref), [`Float32`](@ref), [`Float64`](@ref) (der Standard) und [`BigFloat`](@ref), zusammen mit ihren [`Complex`](@ref) Gegenstücken.

(Wenn `T` komplex ist, werden die Werte aus der zirkular symmetrischen komplexen Normalverteilung mit einer Varianz von 1 gezogen, wobei die reellen und imaginären Teile eine unabhängige Normalverteilung mit einem Mittelwert von null und einer Varianz von `1/2` haben).

Siehe auch [`randn!`](@ref), um in-place zu arbeiten.

# Beispiele

Generierung einer einzelnen Zufallszahl (mit dem Standardtyp `Float64`):

```julia-repl
julia> randn()
-0.942481877315864
```

Generierung einer Matrix normalverteilter Zufallszahlen (mit dem Standardtyp `Float64`):

```julia-repl
julia> randn(2,3)
2×3 Matrix{Float64}:
  1.18786   -0.678616   1.49463
 -0.342792  -0.134299  -1.45005
```

Einrichtung des Zufallszahlengenerators `rng` mit einem benutzerdefinierten Seed (für reproduzierbare Zahlen) und Verwendung zur Generierung einer zufälligen `Float32`-Zahl oder einer Matrix von `ComplexF32`-Zufallszahlen:

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> randn(rng, Float32)
-0.6457307f0

julia> randn(rng, ComplexF32, (2, 3))
2×3 Matrix{ComplexF32}:
  -1.03467-1.14806im  0.693657+0.056538im   0.291442+0.419454im
 -0.153912+0.34807im    1.0954-0.948661im  -0.543347-0.0538589im
```
