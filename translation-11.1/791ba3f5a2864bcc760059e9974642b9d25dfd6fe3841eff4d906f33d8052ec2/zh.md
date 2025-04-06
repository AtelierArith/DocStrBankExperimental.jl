```
findfirst(pattern::AbstractString, string::AbstractString)
findfirst(pattern::AbstractPattern, string::String)
```

在 `string` 中查找 `pattern` 的第一次出现。等同于 [`findnext(pattern, string, firstindex(s))`](@ref)。

# 示例

```jldoctest
julia> findfirst("z", "Hello to the world") # 返回无，但在 REPL 中不打印

julia> findfirst("Julia", "JuliaLang")
1:5
```
