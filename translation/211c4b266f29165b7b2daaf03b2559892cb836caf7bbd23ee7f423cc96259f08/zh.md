```
elsize(type)
```

计算在给定 `type` 中存储的 [`eltype`](@ref) 的连续元素之间的内存步幅（以字节为单位），如果数组元素以均匀线性步幅密集存储。

# 示例

```jldoctest
julia> Base.elsize(rand(Float32, 10))
4
```
