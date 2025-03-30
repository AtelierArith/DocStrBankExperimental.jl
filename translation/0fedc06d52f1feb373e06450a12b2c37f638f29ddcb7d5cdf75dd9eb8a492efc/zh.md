```
isless(a::AbstractString, b::AbstractString) -> Bool
```

测试字符串 `a` 是否在字母顺序上（严格来说，是按 Unicode 代码点的字典顺序）排在字符串 `b` 之前。

# 示例

```jldoctest
julia> isless("a", "b")
true

julia> isless("β", "α")
false

julia> isless("a", "a")
false
```
