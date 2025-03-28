```
randperm([rng=default_rng(),] n::Integer)
```

Konstruiere eine zufällige Permutation der Länge `n`. Das optionale Argument `rng` gibt einen Zufallszahlengenerator an (siehe [Zufallszahlen](@ref)). Der Elementtyp des Ergebnisses ist derselbe wie der Typ von `n`.

Um einen beliebigen Vektor zufällig zu permutieren, siehe [`shuffle`](@ref) oder [`shuffle!`](@ref).

!!! compat "Julia 1.1"
    In Julia 1.1 gibt `randperm` einen Vektor `v` zurück, bei dem `eltype(v) == typeof(n)` ist, während in Julia 1.0 `eltype(v) == Int` ist.


# Beispiele

```jldoctest
julia> randperm(Xoshiro(123), 4)
4-element Vector{Int64}:
 1
 4
 2
 3
```
