```
randcycle([rng=default_rng(),] n::Integer)
```

Konstruiere eine zufällige zyklische Permutation der Länge `n`. Das optionale Argument `rng` gibt einen Zufallszahlengenerator an, siehe [Zufallszahlen](@ref). Der Elementtyp des Ergebnisses ist derselbe wie der Typ von `n`.

Hier bedeutet eine "zyklische Permutation", dass alle Elemente innerhalb eines einzigen Zyklus liegen. Wenn `n > 0` ist, gibt es $(n-1)!$ mögliche zyklische Permutationen, die gleichmäßig ausgewählt werden. Wenn `n == 0` ist, gibt `randcycle` einen leeren Vektor zurück.

[`randcycle!`](@ref) ist eine In-Place-Variante dieser Funktion.

!!! compat "Julia 1.1"
    In Julia 1.1 und höher gibt `randcycle` einen Vektor `v` zurück, bei dem `eltype(v) == typeof(n)` ist, während in Julia 1.0 `eltype(v) == Int` ist.


# Beispiele

```jldoctest
julia> randcycle(Xoshiro(123), 6)
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
