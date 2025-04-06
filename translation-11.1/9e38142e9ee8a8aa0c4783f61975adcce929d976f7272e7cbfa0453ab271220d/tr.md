```
nand(x, y)
⊼(x, y)
```

`x` ve `y`'nin bit düzeyinde nand (ve değil) işlemi. [`missing`](@ref) olan bir argüman varsa, [üç değerli mantık](https://en.wikipedia.org/wiki/Three-valued_logic) uygular.

İnfix işlemi `a ⊼ b`, `nand(a,b)` için bir eşanlamlıdır ve `⊼` Julia REPL'de `\nand` veya `\barwedge` yazarak tamamlanabilir.

# Örnekler

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
