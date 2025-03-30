```
nor(x, y)
⊽(x, y)
```

`x` ve `y`'nin bit düzeyinde nor (değil veya) işlemi. Eğer argümanlardan biri `missing` ise ve diğeri `true` değilse [`missing`](@ref) döner.

İnfix işlemi `a ⊽ b`, `nor(a,b)` için bir eşanlamlıdır ve `⊽` Julia REPL'de `\nor` veya `\barvee` yazarak otomatik tamamlama ile yazılabilir.

# Örnekler

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
