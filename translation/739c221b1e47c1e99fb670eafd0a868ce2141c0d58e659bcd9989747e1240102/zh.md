```@meta
EditURL = "https://github.com/JuliaLang/julia/blob/master/stdlib/Random/docs/src/index.md"
```

# Random Numbers

```@meta
DocTestSetup = :(using Random)
```

在 Julia 中，随机数生成默认使用 [Xoshiro256++](https://prng.di.unimi.it/) 算法，并具有每个 `Task` 的状态。其他 RNG 类型可以通过继承 `AbstractRNG` 类型进行插入；然后可以使用它们来获取多个随机数流。

`Random` 包导出的 PRNG（伪随机数生成器）有：

  * `TaskLocalRNG`：一个表示使用当前活动任务局部流的令牌，该流是从父任务确定性地播种的，或者在程序启动时由 `RandomDevice`（使用系统随机性）播种。
  * `Xoshiro`：使用 Xoshiro256++ 算法生成高质量的随机数流，具有小状态向量和高性能。
  * `RandomDevice`：用于操作系统提供的熵。这可以用于加密安全的随机数（CS(P)RNG）。
  * `MersenneTwister`：一种替代的高质量伪随机数生成器（PRNG），在旧版本的Julia中是默认的，速度也相当快，但需要更多的空间来存储状态向量和生成随机序列。

大多数与随机生成相关的函数接受一个可选的 `AbstractRNG` 对象作为第一个参数。有些函数还接受维度规格 `dims...`（也可以作为元组给出）来生成随机值的数组。在多线程程序中，通常应该使用来自不同线程或任务的不同 RNG 对象，以确保线程安全。然而，从 Julia 1.3 开始，默认的 RNG 是线程安全的（在 1.6 版本之前使用每线程 RNG，从那以后使用每任务 RNG）。

提供的随机数生成器可以生成以下类型的均匀随机数： [`Float16`](@ref)， [`Float32`](@ref)， [`Float64`](@ref)， [`BigFloat`](@ref)， [`Bool`](@ref)， [`Int8`](@ref)， [`UInt8`](@ref)， [`Int16`](@ref)， [`UInt16`](@ref)， [`Int32`](@ref)， [`UInt32`](@ref)， [`Int64`](@ref)， [`UInt64`](@ref)， [`Int128`](@ref)， [`UInt128`](@ref)， [`BigInt`](@ref)（或这些类型的复数）。随机浮点数在 $[0, 1)$ 区间内均匀生成。由于 `BigInt` 表示无界整数，因此必须指定区间（例如 `rand(big.(1:6))`）。

此外，正态分布和指数分布已为某些 `AbstractFloat` 和 `Complex` 类型实现，详情请参见 [`randn`](@ref) 和 [`randexp`](@ref)。

要从其他分布生成随机数，请参见 [Distributions.jl](https://juliastats.org/Distributions.jl/stable/) 包。

!!! warning
    因为随机数生成的精确方式被视为实现细节，因此在版本更改后，错误修复和速度改进可能会改变生成的数字流。因此，在单元测试期间依赖特定的种子或生成的数字流是不鼓励的 - 考虑测试相关方法的属性。


## Random numbers module

```@docs
Random.Random
```

## Random generation functions

```@docs
Random.rand
Random.rand!
Random.bitrand
Random.randn
Random.randn!
Random.randexp
Random.randexp!
Random.randstring
```

## Subsequences, permutations and shuffling

```@docs
Random.randsubseq
Random.randsubseq!
Random.randperm
Random.randperm!
Random.randcycle
Random.randcycle!
Random.shuffle
Random.shuffle!
```

## Generators (creation and seeding)

```@docs
Random.default_rng
Random.seed!
Random.AbstractRNG
Random.TaskLocalRNG
Random.Xoshiro
Random.MersenneTwister
Random.RandomDevice
```

## [Hooking into the `Random` API](@id rand-api-hook)

有两种主要正交的方式来扩展 `Random` 的功能：

1. 生成自定义类型的随机值
2. 创建新生成器

The API for 1) is quite functional, but is relatively recent so it may still have to evolve in subsequent releases of the `Random` module. For example, it's typically sufficient to implement one `rand` method in order to have all other usual methods work automatically.

The API for 2) is still rudimentary, and may require more work than strictly necessary from the implementor, in order to support usual types of generated values.

### Generating random values of custom types

