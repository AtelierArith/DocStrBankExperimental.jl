```
peel([T,] obj::GitObject)
```

Pelar recursivamente `obj` hasta obtener un objeto del tipo `T`. Si no se proporciona `T`, entonces `obj` se pelará hasta que el tipo cambie.

  * Un `GitTag` se pelará hasta el objeto que referencia.
  * Un `GitCommit` se pelará hasta un `GitTree`.
