```
any(p, itr) -> Bool
```

确定谓词 `p` 是否对 `itr` 的任何元素返回 `true`，一旦遇到 `itr` 中第一个 `p` 返回 `true` 的项就返回 `true`（短路）。要在 `false` 上短路，请使用 [`all`](@ref)。

如果输入包含 [`missing`](@ref) 值，当所有非缺失值为 `false`（或等价地，如果输入不包含 `true` 值）时，返回 `missing`，遵循 [三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)。

# 示例

```jldoctest
julia> any(i->(4<=i<=6), [3,5,7])
true

julia> any(i -> (println(i); i > 3), 1:10)
1
2
3
4
true

julia> any(i -> i > 0, [1, missing])
true

julia> any(i -> i > 0, [-1, missing])
missing

julia> any(i -> i > 0, [-1, 0])
false
```
