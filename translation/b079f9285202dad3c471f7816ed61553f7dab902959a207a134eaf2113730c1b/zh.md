```
contains(haystack::AbstractString, needle)
```

如果 `haystack` 包含 `needle`，则返回 `true`。这与 `occursin(needle, haystack)` 相同，但为了与 `startswith(haystack, needle)` 和 `endswith(haystack, needle)` 一致而提供。

另请参见 [`occursin`](@ref), [`in`](@ref), [`issubset`](@ref)。

# 示例

```jldoctest
julia> contains("JuliaLang is pretty cool!", "Julia")
true

julia> contains("JuliaLang is pretty cool!", 'a')
true

julia> contains("aba", r"a.a")
true

julia> contains("abba", r"a.a")
false
```

!!! compat "Julia 1.5"
    `contains` 函数需要至少 Julia 1.5。

