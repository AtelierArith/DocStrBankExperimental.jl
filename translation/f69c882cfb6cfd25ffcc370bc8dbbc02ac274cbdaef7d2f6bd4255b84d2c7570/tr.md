```
isodd(x::Number) -> Bool
```

`x` tek bir tek sayı ise `true` döner (yani, 2'ye tam bölünemeyen bir tam sayı), aksi takdirde `false` döner.

!!! compat "Julia 1.7"
    Non-`Integer` argümanlar Julia 1.7 veya daha yenisini gerektirir.


# Örnekler

```jldoctest
julia> isodd(9)
true

julia> isodd(10)
false
```
