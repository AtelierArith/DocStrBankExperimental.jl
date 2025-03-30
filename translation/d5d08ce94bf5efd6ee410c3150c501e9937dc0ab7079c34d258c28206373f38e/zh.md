```
iszero(x)
```

如果 `x == zero(x)`，则返回 `true`；如果 `x` 是一个数组，则检查 `x` 的所有元素是否为零。

另请参见: [`isone`](@ref), [`isinteger`](@ref), [`isfinite`](@ref), [`isnan`](@ref).

# 示例

```jldoctest
julia> iszero(0.0)
true

julia> iszero([1, 9, 0])
false

julia> iszero([false, 0, 0])
true
```
