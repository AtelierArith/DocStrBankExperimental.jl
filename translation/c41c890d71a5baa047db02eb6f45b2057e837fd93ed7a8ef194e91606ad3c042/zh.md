```
randn([rng=default_rng()], [T=Float64], [dims...])
```

生成一个均值为0、标准差为1的类型为`T`的正态分布随机数。给定可选的`dims`参数，生成一个大小为`dims`的数组。Julia的标准库支持对任何实现了[`rand`](@ref)的浮点类型使用`randn`，例如`Base`类型的[`Float16`](@ref)、[`Float32`](@ref)、[`Float64`](@ref)（默认）和[`BigFloat`](@ref)，以及它们的[`Complex`](@ref)对应类型。

（当`T`为复数时，值是从方差为1的圆对称复正态分布中抽取的，实部和虚部具有独立的正态分布，均值为零，方差为`1/2`）。

另见[`randn!`](@ref)以进行就地操作。

# 示例

生成一个单一的随机数（使用默认的`Float64`类型）：

```julia-repl
julia> randn()
-0.942481877315864
```

生成一个正态随机数矩阵（使用默认的`Float64`类型）：

```julia-repl
julia> randn(2,3)
2×3 Matrix{Float64}:
  1.18786   -0.678616   1.49463
 -0.342792  -0.134299  -1.45005
```

使用用户定义的种子设置随机数生成器`rng`（以便生成可重复的数字），并使用它生成一个随机的`Float32`数字或一个`ComplexF32`随机数矩阵：

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> randn(rng, Float32)
-0.6457307f0

julia> randn(rng, ComplexF32, (2, 3))
2×3 Matrix{ComplexF32}:
  -1.03467-1.14806im  0.693657+0.056538im   0.291442+0.419454im
 -0.153912+0.34807im    1.0954-0.948661im  -0.543347-0.0538589im
```
