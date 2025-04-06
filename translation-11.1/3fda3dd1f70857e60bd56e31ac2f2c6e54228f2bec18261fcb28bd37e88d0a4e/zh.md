```
Val(c)
```

返回 `Val{c}()`，其中不包含运行时数据。像这样的类型可以用来通过值 `c` 在函数之间传递信息，`c` 必须是一个 `isbits` 值或一个 `Symbol`。这个构造的意图是能够直接在常量上进行调度（在编译时），而不必在运行时测试常量的值。

# 示例

```jldoctest
julia> f(::Val{true}) = "Good"
f (generic function with 1 method)

julia> f(::Val{false}) = "Bad"
f (generic function with 2 methods)

julia> f(Val(true))
"Good"
```
