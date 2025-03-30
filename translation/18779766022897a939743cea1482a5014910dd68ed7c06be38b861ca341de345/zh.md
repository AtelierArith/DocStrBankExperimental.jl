```
parse(str; raise=true, depwarn=true, filename="none")
```

贪婪地解析表达式字符串，返回一个单一的表达式。如果在第一个表达式之后还有额外的字符，将抛出错误。如果`raise`为`true`（默认），语法错误将引发错误；否则，`parse`将返回一个在评估时会引发错误的表达式。如果`depwarn`为`false`，则会抑制弃用警告。`filename`参数用于在引发错误时显示诊断信息。

```jldoctest; filter=r"(?<=Expr\(:error).*|(?<=Expr\(:incomplete).*"
julia> Meta.parse("x = 3")
:(x = 3)

julia> Meta.parse("1.0.2")
错误: ParseError:
# 错误 @ none:1:1
1.0.2
└──┘ ── 无效的数字常量
[...]

julia> Meta.parse("1.0.2"; raise = false)
:($(Expr(:error, "无效的数字常量 "1.0."")))

julia> Meta.parse("x = ")
:($(Expr(:incomplete, "不完整: 输入的提前结束")))
```
