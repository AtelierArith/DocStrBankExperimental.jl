```
put!(rr::Future, v)
```

Bir değeri [`Future`](@ref) `rr`'ye kaydedin. `Future`'lar bir kez yazılabilen uzak referanslardır. Zaten ayarlanmış bir `Future` üzerinde `put!` çağrısı bir `Exception` fırlatır. Tüm asenkron uzak çağrılar `Future` döndürür ve tamamlandığında değeri çağrının dönüş değeri olarak ayarlar.
