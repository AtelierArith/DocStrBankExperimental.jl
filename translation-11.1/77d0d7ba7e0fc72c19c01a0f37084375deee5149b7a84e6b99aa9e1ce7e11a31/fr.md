```
mutable struct
```

`mutable struct` est similaire à [`struct`](@ref), mais permet en plus de modifier les champs du type après sa construction.

Les champs individuels d'un mutable struct peuvent être marqués comme `const` pour les rendre immuables :

```julia
mutable struct Baz
    a::Int
    const b::Float64
end
```

!!! compat "Julia 1.8"
    Le mot-clé `const` pour les champs des mutable structs nécessite au moins Julia 1.8.


Consultez la section du manuel sur [Composite Types](@ref) pour plus d'informations.
