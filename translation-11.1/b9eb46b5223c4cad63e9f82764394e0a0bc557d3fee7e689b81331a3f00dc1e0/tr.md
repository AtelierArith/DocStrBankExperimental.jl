```
===(x,y) -> Bool
≡(x,y) -> Bool
```

`x` ve `y`'nin, hiçbir programın ayırt edemeyeceği anlamında özdeş olup olmadığını belirleyin. Öncelikle `x` ve `y`'nin türleri karşılaştırılır. Eğer bunlar özdeşse, değiştirilebilir nesneler bellek adresi ile, değiştirilemez nesneler (örneğin sayılar) ise bit düzeyinde içerik ile karşılaştırılır. Bu işlev bazen "egal" olarak adlandırılır. Her zaman bir `Bool` değeri döndürür.

# Örnekler

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a == b
true

julia> a === b
false

julia> a === a
true
```
