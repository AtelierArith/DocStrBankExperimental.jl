```
any(itr) -> Bool
```

测试布尔集合中是否有任何元素为 `true`，一旦遇到 `itr` 中的第一个 `true` 值就返回 `true`（短路）。要在 `false` 上短路，请使用 [`all`](@ref)。

如果输入包含 [`missing`](@ref) 值，当所有非缺失值为 `false`（或等价地，如果输入中没有 `true` 值）时，返回 `missing`，遵循 [三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)。

另请参见：[`all`](@ref), [`count`](@ref), [`sum`](@ref), [`|`](@ref), , [`||`](@ref)。

# 示例

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> any(a)
true

julia> any((println(i); v) for (i, v) in enumerate(a))
1
true

julia> any([missing, true])
true

julia> any([false, missing])
missing
```
