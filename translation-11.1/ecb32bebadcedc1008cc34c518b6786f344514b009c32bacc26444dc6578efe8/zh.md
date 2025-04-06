```
cmp(x,y)
```

根据 `x` 是否小于、等于或大于 `y` 返回 -1、0 或 1。使用 `isless` 实现的全序。

# 示例

```jldoctest
julia> cmp(1, 2)
-1

julia> cmp(2, 1)
1

julia> cmp(2+im, 3-im)
ERROR: MethodError: no method matching isless(::Complex{Int64}, ::Complex{Int64})
[...]
```
