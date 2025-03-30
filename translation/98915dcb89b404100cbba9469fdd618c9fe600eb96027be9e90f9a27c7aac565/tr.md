```
!=(x, y)
≠(x,y)
```

Eşit olmama karşılaştırma operatörü. Her zaman [`==`](@ref) ile ters cevap verir.

# Uygulama

Yeni türler genellikle bunu uygulamamalı ve bunun yerine `!=(x,y) = !(x==y)` yedek tanımına güvenmelidir.

# Örnekler

```jldoctest
julia> 3 != 2
true

julia> "foo" ≠ "foo"
false
```
