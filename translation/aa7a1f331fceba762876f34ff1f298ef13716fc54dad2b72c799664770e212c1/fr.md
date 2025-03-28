```
type abstrait
```

`type abstrait` déclare un type qui ne peut pas être instancié et sert uniquement de nœud dans le graphe des types, décrivant ainsi des ensembles de types concrets liés : ces types concrets qui en sont les descendants. Les types abstraits forment la hiérarchie conceptuelle qui rend le système de types de Julia plus qu'une simple collection d'implémentations d'objets. Par exemple :

```julia
type abstrait Nombre fin
type abstrait Réel <: Nombre fin
```

[`Nombre`](@ref) n'a pas de supertype, tandis que [`Réel`](@ref) est un sous-type abstrait de `Nombre`.
