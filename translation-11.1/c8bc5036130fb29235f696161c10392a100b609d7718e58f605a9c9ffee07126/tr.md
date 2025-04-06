```
Meta.isexpr(ex, head[, n])::Bool
```

`ex` bir `Expr` ise ve verilen `head` türüne sahipse ve isteğe bağlı olarak argüman listesinin uzunluğu `n` ise `true` döner. `head` bir `Symbol` veya `Symbol` koleksiyonu olabilir. Örneğin, bir makronun bir fonksiyon çağrısı ifadesi alıp almadığını kontrol etmek için `isexpr(ex, :call)` kullanabilirsiniz.

# Örnekler

```jldoctest
julia> ex = :(f(x))
:(f(x))

julia> Meta.isexpr(ex, :block)
false

julia> Meta.isexpr(ex, :call)
true

julia> Meta.isexpr(ex, [:block, :call]) # birden fazla olası baş
true

julia> Meta.isexpr(ex, :call, 1)
false

julia> Meta.isexpr(ex, :call, 2)
true
```
