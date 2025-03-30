```
all(p, itr) -> Bool
```

确定谓词 `p` 是否对 `itr` 的所有元素返回 `true`，一旦遇到 `itr` 中第一个 `p` 返回 `false` 的项就返回 `false`（短路）。要在 `true` 上短路，请使用 [`any`](@ref)。

如果输入包含 [`missing`](@ref) 值，如果所有非缺失值为 `true`（或者等价地，如果输入不包含 `false` 值），则返回 `missing`，遵循 [三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)。

# 示例

```jldoctest
julia> all(i->(4<=i<=6), [4,5,6])
true

julia> all(i -> (println(i); i < 3), 1:10)
1
2
3
false

julia> all(i -> i > 0, [1, missing])
missing

julia> all(i -> i > 0, [-1, missing])
false

julia> all(i -> i > 0, [1, 2])
true
```
