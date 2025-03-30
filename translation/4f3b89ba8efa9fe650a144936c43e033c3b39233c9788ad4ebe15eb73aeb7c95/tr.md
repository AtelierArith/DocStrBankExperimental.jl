```
remote([p::AbstractWorkerPool], f) -> Function
```

Mevcut bir işçi üzerinde (varsa [`WorkerPool`](@ref) `p`'den alınan) `f` fonksiyonunu çalıştıran anonim bir fonksiyon döndürür. [`remotecall_fetch`](@ref) kullanarak.
