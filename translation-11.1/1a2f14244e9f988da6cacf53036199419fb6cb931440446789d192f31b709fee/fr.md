```
peel([T,] ref::GitReference)
```

Peler récursivement `ref` jusqu'à obtenir un objet de type `T`. Si aucun `T` n'est fourni, alors `ref` sera pelé jusqu'à obtenir un objet autre qu'un [`GitTag`](@ref).

  * Un `GitTag` sera pelé vers l'objet qu'il référence.
  * Un [`GitCommit`](@ref) sera pelé vers un [`GitTree`](@ref).

!!! note
    Seules les étiquettes annotées peuvent être pelées vers des objets `GitTag`. Les étiquettes légères (par défaut) sont des références sous `refs/tags/` qui pointent directement vers des objets `GitCommit`.

