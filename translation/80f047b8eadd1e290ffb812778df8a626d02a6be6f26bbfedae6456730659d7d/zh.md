```
AssertionError([msg])
```

断言条件未评估为 `true`。可选参数 `msg` 是一个描述性错误字符串。

# 示例

```jldoctest
julia> @assert false "this is not true"
ERROR: AssertionError: this is not true
```

`AssertionError` 通常是从 [`@assert`](@ref) 抛出的。 ```
