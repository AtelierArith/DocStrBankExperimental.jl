```
accumulate(op, A; dims::Integer, [init])
```

Kumulative Operation `op` entlang der Dimension `dims` von `A` (wobei `dims` für Vektoren optional ist). Ein Anfangswert `init` kann optional durch ein Schlüsselwort-Argument bereitgestellt werden. Siehe auch [`accumulate!`](@ref), um ein vorab zugewiesenes Ausgabearray zu verwenden, sowohl für die Leistung als auch um die Genauigkeit der Ausgabe zu steuern (z. B. um Überlauf zu vermeiden).

Für gängige Operationen gibt es spezialisierte Varianten von `accumulate`, siehe [`cumsum`](@ref), [`cumprod`](@ref). Für eine faule Version siehe [`Iterators.accumulate`](@ref).

!!! compat "Julia 1.5"
    `accumulate` auf einem Nicht-Array-Iterator erfordert mindestens Julia 1.5.


# Beispiele

```jldoctest
julia> accumulate(+, [1,2,3])
3-element Vector{Int64}:
 1
 3
 6

julia> accumulate(min, (1, -2, 3, -4, 5), init=0)
(0, -2, -2, -4, -4)

julia> accumulate(/, (2, 4, Inf), init=100)
(50.0, 12.5, 0.0)

julia> accumulate(=>, i^2 for i in 1:3)
3-element Vector{Any}:
          1
        1 => 4
 (1 => 4) => 9

julia> accumulate(+, fill(1, 3, 4))
3×4 Matrix{Int64}:
 1  4  7  10
 2  5  8  11
 3  6  9  12

julia> accumulate(+, fill(1, 2, 5), dims=2, init=100.0)
2×5 Matrix{Float64}:
 101.0  102.0  103.0  104.0  105.0
 101.0  102.0  103.0  104.0  105.0
```
