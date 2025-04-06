```
Colon()
```

Les deux-points (:) sont utilisés pour signifier l'indexation d'objets ou de dimensions entiers à la fois.

Très peu d'opérations sont définies directement sur les deux-points ; au lieu de cela, ils sont convertis par [`to_indices`](@ref) en un type de vecteur interne (`Base.Slice`) pour représenter la collection d'indices qu'ils couvrent avant d'être utilisés.

L'instance singleton de `Colon` est également une fonction utilisée pour construire des plages ; voir [`:`](@ref).
