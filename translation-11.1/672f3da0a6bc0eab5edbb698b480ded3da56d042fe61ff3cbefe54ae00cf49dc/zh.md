```
reverseind(v, i)
```

给定索引 `i` 在 [`reverse(v)`](@ref) 中，返回 `v` 中对应的索引，以便满足 `v[reverseind(v,i)] == reverse(v)[i]`。 （在 `v` 包含非 ASCII 字符的情况下，这可能并不简单。）

# 示例

```jldoctest
julia> s = "Julia🚀"
"Julia🚀"

julia> r = reverse(s)
"🚀ailuJ"

julia> for i in eachindex(s)
           print(r[reverseind(r, i)])
       end
Julia🚀
```
