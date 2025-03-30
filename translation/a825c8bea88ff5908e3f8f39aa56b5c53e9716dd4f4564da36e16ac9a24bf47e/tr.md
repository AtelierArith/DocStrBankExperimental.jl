```
için
```

`için` döngüleri, bir değerler dizisi üzerinde yineleme yaparken bir dizi ifadeyi tekrar tekrar değerlendirir.

Yineleme değişkeni her zaman yeni bir değişkendir, kapsayıcı kapsamda aynı isimde bir değişken bulunsa bile. Yineleme için mevcut bir yerel değişkeni yeniden kullanmak için [`outer`](@ref) kullanın.

# Örnekler

```jldoctest
julia> için i [1, 4, 0] içinde
           println(i)
       son
1
4
0
```
