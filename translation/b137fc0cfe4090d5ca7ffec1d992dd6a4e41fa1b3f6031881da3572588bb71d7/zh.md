```
findprev(pattern::AbstractString, string::AbstractString, start::Integer)
```

在位置 `start` 开始的 `string` 中查找 `pattern` 的上一个出现。

返回值是一个索引范围，其中找到匹配序列，使得 `s[findprev(x, s, i)] == x`：

`findprev("substring", string, i)` == `start:stop`，使得 `string[start:stop] == "substring"` 且 `stop <= i`，如果没有匹配则返回 `nothing`。

# 示例

```jldoctest
julia> findprev("z", "Hello to the world", 18) === nothing
true

julia> findprev("o", "Hello to the world", 18)
15:15

julia> findprev("Julia", "JuliaLang", 6)
1:5
```
