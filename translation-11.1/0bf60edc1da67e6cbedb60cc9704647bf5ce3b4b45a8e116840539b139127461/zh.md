```
signbit(x)
```

如果 `x` 的符号值为负，则返回 `true`，否则返回 `false`。

另请参见 [`sign`](@ref) 和 [`copysign`](@ref)。

# 示例

```jldoctest
julia> signbit(-4)
true

julia> signbit(5)
false

julia> signbit(5.5)
false

julia> signbit(-4.1)
true
```
