```
Symbol(x...) -> Symbol
```

通过将参数的字符串表示连接在一起来创建一个 [`Symbol`](@ref)。

# 示例

```jldoctest
julia> Symbol("my", "name")
:myname

julia> Symbol("day", 4)
:day4
```
