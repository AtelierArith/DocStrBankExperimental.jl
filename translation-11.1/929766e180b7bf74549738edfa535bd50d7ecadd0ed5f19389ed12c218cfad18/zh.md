```
copyto!(dest::AbstractArray, src) -> dest
```

将集合 `src` 中的所有元素复制到数组 `dest`，其长度必须大于或等于 `src` 的长度 `n`。`dest` 的前 `n` 个元素将被覆盖，其他元素保持不变。

另请参见 [`copy!`](@ref Base.copy!), [`copy`](@ref)。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


# 示例

```jldoctest
julia> x = [1., 0., 3., 0., 5.];

julia> y = zeros(7);

julia> copyto!(y, x);

julia> y
7-element Vector{Float64}:
 1.0
 0.0
 3.0
 0.0
 5.0
 0.0
 0.0
```
