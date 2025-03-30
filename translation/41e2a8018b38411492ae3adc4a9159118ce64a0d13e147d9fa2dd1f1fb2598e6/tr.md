```
isready(rr::Future)
```

Bir [`Future`](@ref) değerinin depolandığını belirleyin.

Eğer `Future` argümanı farklı bir düğüm tarafından sahipleniliyorsa, bu çağrı cevabı beklemek için engellenecektir. Bunun yerine `rr`'yi ayrı bir görevde beklemek veya yerel bir [`Channel`](@ref) kullanarak bir vekil olarak kullanmak önerilir:

```julia
p = 1
f = Future(p)
errormonitor(@async put!(f, remotecall_fetch(long_computation, p)))
isready(f)  # engellemeyecek
```
