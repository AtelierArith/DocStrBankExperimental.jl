```
foldl(op, itr; [init])
```

类似于 [`reduce`](@ref)，但保证左关联性。如果提供，关键字参数 `init` 将仅使用一次。通常，处理空集合时需要提供 `init`。

另请参见 [`mapfoldl`](@ref)，[`foldr`](@ref)，[`accumulate`](@ref)。

# 示例

```jldoctest
julia> foldl(=>, 1:4)
((1 => 2) => 3) => 4

julia> foldl(=>, 1:4; init=0)
(((0 => 1) => 2) => 3) => 4

julia> accumulate(=>, (1,2,3,4))
(1, 1 => 2, (1 => 2) => 3, ((1 => 2) => 3) => 4)
```
