```
randcycle!([rng=default_rng(),] A::Array{<:Integer})
```

Konstruiere in `A` eine zufällige zyklische Permutation der Länge `n = length(A)`. Das optionale Argument `rng` gibt einen Zufallszahlengenerator an, siehe [Zufallszahlen](@ref).

Hier bedeutet eine "zyklische Permutation", dass alle Elemente innerhalb eines einzigen Zyklus liegen. Wenn `A` nicht leer ist (`n > 0`), gibt es $(n-1)!$ mögliche zyklische Permutationen, die gleichmäßig ausgewählt werden. Wenn `A` leer ist, bleibt `randcycle!` unverändert.

[`randcycle`](@ref) ist eine Variante dieser Funktion, die einen neuen Vektor allokiert.

# Beispiele

```jldoctest
julia> randcycle!(Xoshiro(123), Vector{Int}(undef, 6))
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
