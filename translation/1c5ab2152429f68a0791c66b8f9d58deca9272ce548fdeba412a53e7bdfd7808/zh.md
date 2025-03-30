```
intersect!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

交集所有传入的集合，并用结果覆盖`s`。对于数组保持顺序。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。

