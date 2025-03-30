```
fill(value, dims::Tuple)
fill(value, dims...)
```

创建一个大小为 `dims` 的数组，所有位置都设置为 `value`。

例如，`fill(1.0, (5,5))` 返回一个 5×5 的浮点数组，数组的每个位置都为 `1.0`。

维度长度 `dims` 可以指定为元组或参数序列。一个 `N` 长度的元组或跟在 `value` 后面的 `N` 个参数指定一个 `N` 维数组。因此，创建一个零维数组并将其唯一位置设置为 `x` 的常见习惯用法是 `fill(x)`。

返回数组的每个位置都设置为（因此是 [`===`](@ref)）传入的 `value`；这意味着如果 `value` 本身被修改，所有填充的数组元素都会反映该修改，因为它们*仍然*是那个 `value`。对于 `fill(1.0, (5,5))` 来说，这没有问题，因为 `value` `1.0` 是不可变的，无法被修改，但对于可变值（如最常见的数组）来说，这可能会出乎意料。例如，`fill([], 3)` 将*同一个*空数组放在返回向量的所有三个位置：

```jldoctest
julia> v = fill([], 3)
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v[1] === v[2] === v[3]
true

julia> value = v[1]
Any[]

julia> push!(value, 867_5309)
1-element Vector{Any}:
 8675309

julia> v
3-element Vector{Vector{Any}}:
 [8675309]
 [8675309]
 [8675309]
```

要创建多个独立的内部数组，请使用 [comprehension](@ref man-comprehensions)。这会在循环的每次迭代中创建一个新的独立数组：

```jldoctest
julia> v2 = [[] for _ in 1:3]
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v2[1] === v2[2] === v2[3]
false

julia> push!(v2[1], 8675309)
1-element Vector{Any}:
 8675309

julia> v2
3-element Vector{Vector{Any}}:
 [8675309]
 []
 []
```

另请参见: [`fill!`](@ref), [`zeros`](@ref), [`ones`](@ref), [`similar`](@ref).

# 示例

```jldoctest
julia> fill(1.0, (2,3))
2×3 Matrix{Float64}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> fill(42)
0-dimensional Array{Int64, 0}:
42

julia> A = fill(zeros(2), 2) # 将两个元素设置为相同的 [0.0, 0.0] 向量
2-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [0.0, 0.0]

julia> A[1][1] = 42; # 将填充的值修改为 [42.0, 0.0]

julia> A # A[1] 和 A[2] 是同一个向量
2-element Vector{Vector{Float64}}:
 [42.0, 0.0]
 [42.0, 0.0]
```
