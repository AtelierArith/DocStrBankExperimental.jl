```
!=(x, y)
≠(x,y)
```

不等比较运算符。总是给出与 [`==`](@ref) 相反的答案。

# 实现

新类型通常不应实现此功能，而应依赖于后备定义 `!=(x,y) = !(x==y)`。

# 示例

```jldoctest
julia> 3 != 2
true

julia> "foo" ≠ "foo"
false
```
