```
asyncmap!(f, results, c...; ntasks=0, batch_size=nothing)
```

像 [`asyncmap`](@ref) 一样，但将输出存储在 `results` 中，而不是返回一个集合。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。

