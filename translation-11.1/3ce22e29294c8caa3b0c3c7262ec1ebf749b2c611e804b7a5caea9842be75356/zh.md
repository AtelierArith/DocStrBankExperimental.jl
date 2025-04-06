```
findnext(pattern::AbstractString, string::AbstractString, start::Integer)
findnext(pattern::AbstractPattern, string::String, start::Integer)
```

在位置 `start` 开始查找 `string` 中 `pattern` 的下一个出现。`pattern` 可以是一个字符串，或者一个正则表达式，在这种情况下 `string` 必须是 `String` 类型。

返回值是一个索引范围，其中找到匹配序列，使得 `s[findnext(x, s, i)] == x`：

`findnext("substring", string, i)` == `start:stop`，使得 `string[start:stop] == "substring"` 且 `i <= start`，如果没有匹配则返回 `nothing`。

# 示例

```jldoctest
julia> findnext("z", "Hello to the world", 1) === nothing
true

julia> findnext("o", "Hello to the world", 6)
8:8

julia> findnext("Lang", "JuliaLang", 2)
6:9
```
