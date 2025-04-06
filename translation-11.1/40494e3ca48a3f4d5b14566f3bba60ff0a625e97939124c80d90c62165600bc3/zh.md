```
occursin(haystack)
```

创建一个函数，检查其参数是否出现在 `haystack` 中，即一个等效于 `needle -> occursin(needle, haystack)` 的函数。

返回的函数类型为 `Base.Fix2{typeof(occursin)}`。

!!! compat "Julia 1.6"
    此方法需要 Julia 1.6 或更高版本。


# 示例

```jldoctest
julia> search_f = occursin("JuliaLang is a programming language");

julia> search_f("JuliaLang")
true

julia> search_f("Python")
false
```