生成某些分布的随机值可能涉及各种权衡。*预计算*值，例如用于离散分布的 [alias table](https://en.wikipedia.org/wiki/Alias_method)，或用于单变量分布的 [“squeezing” functions](https://en.wikipedia.org/wiki/Rejection_sampling)，可以显著加快采样速度。应该预计算多少信息可能取决于我们计划从分布中抽取的值的数量。此外，一些随机数生成器可能具有某些属性，各种算法可能希望利用这些属性。

`Random` 模块定义了一个可定制的框架，用于获取随机值，以解决这些问题。每次调用 `rand` 都会生成一个 *sampler*，可以根据上述权衡进行定制，通过向 `Sampler` 添加方法，后者可以根据随机数生成器、描述分布的对象以及重复次数的建议进行调度。目前，对于后者，使用 `Val{1}`（表示单个样本）和 `Val{Inf}`（表示任意数量），`Random.Repetition` 是两者的别名。

`Sampler` 返回的对象随后用于生成随机值。当为可以进行采样的值 `X` 实现随机生成接口时，实施者应定义该方法。

```julia
rand(rng, sampler)
```

对于由 `Sampler(rng, X, repetition)` 返回的特定 `sampler`。

采样器可以是实现 `rand(rng, sampler)` 的任意值，但对于大多数应用，以下预定义的采样器可能已足够：

1. `SamplerType{T}()` 可用于实现从类型 `T` 中抽样的采样器（例如 `rand(Int)`）。这是 `Sampler` 对 *类型* 返回的默认值。
2. `SamplerTrivial(self)` 是 `self` 的一个简单包装，可以通过 `[]` 访问。当不需要预先计算的信息时（例如 `rand(1:3)`），这是推荐的采样器，并且是 `Sampler` 为 *values* 返回的默认值。
3. `SamplerSimple(self, data)` 还包含额外的 `data` 字段，可以用来存储任意预先计算的值，这些值应该在 `Sampler` 的 *自定义方法* 中计算。

我们为每个例子提供了示例。我们在这里假设算法的选择与随机数生成器（RNG）是独立的，因此我们在签名中使用 `AbstractRNG`。

```@docs
Random.Sampler
Random.SamplerType
Random.SamplerTrivial
Random.SamplerSimple
```

将预计算与实际生成值分离是 API 的一部分，并且也对用户可用。举个例子，假设 `rand(rng, 1:20)` 必须在循环中反复调用：利用这种解耦的方式如下：

```julia
rng = Xoshiro()
sp = Random.Sampler(rng, 1:20) # or Random.Sampler(Xoshiro, 1:20)
for x in X
    n = rand(rng, sp) # similar to n = rand(rng, 1:20)
    # use n
end
```

这是在标准库中也使用的机制，例如在随机数组生成的默认实现中（如 `rand(1:20, 10)`）。

#### Generating values from a type

给定一个类型 `T`，目前假设如果定义了 `rand(T)`，将会生成一个类型为 `T` 的对象。`SamplerType` 是 *类型的默认采样器*。为了定义类型 `T` 的随机值生成，应该定义 `rand(rng::AbstractRNG, ::Random.SamplerType{T})` 方法，并且该方法应该返回 `rand(rng, T)` 预期返回的值。

让我们以以下示例为例：我们实现一个 `Die` 类型，具有可变数量 `n` 的面，编号从 `1` 到 `n`。我们希望 `rand(Die)` 生成一个具有随机数量的最多 20 面（至少 4 面）的 `Die`：

```jldoctest Die
struct Die
    nsides::Int # number of sides
end

Random.rand(rng::AbstractRNG, ::Random.SamplerType{Die}) = Die(rand(rng, 4:20))

# output

```

`Die` 的标量和数组方法现在按预期工作：

```jldoctest Die; setup = :(Random.seed!(1))
julia> rand(Die)
Die(5)

julia> rand(Xoshiro(0), Die)
Die(10)

julia> rand(Die, 3)
3-element Vector{Die}:
 Die(9)
 Die(15)
 Die(14)

julia> a = Vector{Die}(undef, 3); rand!(a)
3-element Vector{Die}:
 Die(19)
 Die(7)
 Die(17)
```

#### A simple sampler without pre-computed data

在这里，我们为一个集合定义了一个采样器。如果不需要预先计算的数据，可以使用 `SamplerTrivial` 采样器来实现，它实际上是*值的默认回退*。

为了定义从类型 `S` 的对象中进行随机生成，应该定义以下方法：`rand(rng::AbstractRNG, sp::Random.SamplerTrivial{S})`。在这里，`sp` 只是包装了一个类型为 `S` 的对象，可以通过 `sp[]` 访问。继续以 `Die` 为例，我们现在想要定义 `rand(d::Die)` 以生成一个对应于 `d` 的某一面的 `Int`：

```jldoctest Die; setup = :(Random.seed!(1))
julia> Random.rand(rng::AbstractRNG, d::Random.SamplerTrivial{Die}) = rand(rng, 1:d[].nsides);

julia> rand(Die(4))
1

julia> rand(Die(4), 3)
3-element Vector{Any}:
 2
 3
 3
```

给定一个集合类型 `S`，目前假设如果定义了 `rand(::S)`，将会生成一个类型为 `eltype(S)` 的对象。在最后一个例子中，生成了一个 `Vector{Any}`；原因是 `eltype(Die) == Any`。解决方法是定义 `Base.eltype(::Type{Die}) = Int`。

#### Generating values for an `AbstractFloat` type

`AbstractFloat` 类型是特殊处理的，因为默认情况下，随机值并不是在整个类型域中生成，而是生成在 `[0,1)` 范围内。以下方法应为 `T <: AbstractFloat` 实现：`Random.rand(::AbstractRNG, ::Random.SamplerTrivial{Random.CloseOpen01{T}})`

#### An optimized sampler with pre-computed data

考虑一个离散分布，其中数字 `1:n` 以给定的概率抽取，这些概率的总和为一。当需要从该分布中获取许多值时，最快的方法是使用 [alias table](https://en.wikipedia.org/wiki/Alias_method)。我们在这里不提供构建此类表格的算法，但假设它在 `make_alias_table(probabilities)` 中可用，而 `draw_number(rng, alias_table)` 可用于从中抽取随机数。

假设该分布由以下内容描述：

```julia
struct DiscreteDistribution{V <: AbstractVector}
    probabilities::V
end
```

并且我们*始终*希望构建一个别名表，无论需要多少个值（我们将在下面学习如何自定义这一点）。这些方法

```julia
Random.eltype(::Type{<:DiscreteDistribution}) = Int

function Random.Sampler(::Type{<:AbstractRNG}, distribution::DiscreteDistribution, ::Repetition)
    SamplerSimple(distribution, make_alias_table(distribution.probabilities))
end
```

应该定义为返回一个带有预计算数据的采样器，然后

```julia
function rand(rng::AbstractRNG, sp::SamplerSimple{<:DiscreteDistribution})
    draw_number(rng, sp.data)
end
```

将用于绘制值。

#### Custom sampler types

`SamplerSimple` 类型对于大多数使用预计算数据的用例来说是足够的。然而，为了演示如何使用自定义采样器类型，这里我们实现了一些类似于 `SamplerSimple` 的东西。

回到我们的 `Die` 示例：`rand(::Die)` 使用范围内的随机生成，因此有机会进行此优化。我们将我们的自定义采样器称为 `SamplerDie`。

```julia
import Random: Sampler, rand

struct SamplerDie <: Sampler{Int} # generates values of type Int
    die::Die
    sp::Sampler{Int} # this is an abstract type, so this could be improved
end

Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerDie(die, Sampler(RNG, 1:die.nsides, r))
# the `r` parameter will be explained later on

rand(rng::AbstractRNG, sp::SamplerDie) = rand(rng, sp.sp)
```

现在可以使用 `sp = Sampler(rng, die)` 获取一个采样器，并在任何涉及 `rng` 的 `rand` 调用中使用 `sp` 代替 `die`。在上面的简单示例中，`die` 不需要存储在 `SamplerDie` 中，但在实际中通常是这样的情况。

当然，这种模式非常常见，以至于上面使用的辅助类型 `Random.SamplerSimple` 可用，这样我们就省去了定义 `SamplerDie` 的步骤：我们可以用以下方式实现我们的解耦：

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, r::Random.Repetition) =
    SamplerSimple(die, Sampler(RNG, 1:die.nsides, r))

rand(rng::AbstractRNG, sp::SamplerSimple{Die}) = rand(rng, sp.data)
```

在这里，`sp.data` 指的是调用 `SamplerSimple` 构造函数时的第二个参数（在这种情况下等于 `Sampler(rng, 1:die.nsides, r)`），而 `Die` 对象可以通过 `sp[]` 访问。

像 `SamplerDie` 一样，任何自定义采样器必须是 `Sampler{T}` 的子类型，其中 `T` 是生成值的类型。请注意，`SamplerSimple(x, data) isa Sampler{eltype(x)}`，因此这限制了 `SamplerSimple` 的第一个参数可以是什么（建议像在 `Die` 示例中那样使用 `SamplerSimple`，其中 `x` 在定义 `Sampler` 方法时被简单地转发）。同样，`SamplerTrivial(x) isa Sampler{eltype(x)}`。

另一个帮助器类型目前可用于其他情况，`Random.SamplerTag`，但被视为内部 API，可能会在没有适当弃用的情况下随时中断。

#### Using distinct algorithms for scalar or array generation

在某些情况下，是否希望生成少量值或大量值将影响算法的选择。这通过 `Sampler` 构造函数的第三个参数来处理。假设我们定义了两个 `Die` 的辅助类型，分别是 `SamplerDie1`，用于生成少量随机值，以及 `SamplerDieMany`，用于生成大量值。我们可以如下使用这些类型：

```julia
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{1}) = SamplerDie1(...)
Sampler(RNG::Type{<:AbstractRNG}, die::Die, ::Val{Inf}) = SamplerDieMany(...)
```

当然，`rand` 也必须在这些类型上定义（即 `rand(::AbstractRNG, ::SamplerDie1)` 和 `rand(::AbstractRNG, ::SamplerDieMany)`）。请注意，通常情况下，如果不需要自定义类型，可以使用 `SamplerTrivial` 和 `SamplerSimple`。

注意：`Sampler(rng, x)` 只是 `Sampler(rng, x, Val(Inf))` 的简写，而 `Random.Repetition` 是 `Union{Val{1}, Val{Inf}}` 的别名。

### Creating new generators

API 尚未明确定义，但作为经验法则：

1. 任何产生“基本”类型（`isbitstype` 整数和浮点类型在 `Base` 中）的 `rand` 方法都应该为这个特定的随机数生成器定义，如果它们是需要的；
2. 其他文档中记录的 `rand` 方法接受 `AbstractRNG` 应该可以开箱即用（前提是依赖的 1) 中的方法已实现），但当然可以针对这个 RNG 进行特化，如果有优化的空间；
3. `copy` 对于伪随机数生成器应返回一个独立的副本，该副本在以相同方式调用时从该点开始生成与原始生成的完全相同的随机序列。当这不可行时（例如，基于硬件的随机数生成器），`copy` 不得实现。

关于 1)，`rand` 方法可能会自动工作，但它并没有正式支持，并且在后续版本中可能会在没有警告的情况下中断。

要为假设的 `MyRNG` 生成器定义一个新的 `rand` 方法，以及一个值规范 `s`（例如 `s == Int`，或 `s == 1:10`），类型为 `S==typeof(s)` 或 `S==Type{s}` 如果 `s` 是一个类型，则必须定义与之前看到的相同的两个方法：

1. `Sampler(::Type{MyRNG}, ::S, ::Repetition)`，返回一个类型为 `SamplerS` 的对象。
2. `rand(rng::MyRNG, sp::SamplerS)`

可能会发生 `Sampler(rng::AbstractRNG, ::S, ::Repetition)` 已经在 `Random` 模块中定义。在这种情况下，如果想要针对这个特定的 RNG 类型专门化生成，可以在实践中跳过第 1 步，但相应的 `SamplerS` 类型被视为内部细节，可能会在没有警告的情况下更改。

#### Specializing array generation

在某些情况下，对于给定的随机数生成器类型，生成随机值数组使用专门的方法可能比仅仅使用之前解释的解耦技术更有效。例如，`MersenneTwister` 就是这种情况，它本地将随机值写入数组。

要为 `MyRNG` 实现此特化，并为规范 `s` 生成类型为 `S` 的元素，可以定义以下方法：`rand!(rng::MyRNG, a::AbstractArray{S}, ::SamplerS)`，其中 `SamplerS` 是由 `Sampler(MyRNG, s, Val(Inf))` 返回的采样器的类型。可以仅为子类型实现该功能，例如 `Array{S}`，而不是 `AbstractArray`。`rand` 的非变异数组方法将自动在内部调用此特化。

```@meta
DocTestSetup = nothing
```

# Reproducibility

通过使用用给定种子初始化的RNG参数，您可以在多次运行程序时重现相同的伪随机数序列。然而，Julia的一个小版本更新（例如从1.3到1.4）*可能会改变*从特定种子生成的伪随机数序列，特别是如果使用`MersenneTwister`。 （即使低级函数如[`rand`](@ref)生成的序列没有变化，高级函数如[`randsubseq`](@ref)的输出可能会因算法更新而变化。）理由：保证伪随机流永不改变会阻止许多算法改进。

如果您需要保证随机数据的精确可重现性，建议您简单地 *保存数据*（例如，作为科学出版物中的补充附件）。 （当然，您也可以指定特定的 Julia 版本和包清单，特别是如果您需要位级可重现性。）

依赖于*特定*“随机”数据的软件测试通常也应该保存数据，将其嵌入到测试代码中，或使用第三方包，如 [StableRNGs.jl](https://github.com/JuliaRandom/StableRNGs.jl)。另一方面，应该对*大多数*随机数据通过的测试（例如，测试 `A \ (A*x) ≈ x` 对于随机矩阵 `A = randn(n,n)`）可以使用具有固定种子的随机数生成器，以确保简单地多次运行测试不会由于非常不可能的数据（例如，极度病态的矩阵）而遇到失败。

从中抽取随机样本的统计*分布*在任何小版本的Julia发布中*是*保证相同的。
