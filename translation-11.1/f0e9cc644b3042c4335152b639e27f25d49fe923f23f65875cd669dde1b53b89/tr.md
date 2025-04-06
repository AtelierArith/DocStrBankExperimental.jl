```
timedwait(testcb, timeout::Gerçek; pollint::Gerçek=0.1)
```

`testcb()` `true` döndürene kadar veya `timeout` saniye geçene kadar bekleyin, hangisi daha önce olursa. Test fonksiyonu her `pollint` saniyede bir kontrol edilir. `pollint` için minimum değer 0.001 saniyedir, yani 1 milisaniye.

`:ok` veya `:timed_out` döndürün.

# Örnekler

```jldoctest
julia> cb() = (sleep(5); return);

julia> t = @async cb();

julia> timedwait(()->istaskdone(t), 1)
:timed_out

julia> timedwait(()->istaskdone(t), 6.5)
:ok
```
