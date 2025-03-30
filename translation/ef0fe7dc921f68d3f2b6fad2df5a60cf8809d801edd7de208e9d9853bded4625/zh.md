```
keys(m::RegexMatch) -> Vector
```

返回一个包含所有底层正则表达式捕获组的键的向量。即使捕获组未能匹配，键也会被包含在内。也就是说，即使 `m[idx] == nothing`，`idx` 也会在返回值中。

未命名的捕获组将具有对应于其索引的整数键。命名的捕获组将具有字符串键。

!!! compat "Julia 1.7"
    此方法是在 Julia 1.7 中添加的


# 示例

```jldoctest
julia> keys(match(r"(?<hour>\d+):(?<minute>\d+)(am|pm)?", "11:30"))
3-element Vector{Any}:
  "hour"
  "minute"
 3
```
