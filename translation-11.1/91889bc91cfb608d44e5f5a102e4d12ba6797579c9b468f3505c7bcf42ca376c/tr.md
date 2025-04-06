```
iseven(x::Number) -> Bool
```

`x` bir çift tam sayı (yani, 2'ye tam bölünebilen bir tam sayı) ise `true`, aksi takdirde `false` döndürün.

!!! compat "Julia 1.7"
    Non-`Integer` argümanlar Julia 1.7 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> iseven(9)
false

julia> iseven(10)
true
```
