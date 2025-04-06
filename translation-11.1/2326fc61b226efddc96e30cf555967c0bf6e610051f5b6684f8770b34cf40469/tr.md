```
asyncmap!(f, results, c...; ntasks=0, batch_size=nothing)
```

[`asyncmap`](@ref) gibi, ancak çıktıyı bir koleksiyon döndürmek yerine `results` içinde saklar.

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.
