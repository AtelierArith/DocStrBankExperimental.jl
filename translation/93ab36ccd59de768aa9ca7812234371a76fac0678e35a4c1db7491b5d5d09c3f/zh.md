```
isapprox(x, y; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps, nans::Bool=false[, norm::Function])
```

不精确的相等比较。如果两个数字的相对距离 *或* 绝对距离在容差范围内，则它们被认为相等：`isapprox` 在 `norm(x-y) <= max(atol, rtol*max(norm(x), norm(y)))` 时返回 `true`。默认的 `atol`（绝对容差）为零，默认的 `rtol`（相对容差）取决于 `x` 和 `y` 的类型。关键字参数 `nans` 决定是否将 NaN 值视为相等（默认为 false）。

对于实数或复数浮点值，如果未指定 `atol > 0`，则 `rtol` 默认为 `x` 或 `y` 类型的 [`eps`](@ref) 的平方根，以较大者为准（精度最低）。这对应于要求大约一半有效数字的相等。否则，例如对于整数参数或如果提供了 `atol > 0`，则 `rtol` 默认为零。

`norm` 关键字对于数值 `(x,y)` 默认为 `abs`，对于数组默认为 `LinearAlgebra.norm`（在某些情况下，替代的 `norm` 选择是有用的）。当 `x` 和 `y` 是数组时，如果 `norm(x-y)` 不是有限的（即 `±Inf` 或 `NaN`），则比较会回退到检查 `x` 和 `y` 的所有元素是否在分量上大致相等。

二元运算符 `≈` 等同于带有默认参数的 `isapprox`，而 `x ≉ y` 等同于 `!isapprox(x,y)`。

请注意，`x ≈ 0`（即，使用默认容差与零进行比较）等同于 `x == 0`，因为默认的 `atol` 为 `0`。在这种情况下，您应该提供适当的 `atol`（或使用 `norm(x) ≤ atol`）或重新安排您的代码（例如，使用 `x ≈ y` 而不是 `x - y ≈ 0`）。因为它依赖于您问题的整体缩放（“单位”），所以无法自动选择非零的 `atol`：例如，在 `x - y ≈ 0` 中，如果 `x` 是 [地球半径](https://en.wikipedia.org/wiki/Earth_radius) 的米数，则 `atol=1e-9` 是一个极小的容差，但如果 `x` 是 [氢原子半径](https://en.wikipedia.org/wiki/Bohr_radius) 的米数，则是一个极大的容差。

!!! compat "Julia 1.6"
    在比较数值（非数组）参数时传递 `norm` 关键字参数需要 Julia 1.6 或更高版本。


# 示例

```jldoctest
julia> isapprox(0.1, 0.15; atol=0.05)
true

julia> isapprox(0.1, 0.15; rtol=0.34)
true

julia> isapprox(0.1, 0.15; rtol=0.33)
false

julia> 0.1 + 1e-10 ≈ 0.1
true

julia> 1e-10 ≈ 0
false

julia> isapprox(1e-10, 0, atol=1e-8)
true

julia> isapprox([10.0^9, 1.0], [10.0^9, 2.0]) # using `norm`
true
```
