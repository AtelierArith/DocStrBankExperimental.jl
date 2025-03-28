```
x && y
```

Évaluation booléenne avec court-circuit.

Voir aussi [`&`](@ref), l'opérateur ternaire `? :`, et la section du manuel sur [le flux de contrôle](@ref man-conditional-evaluation).

# Exemples

```jldoctest
julia> x = 3;

julia> x > 1 && x < 10 && x isa Int
true

julia> x < 0 && error("expected positive x")
false
```
