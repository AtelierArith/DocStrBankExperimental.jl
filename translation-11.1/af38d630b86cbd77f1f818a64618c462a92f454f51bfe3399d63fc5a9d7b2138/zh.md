```
MersenneTwister(seed)
MersenneTwister()
```

创建一个 `MersenneTwister` RNG 对象。不同的 RNG 对象可以有自己的种子，这可能对生成不同的随机数流很有用。`seed` 可以是一个整数、一个字符串或一个 `UInt32` 整数的向量。如果没有提供种子，将创建一个随机生成的种子（使用系统的熵）。请参见 [`seed!`](@ref) 函数以重新为已存在的 `MersenneTwister` 对象设置种子。

!!! compat "Julia 1.11"
    传递一个负整数种子需要至少 Julia 1.11。


# 示例

```jldoctest
julia> rng = MersenneTwister(123);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x2 = rand(MersenneTwister(123), 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x1 == x2
true
```
