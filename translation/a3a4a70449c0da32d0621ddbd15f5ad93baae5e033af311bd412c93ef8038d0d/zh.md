```
angle(z)
```

计算复数 `z` 的相位角（以弧度为单位）。

返回一个数字 `-pi ≤ angle(z) ≤ pi`，因此在负实轴上是不连续的。

另见: [`atan`](@ref), [`cis`](@ref), [`rad2deg`](@ref).

# 示例

```jldoctest
julia> rad2deg(angle(1 + im))
45.0

julia> rad2deg(angle(1 - im))
-45.0

julia> rad2deg(angle(-1 + 1e-20im))
180.0

julia> rad2deg(angle(-1 - 1e-20im))
-180.0
```
