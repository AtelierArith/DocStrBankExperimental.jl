```
randsubseq!([rng=default_rng(),] S, A, p)
```

与 [`randsubseq`](@ref) 类似，但结果存储在 `S` 中（根据需要调整大小）。

# 示例

```jldoctest
julia> S = Int64[];

julia> randsubseq!(Xoshiro(123), S, 1:8, 0.3)
2-element Vector{Int64}:
 4
 7

julia> S
2-element Vector{Int64}:
 4
 7
```
