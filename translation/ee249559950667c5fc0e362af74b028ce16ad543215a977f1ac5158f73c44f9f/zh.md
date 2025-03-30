```
reshape(A, dims...) -> AbstractArray
reshape(A, dims) -> AbstractArray
```

返回一个与 `A` 具有相同数据的数组，但具有不同的维度大小或维度数量。这两个数组共享相同的底层数据，因此结果是可变的当且仅当 `A` 是可变的，并且设置一个的元素会改变另一个的值。

新维度可以作为参数列表或形状元组指定。最多可以用 `:` 指定一个维度，在这种情况下，其长度会被计算为与所有指定维度的乘积等于原始数组 `A` 的长度。元素的总数必须保持不变。

# 示例

```jldoctest
julia> A = Vector(1:16)
16-element Vector{Int64}:
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16

julia> reshape(A, (4, 4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reshape(A, 2, :)
2×8 Matrix{Int64}:
 1  3  5  7   9  11  13  15
 2  4  6  8  10  12  14  16

julia> reshape(1:6, 2, 3)
2×3 reshape(::UnitRange{Int64}, 2, 3) with eltype Int64:
 1  3  5
 2  4  6
```
