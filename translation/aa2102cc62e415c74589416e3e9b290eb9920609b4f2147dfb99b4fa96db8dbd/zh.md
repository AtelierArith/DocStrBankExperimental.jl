```
findlast(pattern::AbstractString, string::AbstractString)
```

查找 `string` 中 `pattern` 的最后一个出现位置。等价于 [`findprev(pattern, string, lastindex(string))`](@ref)。

# 示例

```jldoctest
julia> findlast("o", "Hello to the world")
15:15

julia> findfirst("Julia", "JuliaLang")
1:5
```
