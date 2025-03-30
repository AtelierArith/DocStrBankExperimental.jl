```
cmp(a::AbstractString, b::AbstractString) -> Int
```

比较两个字符串。如果两个字符串的长度相同且每个索引处的字符相同，则返回 `0`。如果 `a` 是 `b` 的前缀，或者 `a` 在字母顺序上排在 `b` 之前，则返回 `-1`。如果 `b` 是 `a` 的前缀，或者 `b` 在字母顺序上排在 `a` 之前（从技术上讲，是按 Unicode 代码点的字典顺序），则返回 `1`。

# 示例

```jldoctest
julia> cmp("abc", "abc")
0

julia> cmp("ab", "abc")
-1

julia> cmp("abc", "ab")
1

julia> cmp("ab", "ac")
-1

julia> cmp("ac", "ab")
1

julia> cmp("α", "a")
1

julia> cmp("b", "β")
-1
```
