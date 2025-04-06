```
first(s::AbstractString, n::Integer)
```

获取由`s`的前`n`个字符组成的字符串。

# 示例

```jldoctest
julia> first("∀ϵ≠0: ϵ²>0", 0)
""

julia> first("∀ϵ≠0: ϵ²>0", 1)
"∀"

julia> first("∀ϵ≠0: ϵ²>0", 3)
"∀ϵ≠"
```
