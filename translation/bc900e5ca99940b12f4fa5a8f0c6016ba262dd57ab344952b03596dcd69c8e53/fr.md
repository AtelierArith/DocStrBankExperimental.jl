```
IteratorEltype(itertype::Type) -> IteratorEltype
```

Étant donné le type d'un itérateur, renvoie l'une des valeurs suivantes :

  * `EltypeUnknown()` si le type des éléments produits par l'itérateur n'est pas connu à l'avance.
  * `HasEltype()` si le type d'élément est connu, et [`eltype`](@ref) renverrait une valeur significative.

`HasEltype()` est la valeur par défaut, car on suppose que les itérateurs implémentent [`eltype`](@ref).

Ce trait est généralement utilisé pour sélectionner entre des algorithmes qui pré-allouent un type de résultat spécifique, et des algorithmes qui choisissent un type de résultat en fonction des types des valeurs produites.

```jldoctest
julia> Base.IteratorEltype(1:5)
Base.HasEltype()
```
