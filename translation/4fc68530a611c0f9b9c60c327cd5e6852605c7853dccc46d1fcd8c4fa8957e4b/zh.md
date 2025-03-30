```
dropdims(A; dims)
```

返回一个与 `A` 具有相同数据的数组，但移除了由 `dims` 指定的维度。`size(A,d)` 必须对 `dims` 中的每个 `d` 等于 1，且禁止重复的维度或超出 `1:ndims(A)` 的数字。

结果与 `A` 共享相同的底层数据，因此结果是可变的当且仅当 `A` 是可变的，并且一个的元素设置会改变另一个的值。

另请参见: [`reshape`](@ref), [`vec`](@ref).

# 示例

```jldoctest
julia> a = reshape(Vector(1:4),(2,2,1,1))
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

julia> b = dropdims(a; dims=3)
2×2×1 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

julia> b[1,1,1] = 5; a
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 5  3
 2  4
```
