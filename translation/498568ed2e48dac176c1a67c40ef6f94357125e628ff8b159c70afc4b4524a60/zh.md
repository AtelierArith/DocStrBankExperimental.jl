```
setindex!(A, X, inds...)
A[inds...] = X
```

将数组 `X` 中的值存储在 `A` 的某个子集内，具体由 `inds` 指定。语法 `A[inds...] = X` 等价于 `(setindex!(A, X, inds...); X)`。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


# 示例

```jldoctest
julia> A = zeros(2,2);

julia> setindex!(A, [10, 20], [1, 2]);

julia> A[[3, 4]] = [30, 40];

julia> A
2×2 Matrix{Float64}:
 10.0  30.0
 20.0  40.0
```
