```
eigvals!(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

Dasselbe wie [`eigvals`](@ref), aber spart Speicherplatz, indem es die Eingabe `A` überschreibt, anstatt eine Kopie zu erstellen. Die Schlüsselwörter `permute`, `scale` und `sortby` sind dieselben wie für [`eigen`](@ref).

!!! Hinweis     Die Eingabematrix `A` enthält nach dem Aufruf von `eigvals!` keine Eigenwerte mehr - `A` wird als Arbeitsbereich verwendet.

# Beispiele

```jldoctest
julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> eigvals!(A)
2-element Vector{Float64}:
 -0.3722813232690143
  5.372281323269014

julia> A
2×2 Matrix{Float64}:
 -0.372281  -1.0
  0.0        5.37228
```
