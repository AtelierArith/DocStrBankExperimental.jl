```
upstream(ref::GitReference) -> Union{GitReference, Nothing}
```

确定包含 `ref` 的分支是否具有指定的上游分支。

如果存在，则返回指向上游分支的 `GitReference`，如果请求的分支没有上游对应分支，则返回 [`nothing`](@ref)。
