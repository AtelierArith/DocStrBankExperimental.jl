```
nand(x, y)
⊼(x, y)
```

`x` 和 `y` 的按位 nand（非与）。实现了 [三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)，如果其中一个参数是 `missing`，则返回 [`missing`](@ref)。

中缀操作 `a ⊼ b` 是 `nand(a,b)` 的同义词，`⊼` 可以通过在 Julia REPL 中按 Tab 完成 `\nand` 或 `\barwedge` 来输入。

# 示例

```jldoctest
julia> nand(true, false)
true

julia> nand(true, true)
false

julia> nand(true, missing)
missing

julia> false ⊼ false
true

julia> [true; true; false] .⊼ [true; false; false]
3-element BitVector:
 0
 1
 1
```
