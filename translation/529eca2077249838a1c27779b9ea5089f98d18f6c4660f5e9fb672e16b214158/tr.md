```
xor(x, y)
⊻(x, y)
```

`x` ve `y`'nin bit düzeyinde özel veya işlemi. Eğer argümanlardan biri `missing` ise [`missing`](@ref) döner. 

İnfix işlem `a ⊻ b`, `xor(a,b)` için bir eşanlamlıdır ve `⊻` Julia REPL'de `\xor` veya `\veebar` yazarak tamamlanabilir.

# Örnekler

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
