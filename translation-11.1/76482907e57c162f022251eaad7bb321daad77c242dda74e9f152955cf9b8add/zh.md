```
sort!(v; alg::Algorithm=defalg(v), lt=isless, by=identity, rev::Bool=false, order::Ordering=Forward)
```

就地对向量 `v` 进行排序。默认使用稳定算法：相等元素的顺序得以保留。可以通过 `alg` 关键字选择特定算法（有关可用算法，请参见 [排序算法](@ref)）。

元素首先通过函数 `by` 进行转换，然后根据函数 `lt` 或排序 `order` 进行比较。最后，如果 `rev=true`，则结果顺序会被反转（这保留了前向稳定性：相等的元素不会被反转）。当前实现是在每次比较之前应用 `by` 转换，而不是每个元素一次。

传递一个与 `isless` 不同的 `lt` 以及一个与 [`Base.Order.Forward`](@ref) 或 [`Base.Order.Reverse`](@ref) 不同的 `order` 是不允许的，否则所有选项都是独立的，可以在所有可能的组合中一起使用。请注意，`order` 也可以包含一个 "by" 转换，在这种情况下，它在 `by` 关键字定义的转换之后应用。有关 `order` 值的更多信息，请参见 [替代排序](@ref) 的文档。

两个元素之间的关系定义如下（当 `rev=true` 时，“小于”和“大于”互换）：

  * 如果 `lt(by(x), by(y))`（或 `Base.Order.lt(order, by(x), by(y))`）为真，则 `x` 小于 `y`。
  * 如果 `y` 小于 `x`，则 `x` 大于 `y`。
  * 如果两者都不小于对方，则 `x` 和 `y` 是等价的（“不可比较”有时用作“等价”的同义词）。

`sort!` 的结果是排序的，意味着每个元素都大于或等于前一个元素。

`lt` 函数必须定义严格的弱序，即它必须是

  * 非自反的：`lt(x, x)` 始终返回 `false`，
  * 不对称的：如果 `lt(x, y)` 返回 `true`，则 `lt(y, x)` 返回 `false`，
  * 传递的：`lt(x, y) && lt(y, z)` 意味着 `lt(x, z)`，
  * 在等价中是传递的：`!lt(x, y) && !lt(y, x)` 和 `!lt(y, z) && !lt(z, y)` 一起意味着 `!lt(x, z) && !lt(z, x)`。换句话说：如果 `x` 和 `y` 是等价的，并且 `y` 和 `z` 是等价的，则 `x` 和 `z` 必须是等价的。

例如，`<` 是 `Int` 值的有效 `lt` 函数，但 `≤` 不是：它违反了非自反性。对于 `Float64` 值，即使 `<` 也是无效的，因为它违反了第四个条件：`1.0` 和 `NaN` 是等价的，`NaN` 和 `2.0` 也是等价的，但 `1.0` 和 `2.0` 不是等价的。

另请参见 [`sort`](@ref)、[`sortperm`](@ref)、[`sortslices`](@ref)、[`partialsort!`](@ref)、[`partialsortperm`](@ref)、[`issorted`](@ref)、[`searchsorted`](@ref)、[`insorted`](@ref)、[`Base.Order.ord`](@ref)。

# 示例

```jldoctest
julia> v = [3, 1, 2]; sort!(v); v
3-element Vector{Int64}:
 1
 2
 3

julia> v = [3, 1, 2]; sort!(v, rev = true); v
3-element Vector{Int64}:
 3
 2
 1

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[1]); v
3-element Vector{Tuple{Int64, String}}:
 (1, "c")
 (2, "b")
 (3, "a")

julia> v = [(1, "c"), (3, "a"), (2, "b")]; sort!(v, by = x -> x[2]); v
3-element Vector{Tuple{Int64, String}}:
 (3, "a")
 (2, "b")
 (1, "c")

julia> sort(0:3, by=x->x-2, order=Base.Order.By(abs)) # same as sort(0:3, by=abs(x->x-2))
4-element Vector{Int64}:
 2
 1
 3
 0

julia> sort([2, NaN, 1, NaN, 3]) # correct sort with default lt=isless
5-element Vector{Float64}:
   1.0
   2.0
   3.0
 NaN
 NaN

julia> sort([2, NaN, 1, NaN, 3], lt=<) # wrong sort due to invalid lt. This behavior is undefined.
5-element Vector{Float64}:
   2.0
 NaN
   1.0
 NaN
   3.0
```
