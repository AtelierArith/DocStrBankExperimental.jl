```
findnext(ch::AbstractChar, string::AbstractString, start::Integer)
```

在字符串 `string` 中从位置 `start` 开始查找字符 `ch` 的下一个出现位置。

!!! compat "Julia 1.3"
    此方法至少需要 Julia 1.3。


# 示例

```jldoctest
julia> findnext('z', "Hello to the world", 1) === nothing
true

julia> findnext('o', "Hello to the world", 6)
8
```
