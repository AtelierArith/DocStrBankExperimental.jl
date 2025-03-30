```
eigmax(A; permute::Bool=true, scale::Bool=true)
```

返回 `A` 的最大特征值。选项 `permute=true` 会对矩阵进行排列，使其更接近上三角形状，而 `scale=true` 会通过其对角元素对矩阵进行缩放，以使行和列的范数更为相等。请注意，如果 `A` 的特征值是复数，则此方法将失败，因为复数无法排序。

# 示例

```jldoctest
julia> A = [0 im; -im 0]
2×2 Matrix{Complex{Int64}}:
 0+0im  0+1im
 0-1im  0+0im

julia> eigmax(A)
1.0

julia> A = [0 im; -1 0]
2×2 Matrix{Complex{Int64}}:
  0+0im  0+1im
 -1+0im  0+0im

julia> eigmax(A)
ERROR: DomainError with Complex{Int64}[0+0im 0+1im; -1+0im 0+0im]:
`A` 不能有复数特征值。
Stacktrace:
[...]
```
