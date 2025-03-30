```
open(f::Function, command, args...; kwargs...)
```

`open(command, args...; kwargs...)` ile benzer, ancak sonuçlanan işlem akışında `f(stream)` çağrısını yapar, ardından giriş akışını kapatır ve işlemin tamamlanmasını bekler. Başarılı olduğunda `f` tarafından döndürülen değeri döndürür. İşlem başarısız olursa veya işlem stdout'a herhangi bir şey yazmaya çalışırsa bir hata fırlatır.
