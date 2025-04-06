```
setdiff!(s, itrs...)
```

Küme `s`'den (yerinde) `itrs`'den her bir iterable'ın her bir elemanını çıkarın. Dizilerle sıralamayı koruyun.

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

# Örnekler

```jldoctest
julia> a = Set([1, 3, 4, 5]);

julia> setdiff!(a, 1:2:6);

julia> a
Set{Int64} with 1 element:
  4
```
