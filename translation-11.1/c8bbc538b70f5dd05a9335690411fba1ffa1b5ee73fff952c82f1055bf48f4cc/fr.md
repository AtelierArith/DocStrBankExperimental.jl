```
peel([T,] obj::GitObject)
```

Peler récursivement `obj` jusqu'à ce qu'un objet de type `T` soit obtenu. Si aucun `T` n'est fourni, alors `obj` sera pelé jusqu'à ce que le type change.

  * Un `GitTag` sera pelé vers l'objet qu'il référence.
  * Un `GitCommit` sera pelé vers un `GitTree`.
