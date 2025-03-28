```
Colon()
```

Los dos puntos (:) se utilizan para significar la indexación de objetos o dimensiones enteras a la vez.

Muy pocas operaciones están definidas directamente sobre los dos puntos; en su lugar, se convierten mediante [`to_indices`](@ref) a un tipo de vector interno (`Base.Slice`) para representar la colección de índices que abarcan antes de ser utilizados.

La instancia singleton de `Colon` también es una función utilizada para construir rangos; consulta [`:`](@ref).
