```
symdiff!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

构造传入集合的对称差，并用结果覆盖 `s`。当 `s` 是数组时，顺序会被保持。请注意，在这种情况下，元素的重复性是重要的。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。

