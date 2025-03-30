```
peel([T,] ref::GitReference)
```

递归剥离 `ref`，直到获得类型为 `T` 的对象。如果没有提供 `T`，则 `ref` 将被剥离，直到获得一个不是 [`GitTag`](@ref) 的对象。

  * `GitTag` 将被剥离到它所引用的对象。
  * [`GitCommit`](@ref) 将被剥离到 [`GitTree`](@ref)。

!!! note
    只有带注释的标签可以被剥离为 `GitTag` 对象。轻量标签（默认）是位于 `refs/tags/` 下的引用，直接指向 `GitCommit` 对象。

