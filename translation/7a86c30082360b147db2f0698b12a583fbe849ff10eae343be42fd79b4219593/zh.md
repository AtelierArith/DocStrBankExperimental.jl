```
Xoshiro(seed::Union{Integer, AbstractString})
Xoshiro()
```

Xoshiro256++ 是一个快速的伪随机数生成器，由 David Blackman 和 Sebastiano Vigna 在 "Scrambled Linear Pseudorandom Number Generators" 中描述，发表于 ACM Trans. Math. Softw., 2021。参考实现可在 https://prng.di.unimi.it 获取。

除了高速外，Xoshiro 还具有小内存占用，使其适合于需要长时间保持许多不同随机状态的应用。

Julia 的 Xoshiro 实现具有批量生成模式；它从父级种子生成新的虚拟 PRNG，并使用 SIMD 进行并行生成（即批量流由多个交错的 xoshiro 实例组成）。一旦批量请求得到处理，虚拟 PRNG 将被丢弃（并且不应导致任何堆分配）。

如果未提供种子，将创建一个随机生成的种子（使用系统的熵）。有关重新种植已存在的 `Xoshiro` 对象，请参见 [`seed!`](@ref) 函数。

!!! compat "Julia 1.11"
    传递负整数种子需要至少 Julia 1.11。


# 示例

```jldoctest
julia> using Random

julia> rng = Xoshiro(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> rng = Xoshiro(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true
```
