```
//(num, den)
```

将两个整数或有理数相除，返回一个 [`Rational`](@ref) 结果。更一般地，`//` 可以用于其他数值类型的精确有理除法，这些数值类型具有整数或有理成分，例如具有整数成分的复数。

请注意，`//` 不允许使用浮点数（[`AbstractFloat`](@ref)）作为参数（即使这些值是有理数）。参数必须是 [`Integer`](@ref)、`Rational` 或其复合类型的子类型。

# 示例

```jldoctest
julia> 3 // 5
3//5

julia> (3 // 5) // (2 // 1)
3//10

julia> (1+2im) // (3+4im)
11//25 + 2//25*im

julia> 1.0 // 2
ERROR: MethodError: no method matching //(::Float64, ::Int64)
[...]
```
