```
pop!(koleksiyon, anahtar[, varsayılan])
```

Eğer `koleksiyon` içinde mevcutsa `anahtar` için eşlemeyi sil ve döndür, aksi takdirde `varsayılan`ı döndür veya `varsayılan` belirtilmemişse bir hata fırlat.

# Örnekler

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> pop!(d, "a")
1

julia> pop!(d, "d")
HATA: KeyError: anahtar "d" bulunamadı
Stacktrace:
[...]

julia> pop!(d, "e", 4)
4
```
