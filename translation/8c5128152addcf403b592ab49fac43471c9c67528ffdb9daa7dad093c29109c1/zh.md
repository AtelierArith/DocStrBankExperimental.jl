```
mapslices(f, A; dims)
```

通过在每个切片 `A[..., :, ..., :, ...]` 上应用函数 `f`，转换数组 `A` 的给定维度，其中在 `dims` 中的每个 `d` 位置都有一个冒号。结果沿着其余维度连接。

例如，如果 `dims = [1,2]` 且 `A` 是 4 维的，则 `f` 在 `x = A[:,:,i,j]` 上被调用，针对所有的 `i` 和 `j`，并且 `f(x)` 在结果 `R` 中变为 `R[:,:,i,j]`。

另见 [`eachcol`](@ref) 或 [`eachslice`](@ref)，与 [`map`](@ref) 或 [`stack`](@ref) 一起使用。

# 示例

```jldoctest
julia> A = reshape(1:30,(2,5,3))
2×5×3 reshape(::UnitRange{Int64}, 2, 5, 3) with eltype Int64:
[:, :, 1] =
 1  3  5  7   9
 2  4  6  8  10

[:, :, 2] =
 11  13  15  17  19
 12  14  16  18  20

[:, :, 3] =
 21  23  25  27  29
 22  24  26  28  30

julia> f(x::Matrix) = fill(x[1,1], 1,4);  # 返回一个 1×4 矩阵

julia> B = mapslices(f, A, dims=(1,2))
1×4×3 Array{Int64, 3}:
[:, :, 1] =
 1  1  1  1

[:, :, 2] =
 11  11  11  11

[:, :, 3] =
 21  21  21  21

julia> f2(x::AbstractMatrix) = fill(x[1,1], 1,4);

julia> B == stack(f2, eachslice(A, dims=3))
true

julia> g(x) = x[begin] // x[end-1];  # 返回一个数字

julia> mapslices(g, A, dims=[1,3])
1×5×1 Array{Rational{Int64}, 3}:
[:, :, 1] =
 1//21  3//23  1//5  7//27  9//29

julia> map(g, eachslice(A, dims=2))
5-element Vector{Rational{Int64}}:
 1//21
 3//23
 1//5
 7//27
 9//29

julia> mapslices(sum, A; dims=(1,3)) == sum(A; dims=(1,3))
true
```

注意，在 `eachslice(A; dims=2)` 中，指定的维度是切片中 *没有* 冒号的那个维度。这是 `view(A,:,i,:)`，而 `mapslices(f, A; dims=(1,3))` 使用的是 `A[:,i,:]`。函数 `f` 可以在切片中修改值，而不影响 `A`。
