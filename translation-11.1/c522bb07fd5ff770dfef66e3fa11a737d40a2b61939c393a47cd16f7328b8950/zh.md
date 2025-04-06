```
one(x)
one(T::type)
```

返回 `x` 的乘法单位元：一个值，使得 `one(x)*x == x*one(x) == x`。或者 `one(T)` 可以接受一个类型 `T`，在这种情况下，`one` 返回任何类型为 `T` 的 `x` 的乘法单位元。

如果可能，`one(x)` 返回与 `x` 相同类型的值，而 `one(T)` 返回类型为 `T` 的值。然而，对于表示有维度量的类型（例如，天数的时间），这可能不成立，因为乘法单位元必须是无维的。在这种情况下，`one(x)` 应该返回与 `x` 相同精度（以及形状，对于矩阵）的单位值。

如果你想要一个与 `x` 相同类型的量，或者类型为 `T`，即使 `x` 是有维度的，请使用 [`oneunit`](@ref) 替代。

另请参见 [`identity`](@ref) 函数，以及 `I` 在 [`LinearAlgebra`](@ref man-linalg) 中的单位矩阵。

# 示例

```jldoctest
julia> one(3.7)
1.0

julia> one(Int)
1

julia> import Dates; one(Dates.Day(1))
1
```
