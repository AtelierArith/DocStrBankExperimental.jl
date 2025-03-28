```
peel([T,] ref::GitReference)
```

Pelar recursivamente `ref` hasta obtener un objeto del tipo `T`. Si no se proporciona `T`, entonces `ref` se pelará hasta obtener un objeto que no sea un [`GitTag`](@ref).

  * Un `GitTag` se pelará al objeto que referencia.
  * Un [`GitCommit`](@ref) se pelará a un [`GitTree`](@ref).

!!! note
    Solo las etiquetas anotadas pueden pelarse a objetos `GitTag`. Las etiquetas ligeras (el valor predeterminado) son referencias bajo `refs/tags/` que apuntan directamente a objetos `GitCommit`.

