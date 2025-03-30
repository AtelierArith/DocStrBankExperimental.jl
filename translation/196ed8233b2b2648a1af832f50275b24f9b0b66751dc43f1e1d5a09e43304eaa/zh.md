```
typejoin(T, S, ...)
```

返回类型 `T` 和 `S` 的最近公共祖先，即它们都继承的最窄类型。对额外的可变参数进行递归。

# 示例

```jldoctest
julia> typejoin(Int, Float64)
Real

julia> typejoin(Int, Float64, ComplexF32)
Number
```
