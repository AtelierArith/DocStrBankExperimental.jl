```
circshift!(dest, src, shifts)
```

循环移动，即旋转，`src` 中的数据，将结果存储在 `dest` 中。`shifts` 指定每个维度的移动量。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


另见 [`circshift`](@ref).
