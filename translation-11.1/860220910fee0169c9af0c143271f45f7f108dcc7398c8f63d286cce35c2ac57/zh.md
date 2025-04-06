```
expm1(x)
```

准确计算 $e^x-1$。它避免了在直接计算 exp(x)-1 时对于小值 x 的精度损失。

# 示例

```jldoctest
julia> expm1(1e-16)
1.0e-16

julia> exp(1e-16) - 1
0.0
```
