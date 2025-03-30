```
rand([rng=default_rng()], [S], [dims...])
```

从由 `S` 指定的值集合中选择一个随机元素或随机元素数组；`S` 可以是

  * 可索引的集合（例如 `1:9` 或 `('x', "y", :z)`)
  * `AbstractDict` 或 `AbstractSet` 对象
  * 字符串（视为字符集合），或
  * 来自下面列表的类型，对应于指定的值集合

      * 具体整数类型从 `typemin(S):typemax(S)` 取样（不包括 [`BigInt`](@ref) 不支持）
      * 具体浮点类型从 `[0, 1)` 取样
      * 具体复数类型 `Complex{T}` 如果 `T` 是可取样类型，则独立从对应于 `T` 的值集合中取其实部和虚部，但如果 `T` 不是可取样的，则不支持。
      * 所有 `<:AbstractChar` 类型从有效的 Unicode 标量集合中取样
      * 用户定义的类型和值集合；有关实现指导，请参见 [Hooking into the `Random` API](@ref rand-api-hook)
      * 已知大小的元组类型，并且 `S` 的每个参数本身都是可取样类型；返回类型为 `S` 的值。请注意，像 `Tuple{Vararg{T}}`（未知大小）和 `Tuple{1:2}`（用值参数化）这样的元组类型不受支持
      * `Pair` 类型，例如 `Pair{X, Y}`，使得 `rand` 对 `X` 和 `Y` 定义，在这种情况下生成随机对。

`S` 默认为 [`Float64`](@ref)。当除了可选的 `rng` 之外只传递一个参数并且是 `Tuple` 时，它被解释为值集合（`S`），而不是 `dims`。

另请参见 [`randn`](@ref) 以获取正态分布的数字，以及 [`rand!`](@ref) 和 [`randn!`](@ref) 以获取就地等效项。

!!! compat "Julia 1.1"
    将 `S` 作为元组的支持至少需要 Julia 1.1。


!!! compat "Julia 1.11"
    将 `S` 作为 `Tuple` 类型的支持至少需要 Julia 1.11。


# 示例

```julia-repl
julia> rand(Int, 2)
2-element Array{Int64,1}:
 1339893410598768192
 1575814717733606317

julia> using Random

julia> rand(Xoshiro(0), Dict(1=>2, 3=>4))
3 => 4

julia> rand((2, 3))
3

julia> rand(Float64, (2, 3))
2×3 Array{Float64,2}:
 0.999717  0.0143835  0.540787
 0.696556  0.783855   0.938235
```

!!! note
    `rand(rng, s::Union{AbstractDict,AbstractSet})` 的复杂度与 `s` 的长度成线性关系，除非有可用的常数复杂度的优化方法，这种情况适用于 `Dict`、`Set` 和稠密的 `BitSet`。对于多次调用，请使用 `rand(rng, collect(s))`，或者根据需要使用 `rand(rng, Dict(s))` 或 `rand(rng, Set(s))`。

