```
broadcast(f, As...)
```

对数组、元组、集合、[`Ref`](@ref)和/或标量 `As` 进行函数 `f` 的广播。

广播将函数 `f` 应用到容器参数的元素和 `As` 中的标量本身。单例和缺失维度被扩展以匹配其他参数的范围，通过虚拟重复值来实现。默认情况下，仅考虑有限数量的类型作为标量，包括 `Number`、`String`、`Symbol`、`Type`、`Function` 以及一些常见的单例，如 [`missing`](@ref) 和 [`nothing`](@ref)。所有其他参数按元素进行迭代或索引。

结果容器类型由以下规则确定：

  * 如果所有参数都是标量或零维数组，则返回一个未包装的标量。
  * 如果至少一个参数是元组，且所有其他参数都是标量或零维数组，则返回一个元组。
  * 所有其他参数组合默认返回一个 `Array`，但自定义容器类型可以定义自己的实现和类似提升的规则，以在作为参数出现时自定义结果。

广播有一种特殊语法：`f.(args...)` 等价于 `broadcast(f, args...)`，嵌套的 `f.(g.(args...))` 调用被融合为一个单一的广播循环。

# 示例

```jldoctest
julia> A = [1, 2, 3, 4, 5]
5-element Vector{Int64}:
 1
 2
 3
 4
 5

julia> B = [1 2; 3 4; 5 6; 7 8; 9 10]
5×2 Matrix{Int64}:
 1   2
 3   4
 5   6
 7   8
 9  10

julia> broadcast(+, A, B)
5×2 Matrix{Int64}:
  2   3
  5   6
  8   9
 11  12
 14  15

julia> parse.(Int, ["1", "2"])
2-element Vector{Int64}:
 1
 2

julia> abs.((1, -2))
(1, 2)

julia> broadcast(+, 1.0, (0, -2.0))
(1.0, -1.0)

julia> (+).([[0,2], [1,3]], Ref{Vector{Int}}([1,-1]))
2-element Vector{Vector{Int64}}:
 [1, 1]
 [2, 2]

julia> string.(("one","two","three","four"), ": ", 1:4)
4-element Vector{String}:
 "one: 1"
 "two: 2"
 "three: 3"
 "four: 4"

```
