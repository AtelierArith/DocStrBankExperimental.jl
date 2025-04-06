```
promote_shape(s1, s2)
```

İki dizi şeklinin uyumluluğunu kontrol eder, sonlanan tekil boyutlara izin verir ve daha fazla boyuta sahip olan şekli döndürür.

# Örnekler

```jldoctest
julia> a = fill(1, (3,4,1,1,1));

julia> b = fill(1, (3,4));

julia> promote_shape(a,b)
(Base.OneTo(3), Base.OneTo(4), Base.OneTo(1), Base.OneTo(1), Base.OneTo(1))

julia> promote_shape((2,3,1,4), (2, 3, 1, 4, 1))
(2, 3, 1, 4, 1)
```
