```
xor(x, y)
⊻(x, y)
```

`x` 和 `y` 的按位异或。实现了 [三值逻辑](https://en.wikipedia.org/wiki/Three-valued_logic)，如果其中一个参数是 `missing`，则返回 [`missing`](@ref)。

中缀操作 `a ⊻ b` 是 `xor(a,b)` 的同义词，`⊻` 可以通过在 Julia REPL 中按 Tab 完成 `\xor` 或 `\veebar` 来输入。

# 示例

```jldoctest
julia> xor(true, false)
true

julia> xor(true, true)
false

julia> xor(true, missing)
missing

julia> false ⊻ false
false

julia> [true; true; false] .⊻ [true; false; false]
3-element BitVector:
 0
 1
 0
```
