```
nor(x, y)
⊽(x, y)
```

`x` 和 `y` 的按位 nor（非或）。实现了 [三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)，如果其中一个参数是 `missing` 而另一个不是 `true`，则返回 [`missing`](@ref)。

中缀操作 `a ⊽ b` 是 `nor(a,b)` 的同义词，`⊽` 可以通过在 Julia REPL 中按 Tab 完成 `\nor` 或 `\barvee` 来输入。

# 示例

```jldoctest
julia> nor(true, false)
false

julia> nor(true, true)
false

julia> nor(true, missing)
false

julia> false ⊽ false
true

julia> false ⊽ missing
missing

julia> [true; true; false] .⊽ [true; false; false]
3-element BitVector:
 0
 0
 1
```
