```
AbstractIrrational <: Real
```

Type numérique représentant une valeur irrationnelle exacte, qui est automatiquement arrondie à la précision correcte dans les opérations arithmétiques avec d'autres quantités numériques.

Les sous-types `MyIrrational <: AbstractIrrational` doivent implémenter au moins `==(::MyIrrational, ::MyIrrational)`, `hash(x::MyIrrational, h::UInt)`, et `convert(::Type{F}, x::MyIrrational) where {F <: Union{BigFloat,Float32,Float64}}`.

Si un sous-type est utilisé pour représenter des valeurs qui peuvent occasionnellement être rationnelles (par exemple, un type de racine carrée qui représente `√n` pour des entiers `n` donnera un résultat rationnel lorsque `n` est un carré parfait), il doit également implémenter `isinteger`, `iszero`, `isone`, et `==` avec des valeurs `Real` (puisque tous ces derniers par défaut renvoient `false` pour les types `AbstractIrrational`), ainsi que définir [`hash`](@ref) pour être égal à celui du `Rational` correspondant.
