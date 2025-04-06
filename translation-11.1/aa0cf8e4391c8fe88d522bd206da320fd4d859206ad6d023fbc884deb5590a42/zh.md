```
parse(str, start; greedy=true, raise=true, depwarn=true, filename="none")
```

解析表达式字符串并返回一个表达式（该表达式可以稍后传递给 eval 进行执行）。`start` 是 `str` 中第一个要开始解析的字符的代码单元索引（与所有字符串索引一样，这些不是字符索引）。如果 `greedy` 为 `true`（默认值），`parse` 将尽量消耗尽可能多的输入；否则，它将在解析出有效表达式后立即停止。未完成但在语法上有效的表达式将返回 `Expr(:incomplete, "(错误信息)")`。如果 `raise` 为 `true`（默认值），除未完成表达式外的语法错误将引发错误。如果 `raise` 为 `false`，`parse` 将返回一个在评估时会引发错误的表达式。如果 `depwarn` 为 `false`，将抑制弃用警告。`filename` 参数用于在引发错误时显示诊断信息。

```jldoctest
julia> Meta.parse("(α, β) = 3, 5", 1) # start of string
(:((α, β) = (3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 1, greedy=false)
(:((α, β)), 9)

julia> Meta.parse("(α, β) = 3, 5", 16) # end of string
(nothing, 16)

julia> Meta.parse("(α, β) = 3, 5", 11) # index of 3
(:((3, 5)), 16)

julia> Meta.parse("(α, β) = 3, 5", 11, greedy=false)
(3, 13)
```
