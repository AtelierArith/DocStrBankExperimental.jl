```
randsubseq([rng=default_rng(),] A, p) -> Vector
```

返回一个向量，该向量由给定数组 `A` 的随机子序列组成，其中 `A` 的每个元素以独立概率 `p` 包含（按顺序）。 （复杂度是 `p*length(A)` 的线性，因此即使 `p` 较小而 `A` 较大，该函数也是高效的。）从技术上讲，这个过程被称为 `A` 的“伯努利抽样”。

# 示例

```jldoctest
julia> randsubseq(Xoshiro(123), 1:8, 0.3)
2-element Vector{Int64}:
 4
 7
```
