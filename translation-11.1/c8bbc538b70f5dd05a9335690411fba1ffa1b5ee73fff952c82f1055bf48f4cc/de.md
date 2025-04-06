```
peel([T,] obj::GitObject)
```

Rekursiv `obj` schälen, bis ein Objekt vom Typ `T` erhalten wird. Wenn kein `T` angegeben ist, wird `obj` geschält, bis sich der Typ ändert.

  * Ein `GitTag` wird zum Objekt geschält, auf das es verweist.
  * Ein `GitCommit` wird zu einem `GitTree` geschält.
