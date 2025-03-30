```
last(s::AbstractString, n::Integer)
```

获取由`s`的最后`n`个字符组成的字符串。

# 示例

```jldoctest
julia> last("∀ϵ≠0: ϵ²>0", 0)
""

julia> last("∀ϵ≠0: ϵ²>0", 1)
"0"

julia> last("∀ϵ≠0: ϵ²>0", 3)
"²>0"
```
