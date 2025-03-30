```
ismutabletype(T) -> Bool
```

确定类型 `T` 是否被声明为可变类型（即使用 `mutable struct` 关键字）。如果 `T` 不是一个类型，则返回 `false`。

!!! compat "Julia 1.7"
    此函数至少需要 Julia 1.7。

