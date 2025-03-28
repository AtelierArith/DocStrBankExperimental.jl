```
ScopedValue(x)
```

Créez un conteneur qui propage des valeurs à travers des portées dynamiques. Utilisez [`with`](@ref) pour créer et entrer une nouvelle portée dynamique.

Les valeurs ne peuvent être définies que lors de l'entrée dans une nouvelle portée dynamique, et la valeur référencée sera constante pendant l'exécution d'une portée dynamique.

Les portées dynamiques sont propagées à travers les tâches.

# Exemples

```jldoctest
julia> using Base.ScopedValues;

julia> const sval = ScopedValue(1);

julia> sval[]
1

julia> with(sval => 2) do
           sval[]
       end
2

julia> sval[]
1
```

!!! compat "Julia 1.11"
    Les valeurs scoping ont été introduites dans Julia 1.11. Dans Julia 1.8+, une implémentation compatible est disponible à partir du package ScopedValues.jl.

