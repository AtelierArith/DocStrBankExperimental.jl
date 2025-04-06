```
@assert cond [text]
```

如果 `cond` 为 `false`，则抛出一个 [`AssertionError`](@ref)。这是编写断言的首选语法，断言是被假定为真的条件，但用户可能会决定检查它们，以帮助调试如果它们失败。可选消息 `text` 在断言失败时显示。

!!! warning
    在某些优化级别下，断言可能会被禁用。因此，断言应仅作为调试工具使用，而不应用于身份验证验证（例如，验证密码或检查数组边界）。代码不得依赖于运行 `cond` 的副作用来确保函数的正确行为。


# 示例

```jldoctest
julia> @assert iseven(3) "3 is an odd number!"
ERROR: AssertionError: 3 is an odd number!

julia> @assert isodd(3) "What even are numbers?"
```
