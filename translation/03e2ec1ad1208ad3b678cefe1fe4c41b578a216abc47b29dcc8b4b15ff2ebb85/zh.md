```
!==(x, y)
≢(x,y)
```

总是给出与 [`===`](@ref) 相反的答案。

# 示例

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a ≢ b
true

julia> a ≢ a
false
```
