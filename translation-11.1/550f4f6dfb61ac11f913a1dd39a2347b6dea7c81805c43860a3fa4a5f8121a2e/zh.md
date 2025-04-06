```
SubArray{T,N,P,I,L} <: AbstractArray{T,N}
```

`N`维视图，指向父数组（类型为 `P`），元素类型为 `T`，由索引元组（类型为 `I`）限制。`L` 对于支持快速线性索引的类型为真，反之为假。

使用 [`view`](@ref) 函数构造 `SubArray`。
