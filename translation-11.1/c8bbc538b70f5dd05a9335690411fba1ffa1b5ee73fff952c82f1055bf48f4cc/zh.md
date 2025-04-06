```
peel([T,] obj::GitObject)
```

递归剥离 `obj`，直到获得类型为 `T` 的对象。如果没有提供 `T`，则 `obj` 将被剥离直到类型发生变化。

  * `GitTag` 将被剥离到它所引用的对象。
  * `GitCommit` 将被剥离到 `GitTree`。
