```
foldr(op, itr; [init])
```

类似于 [`reduce`](@ref)，但保证右结合性。如果提供，关键字参数 `init` 将仅使用一次。通常，在处理空集合时，需要提供 `init`。

# 示例

```jldoctest
julia> foldr(=>, 1:4)
1 => (2 => (3 => 4))

julia> foldr(=>, 1:4; init=0)
1 => (2 => (3 => (4 => 0)))
```
