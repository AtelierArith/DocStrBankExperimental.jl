```
PermutedDimsArray(A, perm) -> B
```

给定一个 AbstractArray `A`，创建一个视图 `B`，使得维度看起来被置换。类似于 `permutedims`，但不进行复制（`B` 与 `A` 共享存储）。

另请参见 [`permutedims`](@ref)，[`invperm`](@ref)。

# 示例

```jldoctest
julia> A = rand(3,5,4);

julia> B = PermutedDimsArray(A, (3,1,2));

julia> size(B)
(4, 3, 5)

julia> B[3,1,2] == A[1,2,3]
true
```
