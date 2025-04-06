```
^(s::Union{AbstractString,AbstractChar}, n::Integer) -> AbstractString
```

将字符串或字符重复 `n` 次。这也可以写作 `repeat(s, n)`。

另见 [`repeat`](@ref)。

# 示例

```jldoctest
julia> "Test "^3
"Test Test Test "
```
