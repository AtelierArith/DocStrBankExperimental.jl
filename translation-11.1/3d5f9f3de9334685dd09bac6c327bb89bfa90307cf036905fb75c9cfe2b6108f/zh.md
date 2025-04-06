```
BitArray{N} <: AbstractArray{Bool, N}
```

节省空间的 `N` 维布尔数组，每个布尔值仅使用一个比特。

`BitArray` 将最多 64 个值打包到每 8 字节中，导致相对于 `Array{Bool, N}` 的 8 倍空间效率，并允许某些操作一次处理 64 个值。

默认情况下，Julia 从生成布尔元素的 [broadcasting](@ref Broadcasting) 操作（包括像 `.==` 这样的点比较）以及从函数 [`trues`](@ref) 和 [`falses`](@ref) 返回 `BitArrays`。

!!! note
    由于其打包存储格式，`BitArray` 的元素的并发访问（其中至少有一个是写入）不是线程安全的。

