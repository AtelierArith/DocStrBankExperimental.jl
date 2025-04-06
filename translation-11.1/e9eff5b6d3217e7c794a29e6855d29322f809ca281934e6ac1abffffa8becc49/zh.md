```
@nref N A indexexpr
```

生成类似 `A[i_1, i_2, ...]` 的表达式。`indexexpr` 可以是一个迭代符号前缀，或者是一个匿名函数表达式。

# 示例

```jldoctest
julia> @macroexpand Base.Cartesian.@nref 3 A i
:(A[i_1, i_2, i_3])
```
