```
all(itr) -> Bool
```

测试布尔集合的所有元素是否为 `true`，一旦在 `itr` 中遇到第一个 `false` 值就返回 `false`（短路）。要在 `true` 上短路，请使用 [`any`](@ref)。

如果输入包含 [`missing`](@ref) 值，当所有非缺失值为 `true`（或等价地，如果输入中没有 `false` 值）时，返回 `missing`，遵循 [三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)。

另请参见：[`all!`](@ref), [`any`](@ref), [`count`](@ref), [`&`](@ref), , [`&&`](@ref), [`allunique`](@ref)。

# 示例

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> all(a)
false

julia> all((println(i); v) for (i, v) in enumerate(a))
1
2
false

julia> all([missing, false])
false

julia> all([true, missing])
missing
```
