```
@nexprs N expr
```

生成 `N` 个表达式。`expr` 应该是一个匿名函数表达式。

# 示例

```jldoctest
julia> @macroexpand Base.Cartesian.@nexprs 4 i -> y[i] = A[i+j]
quote
    y[1] = A[1 + j]
    y[2] = A[2 + j]
    y[3] = A[3 + j]
    y[4] = A[4 + j]
end
```
